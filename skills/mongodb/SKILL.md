---
name: mongodb
description: MongoDB fundamentals including document model, CRUD operations, querying, indexing, and aggregation framework for NoSQL database applications.
---

# MongoDB Mastery

## Document Model Basics

```javascript
// MongoDB document (JSON-like structure)
{
  _id: ObjectId("507f1f77bcf86cd799439011"),
  firstName: "John",
  lastName: "Doe",
  email: "john@example.com",
  salary: 75000,
  department: "Engineering",
  skills: ["JavaScript", "Python", "SQL"],
  address: {
    street: "123 Main St",
    city: "New York",
    state: "NY"
  },
  joinDate: new Date("2023-01-15")
}
```

## Collection Operations

```javascript
// Create database and collection
use company_db

// Insert single document
db.employees.insertOne({
  firstName: "Jane",
  lastName: "Smith",
  email: "jane@example.com",
  salary: 80000
})

// Insert multiple documents
db.employees.insertMany([
  { firstName: "Bob", lastName: "Johnson", salary: 70000 },
  { firstName: "Alice", lastName: "Williams", salary: 85000 }
])

// Get document count
db.employees.countDocuments({})

// Validate collection
db.employees.validate()
```

## CRUD Operations

```javascript
// READ - Basic find
db.employees.find()

// Find by condition
db.employees.find({ salary: { $gt: 75000 } })

// Find with projection (select specific fields)
db.employees.find(
  { department: "Engineering" },
  { firstName: 1, lastName: 1, salary: 1, _id: 0 }
)

// Find one document
db.employees.findOne({ email: "john@example.com" })

// UPDATE - Update one document
db.employees.updateOne(
  { _id: ObjectId("...") },
  { $set: { salary: 90000 } }
)

// Update multiple documents
db.employees.updateMany(
  { department: "Engineering" },
  { $set: { bonus: 5000 } }
)

// DELETE - Delete documents
db.employees.deleteOne({ _id: ObjectId("...") })
db.employees.deleteMany({ department: "HR" })
```

## Query Operators

```javascript
// Comparison operators
db.employees.find({ salary: { $gt: 75000 } })      // Greater than
db.employees.find({ salary: { $gte: 75000 } })     // Greater than or equal
db.employees.find({ salary: { $lt: 75000 } })      // Less than
db.employees.find({ salary: { $lte: 75000 } })     // Less than or equal
db.employees.find({ salary: { $eq: 75000 } })      // Equal
db.employees.find({ salary: { $ne: 75000 } })      // Not equal

// Array operators
db.employees.find({ skills: "JavaScript" })        // Contains value
db.employees.find({ skills: { $in: ["Python", "Go"] } })    // Contains any
db.employees.find({ skills: { $all: ["JavaScript", "Python"] } })  // Contains all
db.employees.find({ skills: { $size: 3 } })        // Array size

// Element operators
db.employees.find({ phone: { $exists: true } })    // Field exists
db.employees.find({ salary: { $type: "number" } }) // Field type check

// String matching
db.employees.find({ email: { $regex: "gmail" } })  // Regular expression
```

## Sorting and Limiting

```javascript
// Sort by single field
db.employees.find().sort({ salary: -1 })           // Descending
db.employees.find().sort({ salary: 1 })            // Ascending

// Sort by multiple fields
db.employees.find().sort({ department: 1, salary: -1 })

// Limit and skip
db.employees.find().limit(10)                       // First 10 results
db.employees.find().skip(20).limit(10)              // Pagination
```

## Indexing

```javascript
// Create single field index
db.employees.createIndex({ email: 1 })

// Create unique index
db.employees.createIndex({ email: 1 }, { unique: true })

// Create compound index
db.employees.createIndex({ department: 1, salary: -1 })

// Create text index for search
db.employees.createIndex({ firstName: "text", lastName: "text" })

// List indexes
db.employees.getIndexes()

// Drop index
db.employees.dropIndex("email_1")

// Full text search with text index
db.employees.find({ $text: { $search: "john" } })
```

## Data Types

```javascript
// String
{ name: "John Doe" }

// Number (Int32, Int64, Double)
{ age: 30, salary: 75000.50 }

// Boolean
{ active: true }

// Date
{ createdDate: new Date() }

// Array
{ skills: ["JavaScript", "Python"] }

// Object/Embedded document
{ address: { city: "NYC", state: "NY" } }

// ObjectID
{ _id: ObjectId() }

// Null
{ phone: null }

// Regular Expression
{ email: /gmail/ }
```

## Bulk Operations

```javascript
// Initialize bulk operation
let bulk = db.employees.initializeUnorderedBulkOp()

// Add multiple operations
bulk.find({ department: "Engineering" }).update({ $set: { bonus: 5000 } })
bulk.find({ salary: { $lt: 50000 } }).update({ $inc: { salary: 2000 } })
bulk.insert({ firstName: "New", lastName: "Employee" })
bulk.find({ _id: ObjectId("...") }).removeOne()

// Execute bulk
bulk.execute()
```

## Next Steps

Learn NoSQL design patterns, denormalization strategies, and advanced schema design in the `nosql-design` skill.
