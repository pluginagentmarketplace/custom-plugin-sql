---
name: projects
description: Hands-On Projects
allowed-tools: Read
---

# Hands-On Projects

Build real-world experience with these database and SQL projects. Choose by difficulty and your learning path.

## 🟢 Beginner Projects (1-3 hours each)

### 1. Movie Database Query Practice
**Skills:** SQL Fundamentals
**Topics:** SELECT, WHERE, ORDER BY, basic joins

Create a movie database and practice queries:
- Find movies by genre
- List top-rated movies
- Count movies by director
- Find movies released in a year

**Starter SQL:**
```sql
CREATE TABLE movies (
  id INT PRIMARY KEY,
  title VARCHAR(200),
  release_year INT,
  rating DECIMAL(3,1),
  director VARCHAR(100),
  genre VARCHAR(50)
);
```

---

### 2. Employee Salary Analysis
**Skills:** SQL Fundamentals + Data Analysis
**Topics:** GROUP BY, aggregates, HAVING

Analyze employee data:
- Average salary by department
- Department with most employees
- Highest paid employees
- Salary ranges analysis

---

### 3. E-Commerce Basic Queries
**Skills:** SQL Fundamentals, JOINs
**Topics:** Multiple tables, WHERE, ORDER BY

Work with orders and customers:
- Find customer orders
- Order totals by customer
- Top 10 customers by spending
- Orders in a date range

---

### 4. Blog Analytics Dashboard Prep
**Skills:** Data Analysis SQL
**Topics:** Aggregations, GROUP BY

Create analytics for a blog:
- Posts per author
- Average views per post
- Comments per post
- Top performing posts

---

### 5. Simple Cache Implementation
**Skills:** Redis Basics
**Topics:** SET, GET, expiration

Build a basic caching system:
- Cache user profiles (1 hour expiry)
- Cache session data
- Count page views
- Simple rate limiting (10 requests/minute)

---

## 🟡 Intermediate Projects (4-8 hours each)

### 6. Customer Data Warehouse
**Skills:** Data Warehouse Design, Star Schema
**Topics:** Fact tables, dimensions, normalization

Design a data warehouse:
- Create fact_orders table
- Design dim_customer, dim_product, dim_date
- Write dimensional queries
- Implement slowly changing dimensions

---

### 7. Real-Time Analytics with Redis
**Skills:** Redis Patterns, Data Structures
**Topics:** Pub/Sub, sorted sets, counters

Build real-time analytics:
- User activity tracking
- Live leaderboard
- Session management
- Real-time counters

---

### 8. MongoDB Document Modeling
**Skills:** MongoDB & NoSQL Design
**Topics:** Embedding, referencing, aggregation

Model different scenarios:
- Blog with posts and comments
- E-commerce with products and reviews
- Social network with users and followers
- Project management system

---

### 9. ETL Pipeline (CSV to Database)
**Skills:** Data Engineer, ETL Basics
**Topics:** Extract, transform, load, validation

Build a simple ETL:
- Extract from CSV file
- Transform and clean data
- Validate data quality
- Load into database
- Log execution

---

### 10. Query Performance Optimization
**Skills:** Advanced SQL, Database Admin
**Topics:** Indexes, execution plans, optimization

Optimize slow queries:
- Analyze query performance
- Create appropriate indexes
- Refactor inefficient queries
- Measure improvements

---

### 11. PostgreSQL Replication Setup
**Skills:** PostgreSQL DBA
**Topics:** Backup, recovery, replication

Set up PostgreSQL high availability:
- Configure primary server
- Set up standby replica
- Test failover
- Implement automated backups

---

### 12. Data Analysis Report
**Skills:** Data Analysis SQL, Presentation
**Topics:** Statistical analysis, insights

Create analytical reports:
- Customer segmentation analysis
- Cohort analysis
- Churn rate calculation
- Trend analysis with visualizations

---

## 🔴 Advanced Projects (8+ hours each)

### 13. Multi-Node MongoDB Cluster
**Skills:** MongoDB Scaling, Replication
**Topics:** Sharding, replica sets, HA

Build a production MongoDB setup:
- Configure replica set (3 nodes)
- Implement sharding
- Set up connection pooling
- Test failover scenarios

---

### 14. Data Lake Architecture
**Skills:** Data Engineer, Big Data
**Topics:** Data organization, schemas, governance

Design a data lake:
- Organize raw, curated, trusted zones
- Implement data catalog
- Add data quality monitoring
- Create self-service analytics layer

