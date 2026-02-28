# MongoDB Shell Practice Project  
## Task Manager System – Database Operations
``` Built with love with the help of CipherSchools ```
---

## 1. Introduction

This project demonstrates the use of MongoDB shell to perform database and collection operations.  

Two databases are used:

- **university** – Stores user information  
- **task-manager** – Stores task details  

The project covers complete CRUD operations (Create, Read, Update, Delete) along with indexing and query filtering.

---

# 2. University Database Setup

## 2.1 Create and Use Database

```javascript
// Switch to university database
use university
```
## 2.2 Create Users Collection

```javascript
// Create users collection
db.createCollection("users")
```

2.3 Insert User Document
```javascript
// Insert a user
db.users.insertOne({
  name: "Raj",
  email: "raj@gmail.com",
  createdAt: new Date()
})
```

2.4 View Users
```javascript
// Display all users
db.users.find()
```
3. Task Manager Database Setup
3.1 Switch to Task Manager Database
```javascript
use task-manager
```
3.2 Create Tasks Collection
```javascript
db.createCollection("tasks")
```
4. Insert Task Records
4.1 Insert One Task
```javascript
db.tasks.insertOne({
  task: "Learning MongoDB",
  createdAt: new Date("2026-02-27"),
  deadline: new Date("2026-02-28"),
  user: "Raj",
  isCompleted: false,
  procrastinated: 0
})
```
4.2 Insert Multiple Tasks
```javascript
db.tasks.insertMany([
  {
    task: "Workout",
    createdAt: new Date("2026-02-27"),
    deadline: new Date("2026-02-28"),
    user: "Raj",
    isCompleted: false,
    procrastinated: 1
  },
  {
    task: "Teaching",
    createdAt: new Date("2026-02-25"),
    deadline: new Date("2026-02-26"),
    user: "SKT",
    isCompleted: true,
    procrastinated: 2
  }
])
```
5. Read Operations
5.1 Retrieve All Tasks
```javascript
db.tasks.find()
```
5.2 Retrieve Tasks by User
```javascript
db.tasks.find({ user: "SKT" })
```
5.3 Retrieve Tasks with Condition
```javascript
// Find tasks where procrastinated value is greater than 3
db.tasks.find({ procrastinated: { $gt: 3 } })
```
6. Update Operations
6.1 Update One Document
```javascript
db.tasks.updateOne(
  { user: "SKT" },
  {
    $set: { deadline: new Date("2026-02-29") }
  }
)
```
6.2 Update Multiple Documents
```javascript
db.tasks.updateMany(
  { user: "Raj" },
  {
    $set: { deadline: new Date("2026-02-29") }
  }
)
```
6.3 Update Using OR Condition
```javascript
db.tasks.updateMany(
  {
    $or: [
      { task: "Workout", user: "Raj" },
      { task: "Teaching", user: "SKT" }
    ]
  },
  {
    $set: { isCompleted: true }
  }
)
```
7. Delete Operations
7.1 Delete One Document
```javascript
db.tasks.deleteOne({ task: "Learning MongoDB" })
```
7.2 Delete Multiple Documents
```javascript
db.tasks.deleteMany({ isCompleted: true })
```
8. Utility Commands
8.1 Show Databases
```javascript
show dbs
```
8.2 Show Collections
```javascript
show collections
```
8.3 Pretty Output
```javascript
db.tasks.find().pretty()
```
9. Index Creation (Performance Optimization)
```javascript
// Create index on user field
db.tasks.createIndex({ user: 1 })
```
