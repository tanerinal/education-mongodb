## Deleting One Document

**Command**
```json
use users

db.userData.find({"name": "Chris"})

db.userData.deleteOne({"name": "Chris"})

db.userData.find({"name": "Chris"})
```
**Output**
```json
[
  {
    "_id": ObjectId("67570a5c1df5ee46ca39248e"),
    "name": "Chris",
    "hobbies": [
      {
        "title": "Sports",
        "frequency": 4,
        "highFrequency": true,
        "goodFrequency": true
      },
      { "title": "Cooking", "frequency": 2 },
      { "title": "Hiking", "frequency": 0 }
    ],
    "isSporty": true,
    "totalAge": 40
  }
]

{
  "acknowledged": true,
  "deletedCount": 1
}

*NULL*
```

## Deleting Many Documents

**Command**
```json
db.userData.find({"totalAge": {$exists: false}, "isSporty": true})

db.userData.deleteMany({"totalAge": {$exists: false}, "isSporty": true})

db.userData.find({"totalAge": {$exists: false}, "isSporty": true})
```
**Output**
```json
[
  {
    "_id": ObjectId("67570a5c1df5ee46ca39248f"),
    "name": "Max",
    "hobbies": [
      {
        "title": "Sports",
        "frequency": 3,
        "highFrequency": true,
        "goodFrequency": true
      },
      {
        "title": "Cooking",
        "frequency": 6,
        "goodFrequency": true
      }
    ],
    "isSporty": true
  },
  {
    "_id": ObjectId("6757156e781905fb7c6d1f0f"),
    "name": "Maria",
    "hobbies": [
      {
        "title": "Good food",
        "frequency": 3,
        "goodFrequency": true
      },
      {
        "title": "Sports",
        "frequency": 2
      }
    ],
    "isSporty": true
  }
]

{
  "acknowledged": true,
  "deletedCount": 2
}

*NULL*
```

## Deleting All Entries of a Collections

**Command**
```json
db.userData.find({})

db.userData.deleteMany({})

db.userData.find({})
```
**Output**
```json
[
  {
    "_id": ObjectId("67570a5c1df5ee46ca392490"),
    "name": "Manuel",
    "hobbies": [
      {
        "title": "Cooking",
        "frequency": 4,
        "goodFrequency": true
      },
      {
        "title": "Cars",
        "frequency": 1
      }
    ],
    "phone": "012177972",
    "isSporty": false,
    "totalAge": 31
  },
  {
    "_id": ObjectId("67570a5c1df5ee46ca392491"),
    "name": "Anna",
    "hobbies": [
      {
        "title": "Sports",
        "frequency": 2
      },
      {
        "title": "Yoga",
        "frequency": 3,
        "goodFrequency": true
      }
    ],
    "isSporty": true,
    "totalAge": null
  }
]

{
  "acknowledged": true,
  "deletedCount": 2
}

*NULL*
```

## Deleting a Collection and Database

**Command**
```json
show collections

db.userData.drop()

show collections

show dbs

db.dropDatabase()

show dbs
```
**Output**
```console
users> show collections
userData
users> db.userData.drop()
true
users> show collections

users> show dbs
admin           40.00 KiB
blog           112.00 KiB
bookStore       80.00 KiB
boxOffice       80.00 KiB
config         108.00 KiB
economy         72.00 KiB
financialData   40.00 KiB
local           72.00 KiB
movieData      188.00 KiB
social          72.00 KiB
sportsData      72.00 KiB
users> db.dropDatabase()
{ ok: 1, dropped: 'users' }
users> show dbs
admin           40.00 KiB
blog           112.00 KiB
bookStore       80.00 KiB
boxOffice       80.00 KiB
config         108.00 KiB
economy         72.00 KiB
financialData   40.00 KiB
local           72.00 KiB
movieData      188.00 KiB
social          72.00 KiB
sportsData      72.00 KiB
users>
```