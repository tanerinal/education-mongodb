## Current Data

**Command**
```json
use userData
db.userData.find()
```
**Output**
```json
[
  {
    "_id": ObjectId("67570a5c1df5ee46ca39248e"),
    "name": "Chris",
    "hobbies": [ "Sports", "Cooking", "Hiking" ]
  },
  {
    "_id": ObjectId("67570a5c1df5ee46ca39248f"),
    "name": "Max",
    "hobbies": [
      { "title": "Sports", "frequency": 3 },
      { "title": "Cooking", "frequency": 6 }
    ],
    "phone": 131782734
  },
  {
    "_id": ObjectId("67570a5c1df5ee46ca392490"),
    "name": "Manuel",
    "hobbies": [
      { "title": "Cooking", "frequency": 5 },
      { "title": "Cars", "frequency": 2 }
    ],
    "phone": "012177972",
    "age": 30
  },
  {
    "_id": ObjectId("67570a5c1df5ee46ca392491"),
    "name": "Anna",
    "hobbies": [
      { "title": "Sports", "frequency": 2 },
      { "title": "Yoga", "frequency": 3 }
    ],
    "phone": "80811987291",
    "age": null
  }
]
```

## Updating One Document

**Command**
```json
db.userData.updateOne({"_id": ObjectId("67570a5c1df5ee46ca39248e")}, {$set: {"hobbies": [{ "title": "Sports", "frequency": 5 }, { "title": "Cooking", "frequency": 3 }, { "title": "Hiking", "frequency": 1 }]}})

db.userData.findOne({"_id": ObjectId("67570a5c1df5ee46ca39248e")})
```
**Output**
```json
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}

{
  "_id": ObjectId("67570a5c1df5ee46ca39248e"),
  "name": "Chris",
  "hobbies": [
    { "title": "Sports", "frequency": 5 },
    { "title": "Cooking", "frequency": 3 },
    { "title": "Hiking", "frequency": 1 }
  ]
}
```

## Updating Many Records & Adding Field To Documents

### Current Data

**Command**
```json
db.userData.find({"hobbies.title": "Sports"})
```
**Output**
```json
[
  {
    "_id": ObjectId("67570a5c1df5ee46ca39248e"),
    "name": "Chris",
    "hobbies": [
      { "title": "Sports", "frequency": 5 },
      { "title": "Cooking", "frequency": 3 },
      { "title": "Hiking", "frequency": 1 }
    ]
  },
  {
    "_id": ObjectId("67570a5c1df5ee46ca39248f"),
    "name": "Max",
    "hobbies": [
      { "title": "Sports", "frequency": 3 },
      { "title": "Cooking", "frequency": 6 }
    ],
    "phone": 131782734
  },
  {
    "_id": ObjectId("67570a5c1df5ee46ca392491"),
    "name": "Anna",
    "hobbies": [
      { "title": "Sports", "frequency": 2 },
      { "title": "Yoga", "frequency": 3 }
    ],
    "phone": "80811987291",
    "age": null
  }
]
```

**Command**
```json
db.userData.updateMany({"hobbies.title": "Sports"}, {$set: {"isSporty": true}})
```

**Output**
```json
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 3,
  modifiedCount: 3,
  upsertedCount: 0
}

[
  {
    "_id": ObjectId("67570a5c1df5ee46ca39248e"),
    "name": "Chris",
    "hobbies": [
      { "title": "Sports", "frequency": 5 },
      { "title": "Cooking", "frequency": 3 },
      { "title": "Hiking", "frequency": 1 }
    ],
    "isSporty": true
  },
  {
    "_id": ObjectId("67570a5c1df5ee46ca39248f"),
    "name": "Max",
    "hobbies": [
      { "title": "Sports", "frequency": 3 },
      { "title": "Cooking", "frequency": 6 }
    ],
    "phone": 131782734,
    "isSporty": true
  },
  {
    "_id": ObjectId("67570a5c1df5ee46ca392490"),
    "name": "Manuel",
    "hobbies": [
      { "title": "Cooking", "frequency": 5 },
      { "title": "Cars", "frequency": 2 }
    ],
    "phone": "012177972",
    "age": 30
  },
  {
    "_id": ObjectId("67570a5c1df5ee46ca392491"),
    "name": "Anna",
    "hobbies": [
      { "title": "Sports", "frequency": 2 },
      { "title": "Yoga", "frequency": 3 }
    ],
    "phone": "80811987291",
    "age": null,
    "isSporty": true
  }
]
```
## Updating Multiple Fields

