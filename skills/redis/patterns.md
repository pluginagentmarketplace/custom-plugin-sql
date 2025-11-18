---
name: redis-patterns
description: Redis patterns and use cases including caching strategies, session management, rate limiting, leaderboards, real-time analytics, and high-performance applications.
---

# Redis Patterns & Use Cases

## Caching Patterns

### Cache-Aside (Lazy Loading)

```javascript
// Pseudocode for cache-aside pattern

function getValue(key) {
  // Check cache first
  const cached = redis.get(key)
  if (cached !== null) {
    return cached
  }

  // Cache miss - fetch from database
  const value = database.query(key)

  // Store in cache with expiration
  redis.setex(key, 3600, value)  // Cache for 1 hour

  return value
}
```

### Write-Through Cache

```javascript
// Write to cache and database together

function setValue(key, value) {
  // Write to both cache and database
  redis.set(key, value)
  database.insert(key, value)

  return value
}

// Always read from cache
function getValue(key) {
  return redis.get(key)
}
```

### Cache Invalidation

```
// Invalidate on update
SET user:1 '{"name":"John","email":"john@example.com"}'

// Update user
UPDATE users SET name="Jane" WHERE id=1

// Invalidate cache
DEL user:1

// Pattern invalidation
KEYS user:*
// Then DEL each key

// Tag-based invalidation
SADD tags:user:1 "user:1"
SADD tags:user:1 "posts:1"

// Later, invalidate by tag
SMEMBERS tags:user:1
// DEL all returned keys
```

## Session Management

```javascript
// Store session data
function createSession(sessionId, userData) {
  const sessionKey = `session:${sessionId}`
  redis.hset(sessionKey, 'user_id', userData.id)
  redis.hset(sessionKey, 'username', userData.username)
  redis.hset(sessionKey, 'created_at', Date.now())
  redis.expire(sessionKey, 86400)  // 24 hours
  return sessionId
}

// Get session data
function getSession(sessionId) {
  return redis.hgetall(`session:${sessionId}`)
}

// Update session expiration (on each request)
function refreshSession(sessionId) {
  redis.expire(`session:${sessionId}`, 86400)
}

// Logout (delete session)
function logout(sessionId) {
  redis.del(`session:${sessionId}`)
}
```

## Rate Limiting

### Token Bucket Algorithm

```javascript
function isRateLimited(userId, limit, window) {
  const key = `ratelimit:${userId}`
  const current = redis.get(key)

  if (current === null) {
    redis.setex(key, window, 1)
    return false
  }

  const count = parseInt(current) + 1
  if (count > limit) {
    return true  // Rate limited
  }

  redis.incr(key)
  return false
}

// Usage: Check before allowing API request
if (isRateLimited(userId, 100, 60)) {
  return "Too many requests"
}
```

### Sliding Window Counter

```
// Increment counter for user in current minute
INCR ratelimit:user:1:2024-01-15-10-30
EXPIRE ratelimit:user:1:2024-01-15-10-30 60

// Check limit
GET ratelimit:user:1:2024-01-15-10-30
// If > 1000, rate limited
```

## Leaderboards & Rankings

```javascript
// Add or update score
ZADD leaderboard:game1 100 player1
ZADD leaderboard:game1 150 player2
ZADD leaderboard:game1 120 player3

// Get top 10 players
ZREVRANGE leaderboard:game1 0 9 WITHSCORES

// Get player rank
ZREVRANK leaderboard:game1 player2  // Returns 0 (first place)

// Get player score
ZSCORE leaderboard:game1 player1

// Increase player score
ZINCRBY leaderboard:game1 50 player1

// Get rank with score
function getPlayerStats(leaderboard, player) {
  const rank = redis.zrevrank(leaderboard, player)
  const score = redis.zscore(leaderboard, player)
  return { rank: rank + 1, score }  // Rank is 1-based
}

// Get players around current player
ZREVRANK leaderboard:game1 player2  // Get rank (5)
ZREVRANGE leaderboard:game1 3 7 WITHSCORES  // Get surrounding
```

## Real-Time Analytics

### Counters

```javascript
// Track page views
INCR page:views:home
INCR page:views:about

// Track user actions
INCR user:1:logins
INCR user:1:posts

// Get daily stats (auto-expires)
INCRBY stats:2024-01-15:logins 1
EXPIRE stats:2024-01-15:logins 86400  // 1 day

// Increment with multiple metrics
HINCRBY user:1:stats logins 1
HINCRBY user:1:stats posts 1
HINCRBY user:1:stats comments 1
```

### Time Series Data

```javascript
// Store time series with list
LPUSH temperature:sensor1 '{"time":"2024-01-15T10:30:00","value":72.5}'
LPUSH temperature:sensor1 '{"time":"2024-01-15T10:31:00","value":72.3}'

// Get recent readings
LRANGE temperature:sensor1 0 59  // Last 60 readings

// Auto-expire old data
EXPIRE temperature:sensor1 3600  // Keep 1 hour of data

// Using sorted set for range queries
ZADD temperature:sensor1 1705315800 "72.5"
ZADD temperature:sensor1 1705315860 "72.3"

// Get data in time range
ZRANGEBYSCORE temperature:sensor1 1705315000 1705315900
```

## Locks & Mutexes

```javascript
// Simple lock (not recommended for production)
function acquireLock(resource, timeout) {
  const lockKey = `lock:${resource}`
  const acquired = redis.setnx(lockKey, Date.now())
  if (acquired) {
    redis.expire(lockKey, timeout)
    return true
  }
  return false
}

// Release lock
function releaseLock(resource) {
  redis.del(`lock:${resource}`)
}

// Redlock pattern (safer distributed lock)
// Use RedLock library for multi-instance safety
const RedLock = require('redlock')
const redlock = new RedLock([redis1, redis2, redis3], {
  driftFactor: 0.01,
  retryCount: 3,
  retryDelay: 200,
  retryJitter: 200
})

const lock = await redlock.lock('resource:id', 1000)
try {
  // Critical section
} finally {
  await lock.unlock().catch(err => {})
}
```

## Pub/Sub Messaging

```javascript
// Subscriber
function subscribe() {
  const subscriber = redis.createClient()
  subscriber.subscribe('notifications', 'alerts', (err, count) => {
    console.log(`Subscribed to ${count} channels`)
  })
  subscriber.on('message', (channel, message) => {
    console.log(`${channel}: ${message}`)
  })
}

// Publisher
function publish() {
  const publisher = redis.createClient()
  publisher.publish('notifications', 'User login detected')
  publisher.publish('alerts', 'High memory usage')
}

// Pattern subscription
subscriber.psubscribe('user:*:notifications', (err, count) => {
  console.log(`Pattern subscribed`)
})
```

## Bloom Filters (Approximate Set Membership)

```
// Check if value exists (with false positives)
// Redis 4.0+ has RedisBloom module

BF.ADD mybloom item1
BF.EXISTS mybloom item1        // Returns 1 (exists)
BF.EXISTS mybloom notexists    // Returns 0 (doesn't exist)

// Multi-add
BF.MADD mybloom item2 item3 item4
BF.MEXISTS mybloom item1 item5 item2
```

## Best Practices

✅ Use appropriate data structures for use case
✅ Set expiration for temporary data
✅ Monitor memory usage with MEMORY STATS
✅ Use pipelining for multiple commands
✅ Implement circuit breaker for cache failures
✅ Handle cache misses gracefully
✅ Use connection pooling
✅ Plan for cache invalidation strategy
✅ Monitor key performance indicators
✅ Use Redis Cluster for scaling
