## Current Data

**Command**
```json
db.userData.find()
```
**Output**
```json
[
  {
    "_id": ObjectId('674b5c53ad15ea8c480d8190'),
    "name": "Andrew",
    "age": 30,
    "city": "New York"
  },
  {
    "_id": ObjectId('674b5c53ad15ea8c480d8191'),
    "name": "Anna",
    "city": "Washington"
  },
  {
    "_id": ObjectId('674b5c53ad15ea8c480d8192'),
    "name": "Julia",
    "age": null
  }
]
```

## Selecting records having age field

**Command**
```json
db.userData.find({"age": {$exists: true}})
```
**Output**
```json
[
  {
    "_id": ObjectId('674b5c53ad15ea8c480d8190'),
    "name": "Andrew",
    "age": 30,
    "city": "New York"
  },
  {
    "_id": ObjectId('674b5c53ad15ea8c480d8192'),
    "name": "Julia",
    "age": null
  }
]
  ```
  
## Selecting having age field with a valid value

**Command**
```json
db.userData.find({$and: [{"age": {$exists: true}}, {"age": {$ne: null}}] })
```
**Output**
```json
[
  {
    "_id": ObjectId('674b5c53ad15ea8c480d8190'),
    "name": "Andrew",
    "age": 30,
    "city": "New York"
  }
]
  ```