**Command**
```json
db.userData.updateOne({"_id": ObjectId("67570a5c1df5ee46ca39248e")}, {$set: {"age": 40, "phone": 4882736829}})

db.userData.findOne({"_id": ObjectId("67570a5c1df5ee46ca39248e")})
```
**Output**
```json
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}

{
  "_id": ObjectId("67570a5c1df5ee46ca39248e"),
  "name": "Chris",
  "hobbies": [
    { "title": "Sports", "frequency": 5 },
    { "title": "Cooking", "frequency": 3 },
    { "title": "Hiking", "frequency": 1 }
  ],
  "isSporty": true,
  "age": 40,
  "phone": 4882736829
}
```
## Executing Multiple Operations

**Command**
```json
db.userData.findOne({"name": "Manuel"})

db.userData.updateOne({"name": "Manuel"}, {$inc: {"age": 1}, $set: {"isSporty": false}})

db.userData.findOne({"name": "Manuel"})
```
**Output**
```json
{
  "_id": ObjectId("67570a5c1df5ee46ca392490"),
  "name": "Manuel",
  "hobbies": [
    { "title": "Cooking", "frequency": 5 },
    { "title": "Cars", "frequency": 2 }
  ],
  "phone": "012177972",
  "age": 30
}

{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}

{
  "_id": ObjectId("67570a5c1df5ee46ca392490"),
  "name": "Manuel",
  "hobbies": [
    { "title": "Cooking", "frequency": 5 },
    { "title": "Cars", "frequency": 2 }
  ],
  "phone": "012177972",
  "age": 31,
  "isSporty": false
}
```

## Getting Rid of a Field

**Command**
```json
db.userData.find({"isSporty": true})

db.userData.updateMany({"isSporty": true}, {$unset: {"phone": ""}})

db.userData.find({"isSporty": true})
```
**Output**
```json
[
  {
    "_id": ObjectId("67570a5c1df5ee46ca39248e"),
    "name": "Chris",
    "hobbies": [
      { "title": "Sports", "frequency": 5 },
      { "title": "Cooking", "frequency": 3 },
      { "title": "Hiking", "frequency": 1 }
    ],
    "isSporty": true,
    "age": 40,
    "phone": 4882736829
  },
  {
    "_id": ObjectId("67570a5c1df5ee46ca39248f"),
    "name": "Max",
    "hobbies": [
      { "title": "Sports", "frequency": 3 },
      { "title": "Cooking", "frequency": 6 }
    ],
    "phone": 131782734,
    "isSporty": true
  },
  {
    "_id": ObjectId("67570a5c1df5ee46ca392491"),
    "name": "Anna",
    "hobbies": [
      { "title": "Sports", "frequency": 2 },
      { "title": "Yoga", "frequency": 3 }
    ],
    "phone": "80811987291",
    "age": null,
    "isSporty": true
  }
]

{
  acknowledged: true,
  insertedId: null,
  matchedCount: 3,
  modifiedCount: 3,
  upsertedCount: 0
}

[
  {
    "_id": ObjectId("67570a5c1df5ee46ca39248e"),
    "name": "Chris",
    "hobbies": [
      { "title": "Sports", "frequency": 5 },
      { "title": "Cooking", "frequency": 3 },
      { "title": "Hiking", "frequency": 1 }
    ],
    "isSporty": true,
    "age": 40
  },
  {
    "_id": ObjectId("67570a5c1df5ee46ca39248f"),
    "name": "Max",
    "hobbies": [
      { "title": "Sports", "frequency": 3 },
      { "title": "Cooking", "frequency": 6 }
    ],
    "isSporty": true
  },
  {
    "_id": ObjectId("67570a5c1df5ee46ca392491"),
    "name": "Anna",
    "hobbies": [
      { "title": "Sports", "frequency": 2 },
      { "title": "Yoga", "frequency": 3 }
    ],
    "age": null,
    "isSporty": true
  }
]
```
## Renaming a Field

