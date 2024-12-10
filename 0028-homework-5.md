## Task-1: Create a New Collection ("sports") and Upsert Three New Documents into it with These Fields: "title", "requiresTeam" 

**Command**
```json
use sportsData
db.sports.updateMany({"title": "football"}, {$set: {"requiresTeam": true}}, {"upsert": true})
db.sports.updateMany({"title": "handball"}, {$set: {"requiresTeam": true}}, {"upsert": true})
db.sports.updateMany({"title": "running"}, {$set: {"requiresTeam": false}}, {"upsert": true})

```
**Output**
```json
switched to db sportsData.
{
  acknowledged: true,
  insertedId: ObjectId('6757bfdf781905fb7c6d1f10'),
  matchedCount: 0,
  modifiedCount: 0,
  upsertedCount: 1
}

{
  acknowledged: true,
  insertedId: ObjectId('6757c047781905fb7c6d1f11'),
  matchedCount: 0,
  modifiedCount: 0,
  upsertedCount: 1
}

{
  acknowledged: true,
  insertedId: ObjectId('6757c04e781905fb7c6d1f12'),
  matchedCount: 0,
  modifiedCount: 0,
}
```

### Current Data
**Command**

```json
db.sports.find()
```
**Output**
```json
[
  {
    "_id": ObjectId("6757bfdf781905fb7c6d1f10"),
    "title": "football",
    "requiresTeam": true
  },
  {
    "_id": ObjectId("6757c047781905fb7c6d1f11"),
    "title": "handball",
    "requiresTeam": true
  },
  {
    "_id": ObjectId("6757c04e781905fb7c6d1f12"),
    "title": "running",
    "requiresTeam": false
  }
]

```
## Task-2: Update All Documents Which Do Require a Team By Adding a New Field as "minimumPlayerCount"

**Command**
```json
db.sports.updateMany({"requiresTeam": true}, {$set: {"minimumPlayerCount": 22}})
db.sports.find()
```
**Output**
```json
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 2,
  modifiedCount: 2,
  upsertedCount: 0
}

[
  {
    "_id": ObjectId("6757bfdf781905fb7c6d1f10"),
    "title": "football",
    "requiresTeam": true,
    "minimumPlayerCount": 22
  },
  {
    "_id": ObjectId("6757c047781905fb7c6d1f11"),
    "title": "handball",
    "requiresTeam": true,
    "minimumPlayerCount": 22
  },
  {
    "_id": ObjectId("6757c04e781905fb7c6d1f12"),
    "title": "running",
    "requiresTeam": false
  }
]

```
## Task-3: Update All Documents Which Requires a Team by Incrementing the Number of Required Players by 10

**Command**
```json
db.sports.updateMany({"requiresTeam": true}, {$inc: {"minimumPlayerCount": 10}})
db.sports.find()
```
**Output**
```json
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 2,
  modifiedCount: 2,
  upsertedCount: 0
}

[
  {
    "_id": ObjectId("6757bfdf781905fb7c6d1f10"),
    "title": "football",
    "requiresTeam": true,
    "minimumPlayerCount": 32
  },
  {
    "_id": ObjectId("6757c047781905fb7c6d1f11"),
    "title": "handball",
    "requiresTeam": true,
    "minimumPlayerCount": 32
  },
  {
    "_id": ObjectId("6757c04e781905fb7c6d1f12"),
    "title": "running",
    "requiresTeam": false
  }
]
```