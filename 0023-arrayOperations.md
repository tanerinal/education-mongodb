## Current Data

**Command**
```json
db.userData.find()
```
**Output**
```json
[
  {
    "_id": ObjectId("674dd41ff4e6bcc56c0d8190"),
    "name": "Manuel",
    "phone": "123456",
    "age": 30,
    "hobbies": [
      { "title": "Cooking", "frequency": 5 },
      { "title": "Cars", "frequency": 2 }
    ]
  },
  {
    "_id": ObjectId("674dd41ff4e6bcc56c0d8191"),
    "name": "Anna",
    "phone": "343545456",
    "age": null,
    "hobbies": [
      { "title": "Sports", "frequency": 2 },
      { "title": "Yoga", "frequency": 3 }
    ]
  },
  {
    "_id": ObjectId("674dd41ff4e6bcc56c0d8192"),
    "name": "Max",
    "phone": "12345322",
    "hobbies": [
      { "title": "Sports", "frequency": 3 },
      { "title": "Cooking", "frequency": 6 }
    ]
  }
]
```

## Search from an Array with Embedded Documents
**Command**

```json
db.userData.find({"hobbies.title": "Sports"})
```
**Output**
```json
[
  {
    "_id": ObjectId("674dd41ff4e6bcc56c0d8191"),
    "name": "Anna",
    "phone": "343545456",
    "age": null,
    "hobbies": [
      { "title": "Sports", "frequency": 2 },
      { "title": "Yoga", "frequency": 3 }
    ]
  },
  {
    "_id": ObjectId("674dd41ff4e6bcc56c0d8192"),
    "name": "Max",
    "phone": "12345322",
    "hobbies": [
      { "title": "Sports", "frequency": 3 },
      { "title": "Cooking", "frequency": 6 }
    ]
  }
]
```
## Current Data
**Command**

```json
db.userData.find()
```
**Output**
```json
[
  {
    "_id": ObjectId("674dd41ff4e6bcc56c0d8190"),
    "name": "Manuel",
    "phone": "123456",
    "age": 30,
    "hobbies": [
      { "title": "Cooking", "frequency": 5 },
      { "title": "Cars", "frequency": 2 }
    ]
  },
  {
    "_id": ObjectId("674dd41ff4e6bcc56c0d8191"),
    "name": "Anna",
    "phone": "343545456",
    "age": null,
    "hobbies": [
      { "title": "Sports", "frequency": 2 },
      { "title": "Yoga", "frequency": 3 }
    ]
  },
  {
    "_id": ObjectId("674dd41ff4e6bcc56c0d8192"),
    "name": "Max",
    "phone": "12345322",
    "hobbies": [
      { "title": "Sports", "frequency": 3 },
      { "title": "Cooking", "frequency": 6 }
    ]
  },
  {
    "_id": ObjectId("674dd638f4e6bcc56c0d8193"),
    "name": "Chris",
    "hobbies": ["Sports", "Cooking", "Hiking"]
  }
]

```
## Using Size of the Array
**Command**

```json
db.userData.find({"hobbies": {$size: 3}})
```
**Output**
```json
[
  {
    "_id": ObjectId("674dd638f4e6bcc56c0d8193"),
    "name": "Chris",
    "hobbies": ["Sports", "Cooking", "Hiking"]
  }
]
```
## Searching by the Array Containing The Items Given
**Command**

```json
use boxOffice
db.movieStarts.find({"genre": {$all: ["action", "thriller"]}})
```
**Output**
```json
[
  {
    "_id": ObjectId("674c861a94a0baf752b8d446"),
    "title": "Teach me if you can",
    "meta": { "rating": 8.5, "aired": 2014, "runtime": 90 },
    "visitors": 590378,
    "expectedVisitors": 500000,
    "genre": ["action", "thriller"]
  },
  {
    "_id": ObjectId("674c861a94a0baf752b8d447"),
    "title": "Supercharged Teaching",
    "meta": { "rating": 9.3, "aired": 2016, "runtime": 60 },
    "visitors": 370000,
    "expectedVisitors": 1000000,
    "genre": ["thriller", "action"]
  },
  {
    "_id": ObjectId("674c861a94a0baf752b8d448"),
    "title": "The Last Student Returns",
    "meta": { "rating": 9.5, "aired": 2018, "runtime": 100 },
    "visitors": 1300000,
    "expectedVisitors": 1550000,
    "genre": ["thriller", "drama", "action"]
  }
]
```
## Querying Arrays by Matching the Exact Element(s)
**Command**

```json
use users
db.userData.find({"hobbies": {$elemMatch: {"hobbies.title": "Sports", "frequency": {$gte: 3}}}})
```
**Output**
```json
[
  {
    "_id": ObjectId("674dd41ff4e6bcc56c0d8192"),
    "name": "Max",
    "phone": "12345322",
    "hobbies": [
      { "title": "Sports", "frequency": 3 },
      { "title": "Cooking", "frequency": 6 }
    ]
  }
]
```