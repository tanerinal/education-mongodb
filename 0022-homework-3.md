## Task-1: Import the Data within the file bowoffice.json into a New Database and Collection

**Command**
```json
mongoimport D:\......\03-boxoffice.json -d boxOffice -c movieStarts --jsonArray
```
**Output**
```java
2024-12-01T18:51:54.063+0300    connected to: mongodb://localhost/
2024-12-01T18:51:54.108+0300    3 document(s) imported successfully. 0 document(s) failed to import.
```

### Current Data
**Command**

```json
use boxOffice
db.movieStarts.find()
```
**Output**
```json
[
  {
    "_id": ObjectId('674c861a94a0baf752b8d446'),
    "title": "Teach me if you can",
    "meta": {
      "rating": 8.5,
      "aired": 2014,
      "runtime": 90
    },
    "visitors": 590378,
    "expectedVisitors": 500000,
    "genre": ["action", "thriller"]
  },
  {
    "_id": ObjectId('674c861a94a0baf752b8d447'),
    "title": "Supercharged Teaching",
    "meta": {
      "rating": 9.3,
      "aired": 2016,
      "runtime": 60
    },
    "visitors": 370000,
    "expectedVisitors": 1000000,
    "genre": ["thriller", "action"]
  },
  {
    "_id": ObjectId('674c861a94a0baf752b8d448'),
    "title": "The Last Student Returns",
    "meta": {
      "rating": 9.5,
      "aired": 2018,
      "runtime": 100
    },
    "visitors": 1300000,
    "expectedVisitors": 1550000,
    "genre": ["thriller", "drama", "action"]
  }
]
```
## Task-2: Search All Movies That Have a Rating Higher Than 9.2 and a Runtime Lower than 100 Miutes

**Command**
```json
db.movieStarts.find({$and: [{"meta.rating": {$gt: 9.2}}, {"meta.runtime": {$lt: 100}}]})
```
**Output**
```json
[
  {
    "_id": ObjectId("674c861a94a0baf752b8d447"),
    "title": "Supercharged Teaching",
    "meta": {
      "rating": 9.3,
      "aired": 2016,
      "runtime": 60
    },
    "visitors": 370000,
    "expectedVisitors": 1000000,
    "genre": ["thriller", "action"]
  }
]
```
## Task-3: Search All Movies That Have a Genre of "drama" or "action"

**Command**
```json
db.movieStarts.find({$or: [{"genre": "drama"}, {"genre": "action"}]})
```
**Output**
```json
[
  {
    "_id": ObjectId('674c861a94a0baf752b8d446'),
    "title": "Teach me if you can",
    "meta": {
      "rating": 8.5,
      "aired": 2014,
      "runtime": 90
    },
    "visitors": 590378,
    "expectedVisitors": 500000,
    "genre": ["action", "thriller"]
  },
  {
    "_id": ObjectId('674c861a94a0baf752b8d447'),
    "title": "Supercharged Teaching",
    "meta": {
      "rating": 9.3,
      "aired": 2016,
      "runtime": 60
    },
    "visitors": 370000,
    "expectedVisitors": 1000000,
    "genre": ["thriller", "action"]
  },
  {
    "_id": ObjectId('674c861a94a0baf752b8d448'),
    "title": "The Last Student Returns",
    "meta": {
      "rating": 9.5,
      "aired": 2018,
      "runtime": 100
    },
    "visitors": 1300000,
    "expectedVisitors": 1550000,
    "genre": ["thriller", "drama", "action"]
  }
]
```
## Task-4: Search All Movies where Visitors Exceeds Expected Visitors

**Command**
```json
db.movieStarts.find({$expr: {$gt: ["$visitors", "$expectedVisitors"]}})
```
**Output**
```json
[
  {
    "_id": ObjectId('674c861a94a0baf752b8d446'),
    "title": "Teach me if you can",
    "meta": {
      "rating": 8.5,
      "aired": 2014,
      "runtime": 90
    },
    "visitors": 590378,
    "expectedVisitors": 500000,
    "genre": ["action", "thriller"]
  }
]
```