## Updating Matched Array Elements

**Command**
```json
use users

db.userData.find({"hobbies": {$elemMatch: {"title": "Sports", "frequency": {$gte: 3}}}})

db.userData.updateMany({"hobbies": {$elemMatch: {"title": "Sports", "frequency": {$gte: 3}}}}, {$set: {"hobbies.$.highFrequency": true}})

db.userData.find()
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
    "isSporty": false,
    "totalAge": 31
  },
  {
    "_id": ObjectId("67570a5c1df5ee46ca392491"),
    "name": "Anna",
    "hobbies": [
      { "title": "Sports", "frequency": 2 },
      { "title": "Yoga", "frequency": 3 }
    ],
    "isSporty": true,
    "totalAge": null
  },
  {
    "_id": ObjectId("6757156e781905fb7c6d1f0f"),
    "name": "Maria",
    "hobbies": [
      { "title": "Good food", "frequency": 3 }
    ],
    "isSporty": true
  }
]

{
  acknowledged: true,
  insertedId: null,
  matchedCount: 2,
  modifiedCount: 2,
  upsertedCount: 0
}

[
  {
    "_id": ObjectId("67570a5c1df5ee46ca39248e"),
    "name": "Chris",
    "hobbies": [
      { "title": "Sports", "frequency": 5, "highFrequency": true },
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
      { "title": "Sports", "frequency": 3, "highFrequency": true },
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
    "isSporty": false,
    "totalAge": 31
  },
  {
    "_id": ObjectId("67570a5c1df5ee46ca392491"),
    "name": "Anna",
    "hobbies": [
      { "title": "Sports", "frequency": 2 },
      { "title": "Yoga", "frequency": 3 }
    ],
    "isSporty": true,
    "totalAge": null
  },
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

## Updating All Array Elements Not First Matched One

**Command**
```json
db.userData.find({"totalAge": {$gt: 30}})

db.userData.updateMany({"totalAge": {$gt: 30}}, {$inc: {"hobbies.$[].frequency": -1}})

db.userData.find({"totalAge": {$gt: 30}})
```
**Output**
```json
[
  {
    "_id": ObjectId("67570a5c1df5ee46ca39248e"),
    "name": "Chris",
    "hobbies": [
      { "title": "Sports", "frequency": 5, "highFrequency": true },
      { "title": "Cooking", "frequency": 3 },
      { "title": "Hiking", "frequency": 1 }
    ],
    "isSporty": true,
    "totalAge": 40
  },
  {
    "_id": ObjectId("67570a5c1df5ee46ca392490"),
    "name": "Manuel",
    "hobbies": [
      { "title": "Cooking", "frequency": 5 },
      { "title": "Cars", "frequency": 2 }
    ],
    "phone": "012177972",
    "isSporty": false,
    "totalAge": 31
  }
]

{
  acknowledged: true,
  insertedId: null,
  matchedCount: 2,
  modifiedCount: 2,
  upsertedCount: 0
}

[
  {
    "_id": ObjectId("67570a5c1df5ee46ca39248e"),
    "name": "Chris",
    "hobbies": [
      { "title": "Sports", "frequency": 4, "highFrequency": true },
      { "title": "Cooking", "frequency": 2 },
      { "title": "Hiking", "frequency": 0 }
    ],
    "isSporty": true,
    "totalAge": 40
  },
  {
    "_id": ObjectId("67570a5c1df5ee46ca392490"),
    "name": "Manuel",
    "hobbies": [
      { "title": "Cooking", "frequency": 4 },
      { "title": "Cars", "frequency": 1 }
    ],
    "phone": "012177972",
    "isSporty": false,
    "totalAge": 31
  }
]
```

## Finding and Updating Specific Fields

### Current Data

**Command**
```json
db.userData.find({"hobbies.frequency": {$gt: 2}})

db.userData.updateMany({"hobbies.frequency": {$gt: 2}}, {$set: {"hobbies.$[el].goodFrequency": true}}, {"arrayFilters": [{"el.frequency": {$gt: 2}}]})

db.userData.find({"hobbies.frequency": {$gt: 2}})
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
        "highFrequency": true
      },
      { "title": "Cooking", "frequency": 2 },
      { "title": "Hiking", "frequency": 0 }
    ],
    "isSporty": true,
    "totalAge": 40
  },
  {
    "_id": ObjectId("67570a5c1df5ee46ca39248f"),
    "name": "Max",
    "hobbies": [
      {
        "title": "Sports",
        "frequency": 3,
        "highFrequency": true
      },
      { "title": "Cooking", "frequency": 6}
    ],
    "isSporty": true
  },
  {
    "_id": ObjectId("67570a5c1df5ee46ca392490"),
    "name": "Manuel",
    "hobbies": [
      { "title": "Cooking", "frequency": 4},
      { "title": "Cars", "frequency": 1 }
    ],
    "phone": "012177972",
    "isSporty": false,
    "totalAge": 31
  },
  {
    "_id": ObjectId("67570a5c1df5ee46ca392491"),
    "name": "Anna",
    "hobbies": [
      { "title": "Sports", "frequency": 2 },
      { "title": "Yoga", "frequency": 3}
    ],
    "isSporty": true,
    "totalAge": null
  },
  {
    "_id": ObjectId("6757156e781905fb7c6d1f0f"),
    "name": "Maria",
    "hobbies": [
      { "title": "Good food", "frequency": 3}
    ],
    "isSporty": true
  }
]

