## Task-1: Import the Data within the file extended-boxoffice.json into a boxOffice Database with a New Collection Named exmoviestarts

**Command**
```json
mongoimport D:\..........04-boxoffice-extended.json -d boxOffice -c exMovieStarts --jsonArray
```
**Output**
```java
2024-12-02T19:13:28.859+0300    connected to: mongodb://localhost/
2024-12-02T19:13:28.973+0300    3 document(s) imported successfully. 0 document(s) failed to import.
```

### Current Data
**Command**

```json
use boxOffice
db.exMovieStarts.find()
```
**Output**
```json
[
  {
    "_id": ObjectId("674ddca8df11c7bb5c7d1069"),
    "title": "The Last Student Returns",
    "meta": { "rating": 9.5, "aired": 2018, "runtime": 100 },
    "visitors": 1300000,
    "expectedVisitors": 1550000,
    "genre": ["thriller", "drama", "action"],
    "ratings": [10, 9]
  },
  {
    "_id": ObjectId("674ddca8df11c7bb5c7d106a"),
    "title": "Supercharged Teaching",
    "meta": { "rating": 9.3, "aired": 2016, "runtime": 60 },
    "visitors": 370000,
    "expectedVisitors": 1000000,
    "genre": ["thriller", "action"],
    "ratings": [10, 9, 9]
  },
  {
    "_id": ObjectId("674ddca8df11c7bb5c7d106b"),
    "title": "Teach me if you can",
    "meta": { "rating": 8, "aired": 2014, "runtime": 90 },
    "visitors": 590378,
    "expectedVisitors": 500000,
    "genre": ["action", "thriller"],
    "ratings": [8, 8]
  }
]
```
## Task-2: Search All Movies That Have Exactly Two Genres

**Command**
```json
db.exMovieStarts.find({"genre": {$size: 2}})
```
**Output**
```json
[
  {
    "_id": ObjectId("674ddca8df11c7bb5c7d106a"),
    "title": "Supercharged Teaching",
    "meta": { "rating": 9.3, "aired": 2016, "runtime": 60 },
    "visitors": 370000,
    "expectedVisitors": 1000000,
    "genre": ["thriller", "action"],
    "ratings": [10, 9, 9]
  },
  {
    "_id": ObjectId("674ddca8df11c7bb5c7d106b"),
    "title": "Teach me if you can",
    "meta": { "rating": 8, "aired": 2014, "runtime": 90 },
    "visitors": 590378,
    "expectedVisitors": 500000,
    "genre": ["action", "thriller"],
    "ratings": [8, 8]
  }
]
```
## Task-3: Search All Movies That Aired in 2018

**Command**
```json
db.exMovieStarts.find({"meta.aired": 2018})
```
**Output**
```json
[
  {
    "_id": ObjectId("674ddca8df11c7bb5c7d1069"),
    "title": "The Last Student Returns",
    "meta": { "rating": 9.5, "aired": 2018, "runtime": 100 },
    "visitors": 1300000,
    "expectedVisitors": 1550000,
    "genre": ["thriller", "drama", "action"],
    "ratings": [10, 9]
  }
]
```
## Task-4: Search All Movies That Have Ratings Greater Than 8 but Lower Than 10

**Command**
```json
db.exMovieStarts.find({$and: [{"ratings": {$gt: 8}}, {"ratings": {$lt: 10}}]})
db.exMovieStarts.find({"ratings": {$elemMatch: {$gt: 8, $lt: 10}}})
```
**Output**
```json
[
  {
    "_id": ObjectId("674ddca8df11c7bb5c7d1069"),
    "title": "The Last Student Returns",
    "meta": { "rating": 9.5, "aired": 2018, "runtime": 100 },
    "visitors": 1300000,
    "expectedVisitors": 1550000,
    "genre": ["thriller", "drama", "action"],
    "ratings": [10, 9]
  },
  {
    "_id": ObjectId("674ddca8df11c7bb5c7d106a"),
    "title": "Supercharged Teaching",
    "meta": { "rating": 9.3, "aired": 2016, "runtime": 60 },
    "visitors": 370000,
    "expectedVisitors": 1000000,
    "genre": ["thriller", "action"],
    "ratings": [10, 9, 9]
  }
]
```