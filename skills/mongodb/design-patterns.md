---
name: nosql-design
description: NoSQL design patterns including denormalization, embedding strategies, referencing patterns, and schema design best practices for MongoDB applications.
---

# NoSQL Design Patterns

## Embedding vs Referencing

### Embedding Pattern (Denormalization)

```javascript
// One-to-one: Embed related data
db.employees.findOne()
{
  _id: ObjectId("..."),
  firstName: "John",
  lastName: "Doe",
  address: {
    street: "123 Main St",
    city: "New York",
    state: "NY",
    zip: "10001"
  },
  contact: {
    email: "john@example.com",
    phone: "555-1234"
  }
}

// One-to-few: Embed small arrays
db.employees.findOne()
{
  _id: ObjectId("..."),
  firstName: "John",
  skills: ["JavaScript", "Python", "SQL"],
  certifications: [
    { name: "AWS Solutions Architect", year: 2023 },
    { name: "Google Cloud Professional", year: 2022 }
  ]
}
```

### Referencing Pattern (Normalization)

```javascript
// One-to-many: Reference related documents
// employees collection
{
  _id: ObjectId("emp1"),
  firstName: "John",
  lastName: "Doe",
  department_id: ObjectId("dept1")
}

// departments collection
{
  _id: ObjectId("dept1"),
  name: "Engineering",
  budget: 500000
}

// Query with $lookup (join)
db.employees.aggregate([
  {
    $lookup: {
      from: "departments",
      localField: "department_id",
      foreignField: "_id",
      as: "department"
    }
  },
  { $unwind: "$department" }
])
```

## Common Schema Patterns

### Polymorphic Pattern

```javascript
// Handle different document types in same collection
db.items.find()
[
  {
    type: "book",
    title: "MongoDB Guide",
    author: "John Doe",
    isbn: "123-456"
  },
  {
    type: "course",
    title: "MongoDB Mastery",
    instructor: "Jane Smith",
    duration: 40,
    language: "English"
  },
  {
    type: "video",
    title: "MongoDB Basics",
    channel: "Tech Channel",
    duration_minutes: 45,
    url: "https://..."
  }
]

// Query by type
db.items.find({ type: "book" })
```

### Attribute Pattern

```javascript
// Flexible attribute storage for varying data
{
  _id: ObjectId("prod1"),
  name: "Laptop",
  category: "Electronics",
  attributes: [
    { key: "RAM", value: "16GB" },
    { key: "Storage", value: "512GB SSD" },
    { key: "Processor", value: "Intel i7" },
    { key: "Screen", value: "15.6 inch" }
  ]
}

// Query attributes
db.products.find({ "attributes.key": "RAM", "attributes.value": "16GB" })
```

### Extended Reference Pattern

```javascript
// Store frequently accessed data to avoid lookups
// Users collection with department info cached
{
  _id: ObjectId("user1"),
  firstName: "John",
  department_id: ObjectId("dept1"),
  department_name: "Engineering",     // Cached for performance
  department_budget: 500000            // Denormalized
}

// Use lookup when you need all data
// Update cached data with background sync
```

### Subset Pattern

```javascript
// Split large documents into smaller subsets
// Main document with summary
db.products.findOne()
{
  _id: ObjectId("prod1"),
  name: "Popular Book",
  author: "John Smith",
  reviews_count: 1500,
  rating: 4.5,
  review_ids: [
    ObjectId("rev1"),
    ObjectId("rev2"),
    // ... only recent reviews
  ]
}

// Reviews in separate collection
db.product_reviews.findOne()
{
  _id: ObjectId("rev1"),
  product_id: ObjectId("prod1"),
  user: "Jane",
  rating: 5,
  comment: "Excellent book!"
}
```

## Aggregation Framework Patterns

```javascript
// Complex multi-stage aggregation
db.employees.aggregate([
  // Stage 1: Match
  {
    $match: { department: "Engineering", active: true }
  },
  // Stage 2: Group
  {
    $group: {
      _id: "$department",
      count: { $sum: 1 },
      avg_salary: { $avg: "$salary" },
      min_salary: { $min: "$salary" },
      max_salary: { $max: "$salary" },
      total_salary: { $sum: "$salary" }
    }
  },
  // Stage 3: Sort
  {
    $sort: { avg_salary: -1 }
  },
  // Stage 4: Project
  {
    $project: {
      department: "$_id",
      employee_count: "$count",
      average_salary: "$avg_salary",
      salary_range: {
        min: "$min_salary",
        max: "$max_salary"
      },
      _id: 0
    }
  }
])

// Lookup (join) in aggregation
db.orders.aggregate([
  {
    $lookup: {
      from: "customers",
      localField: "customer_id",
      foreignField: "_id",
      as: "customer_info"
    }
  },
  { $unwind: "$customer_info" },
  {
    $group: {
      _id: "$customer_info.city",
      total_orders: { $sum: 1 },
      total_amount: { $sum: "$amount" }
    }
  }
])
```

## Scaling Patterns

### Sharding Strategy

```javascript
// Shard by ranges (bad - uneven distribution)
// sh.shardCollection("mydb.logs", { date: 1 })

// Shard by hash (good - even distribution)
sh.shardCollection("mydb.events", { user_id: "hashed" })

// Compound shard key
sh.shardCollection("mydb.orders", { customer_id: 1, order_date: -1 })
```

### Bulk Insert Pattern

```javascript
// Batch inserts for performance
const batch = []
for (let i = 0; i < 10000; i++) {
  batch.push({
    name: `Item ${i}`,
    value: Math.random() * 1000
  })

  if (batch.length === 1000) {
    db.items.insertMany(batch)
    batch = []
  }
}
if (batch.length > 0) {
  db.items.insertMany(batch)
}
```

## Best Practices

✅ Embed when data is accessed together
✅ Reference when data is large or accessed separately
✅ Denormalize for read performance
✅ Keep related data close
✅ Use indexes on query fields
✅ Limit array sizes (16MB document limit)
✅ Use bulk operations for large inserts
✅ Monitor document growth
✅ Plan for evolving schemas