{
  acknowledged: true,
  insertedId: null,
  matchedCount: 5,
  modifiedCount: 5,
  upsertedCount: 0
}

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
  },
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
      { "title": "Cooking", "frequency": 6, "goodFrequency": true }
    ],
    "isSporty": true
  },
  {
    "_id": ObjectId("67570a5c1df5ee46ca392490"),
    "name": "Manuel",
    "hobbies": [
      { "title": "Cooking", "frequency": 4, "goodFrequency": true },
      { "title": "Cars", "frequency": 1 }
    ],
    "phone": "012177972",
    "isSporty": false,
    "totalAge": 31
  },
  {
    "_id": ObjectId("67570a5c1df5ee46ca392491"),
    "name": "Anna",
    "hobbies": [
      { "title": "Sports", "frequency": 2 },
      { "title": "Yoga", "frequency": 3, "goodFrequency": true }
    ],
    "isSporty": true,
    "totalAge": null
  },
  {
    "_id": ObjectId("6757156e781905fb7c6d1f0f"),
    "name": "Maria",
    "hobbies": [
      { "title": "Good food", "frequency": 3, "goodFrequency": true }
    ],
    "isSporty": true
  }
]
```
## Adding Data to Arrays

### Current Data

**Command**
```json
db.userData.find({"name": "Maria"})

db.userData.updateOne({"name": "Maria"}, {$push: {"hobbies": {"title": "Sports", "frequency": 2}}})

db.userData.find({"name": "Maria"})
```
**Output**
```json
[
  {
    "_id": ObjectId("6757156e781905fb7c6d1f0f"),
    "name": "Maria",
    "hobbies": [
      { "title": "Good food", "frequency": 3, "goodFrequency": true }
    ],
    "isSporty": true
  }
]

{
  "acknowledged": true,
  "insertedId": null,
  "matchedCount": 1,
  "modifiedCount": 1,
  "upsertedCount": 0
}

[
  {
    "_id": ObjectId("6757156e781905fb7c6d1f0f"),
    "name": "Maria",
    "hobbies": [
      { "title": "Good food", "frequency": 3, "goodFrequency": true },
      { "title": "Sports", "frequency": 2 }
    ],
    "isSporty": true
  }
]

```

## Adding Mutiple Data to Arrays

### Current Data

**Command**
```json
db.userData.find({"name": "Maria"})

db.userData.updateOne({"name": "Maria"}, {$push: {"hobbies": {$each: [{"title": "Good Vine", "frequency": 1}, {"title": "Hiking", "frequency": 2}], $sort: {"frequency": -1}}}})

db.userData.find({"name": "Maria"})
```

> Use *$addToSet* command instead of $push in order to prevent adding exact same element(s) into the array.

**Output**
```json
[
  {
    "_id": ObjectId("6757156e781905fb7c6d1f0f"),
    "name": "Maria",
    "hobbies": [
      { "title": "Good food", "frequency": 3, "goodFrequency": true },
      { "title": "Sports", "frequency": 2 }
    ],
    "isSporty": true
  }
]

{
  "acknowledged": true,
  "insertedId": null,
  "matchedCount": 1,
  "modifiedCount": 1,
  "upsertedCount": 0
}

[
  {
    "_id": ObjectId("6757156e781905fb7c6d1f0f"),
    "name": "Maria",
    "hobbies": [
      { "title": "Good food", "frequency": 3, "goodFrequency": true },
      { "title": "Sports", "frequency": 2 },
      { "title": "Hiking", "frequency": 2 },
      { "title": "Good Vine", "frequency": 1 }
    ],
    "isSporty": true
  }
]
```
>It adds the items in descending order of *frequency* field values.

## Removing Data from Arrays

### Current Data

**Command**
```json
db.userData.find({"name": "Maria"})

db.userData.updateOne({"name": "Maria"}, {$pull: {"hobbies": {"title": "Good Vine"}}})

db.userData.find({"name": "Maria"})
```
**Output**
```json
[
  {
    "_id": ObjectId("6757156e781905fb7c6d1f0f"),
    "name": "Maria",
    "hobbies": [
      { "title": "Good food", "frequency": 3, "goodFrequency": true },
      { "title": "Sports", "frequency": 2 },
      { "title": "Hiking", "frequency": 2 },
      { "title": "Hiking", "frequency": 2 },
      { "title": "Good Vine", "frequency": 1 },
      { "title": "Good Vine", "frequency": 1 }
    ],
    "isSporty": true
  }
]

{
  "acknowledged": true,
  "insertedId": null,
  "matchedCount": 1,
  "modifiedCount": 1,
  "upsertedCount": 0
}

[
  {
    "_id": ObjectId("6757156e781905fb7c6d1f0f"),
    "name": "Maria",
    "hobbies": [
      { "title": "Good food", "frequency": 3, "goodFrequency": true },
      { "title": "Sports", "frequency": 2 },
      { "title": "Hiking", "frequency": 2 },
      { "title": "Hiking", "frequency": 2 }
    ],
    "isSporty": true
  }
]
```