---

### 15. BI Dashboard Development
**Skills:** BI Analyst, Dashboard Design
**Topics:** Metrics, dimensions, visualization

Build a complete BI solution:
- Design star schema
- Define KPIs and metrics
- Create dashboard mockups
- Write optimized queries
- (Optional: Integrate with BI tool)

---

### 16. Production ETL System
**Skills:** Data Engineer, Advanced patterns
**Topics:** Complex pipelines, error handling, scheduling

Build enterprise ETL:
- Multiple data sources
- Complex transformations
- Error handling and retry logic
- Data quality framework
- Scheduling and monitoring
- Incremental loads
- Audit logging

---

### 17. Real-Time Data Pipeline
**Skills:** Redis, Streaming, Data Engineer
**Topics:** Event streaming, real-time processing

Build a real-time system:
- Stream user events (clicks, views, etc.)
- Process with Redis Streams
- Update real-time metrics
- Feed to analytics dashboard

---

### 18. Complete Analytics Platform
**Skills:** All agents
**Topics:** Full stack data solution

Integrate everything:
- Data warehouse (PostgreSQL)
- Caching layer (Redis)
- NoSQL data store (MongoDB)
- ETL pipelines
- BI dashboards
- Real-time analytics

---

## 📊 Project Difficulty Matrix

| Project | SQL | Databases | NoSQL | Analysis | Engineering | BI |
|---------|-----|-----------|-------|----------|-------------|-----|
| 1. Movies | ★★★ | - | - | - | - | - |
| 2. Salaries | ★★★ | ★★ | - | ★★★ | - | - |
| 3. E-Commerce | ★★★ | ★★ | - | - | - | - |
| 4. Blog Analytics | ★★★ | ★★ | - | ★★★ | - | ★★ |
| 5. Cache | - | ★★ | ★★★ | - | - | - |
| 6. Warehouse | ★★★ | ★★ | - | ★★ | ★★★ | ★★★ |
| 7. Real-Time | - | ★★ | ★★★ | ★★ | ★★★ | - |
| 8. MongoDB | ★★ | - | ★★★ | - | ★★ | - |
| 9. ETL Pipeline | ★★★ | ★★★ | - | ★★ | ★★★ | - |
| 10. Query Optimization | ★★★ | ★★★ | - | - | ★★ | - |
| 11. PostgreSQL HA | - | ★★★ | - | - | ★★ | - |
| 12. Analysis Report | ★★★ | ★★ | - | ★★★ | - | ★★ |
| 13. MongoDB Cluster | - | ★ | ★★★ | - | ★★★ | - |
| 14. Data Lake | ★★★ | ★★ | ★★ | - | ★★★ | - |
| 15. BI Dashboard | ★★★ | ★★ | - | ★★ | - | ★★★ |
| 16. Enterprise ETL | ★★★ | ★★★ | ★★ | ★★ | ★★★ | - |
| 17. Real-Time Streaming | - | ★★ | ★★★ | ★★ | ★★★ | ★★ |
| 18. Full Platform | ★★★ | ★★★ | ★★★ | ★★★ | ★★★ | ★★★ |

---

## 🎯 Learning Paths by Role

### Backend Developer
1. Project 1: Movie Database
2. Project 3: E-Commerce
3. Project 9: ETL Pipeline
4. Project 11: PostgreSQL HA
5. Project 18: Full Platform

### Data Analyst
1. Project 2: Salary Analysis
2. Project 4: Blog Analytics
3. Project 12: Analysis Report
4. Project 6: Data Warehouse
5. Project 15: BI Dashboard

### Data Engineer
1. Project 9: ETL Pipeline
2. Project 6: Data Warehouse
3. Project 14: Data Lake
4. Project 16: Enterprise ETL
5. Project 18: Full Platform

### DBA
1. Project 11: PostgreSQL HA
2. Project 13: MongoDB Cluster
3. Project 6: Data Warehouse
4. Project 10: Query Optimization

---

## 🚀 Getting Started

1. Choose a project matching your level
2. Review required skills
3. Follow starter code/prompts
4. Complete all requirements
5. Document your solution
6. Compare with reference implementations

---

## 📝 Project Submission Tips

1. **Document everything**: Why you made decisions
2. **Show your work**: Include queries, configs, code
3. **Test thoroughly**: Verify results and edge cases
4. **Performance matters**: Measure and optimize
5. **Share learnings**: What would you do differently?

---

**Ready to build?** Choose your first project above and let's get started!