**Command**
```json
db.userData.find()

db.userData.updatemMany({}, {$rename: {"age": "totalAge"}})

db.userData.find({"isSporty": true})
```
**Output**
```json
[
  {
    "_id": ObjectId("67570a5c1df5ee46ca39248e"),
    "name": "Chris",
    "hobbies": [
      { "title": "Sports", "frequency": 5 },
      { "title": "Cooking", "frequency": 3 },
      { "title": "Hiking", "frequency": 1 }
    ],
    "isSporty": true,
    "age": 40
  },
  {
    "_id": ObjectId("67570a5c1df5ee46ca39248f"),
    "name": "Max",
    "hobbies": [
      { "title": "Sports", "frequency": 3 },
      { "title": "Cooking", "frequency": 6 }
    ],
    "isSporty": true
  },
  {
    "_id": ObjectId("67570a5c1df5ee46ca392490"),
    "name": "Manuel",
    "hobbies": [
      { "title": "Cooking", "frequency": 5 },
      { "title": "Cars", "frequency": 2 }
    ],
    "phone": "012177972",
    "age": 31,
    "isSporty": false
  },
  {
    "_id": ObjectId("67570a5c1df5ee46ca392491"),
    "name": "Anna",
    "hobbies": [
      { "title": "Sports", "frequency": 2 },
      { "title": "Yoga", "frequency": 3 }
    ],
    "age": null,
    "isSporty": true
  }
]


{
  acknowledged: true,
  insertedId: null,
  matchedCount: 4,
  modifiedCount: 3,
  upsertedCount: 0
}

[
  {
    "_id": ObjectId("67570a5c1df5ee46ca39248e"),
    "name": "Chris",
    "hobbies": [
      { "title": "Sports", "frequency": 5 },
      { "title": "Cooking", "frequency": 3 },
      { "title": "Hiking", "frequency": 1 }
    ],
    "isSporty": true,
    "totalAge": 40
  },
  {
    "_id": ObjectId("67570a5c1df5ee46ca39248f"),
    "name": "Max",
    "hobbies": [
      { "title": "Sports", "frequency": 3 },
      { "title": "Cooking", "frequency": 6 }
    ],
    "isSporty": true
  },
  {
    "_id": ObjectId("67570a5c1df5ee46ca392490"),
    "name": "Manuel",
    "hobbies": [
      { "title": "Cooking", "frequency": 5 },
      { "title": "Cars", "frequency": 2 }
    ],
    "phone": "012177972",
    "totalAge": 31,
    "isSporty": false
  },
  {
    "_id": ObjectId("67570a5c1df5ee46ca392491"),
    "name": "Anna",
    "hobbies": [
      { "title": "Sports", "frequency": 2 },
      { "title": "Yoga", "frequency": 3 }
    ],
    "totalAge": null,
    "isSporty": true
  }
]
```
## upserting a Document

**Command**
```json
db.userData.find({"name": "Maria"})

db.userData.updateMany({"name": "Maria"}, {"$set": {"hobbies": [{"title": "Good food", "frequency": 3}], "isSporty": true}}, {"upsert": true});

db.userData.find({"name": "Maria"})
```
**Output**
```json
NULL

{
  acknowledged: true,
  insertedId: ObjectId('6757156e781905fb7c6d1f0f'),
  matchedCount: 0,
  modifiedCount: 0,
  upsertedCount: 1
}

[
  {
    "_id": ObjectId("6757156e781905fb7c6d1f0f"),
    "name": "Maria",
    "hobbies": [
      { "title": "Good food", "frequency": 3 }
    ],
    "isSporty": true
  }
]
```