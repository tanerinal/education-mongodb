## End All Operation when Duplication Key or Not?

### Prepare Database and hobbies Collection
**Command**
```java
use social
db.hobbies.insertMany([{"_id": "yoga", "name": "Yoga"}, 
{"_id": "football", "name": "Football"}, 
{"_id": "cars", "name": "Cars"}])
```
**Output**
```json
switched to db social
{
  acknowledged: true,
  insertedIds: { '0': 'yoga', '1': 'football', '2': 'cars' }
}
```

### Current Data

**Command**
```json
db.hobbies.find()
```
**Output**
```json
[
  { _id: 'yoga', name: 'Yoga' },
  { _id: 'football', name: 'Football' },
  { _id: 'cars', name: 'Cars' }
]
```

### Insert an Array of Documents Which Has an Document Having Overlapping ID with One of Current Documents

**Command**
```json
db.hobbies.insertMany([{"_id": "photography", "name": "Photography"}, 
{"_id": "cars", "name": "Cars"}, 
{"_id": "hiking", "name": "Hiking"}])
```
**Output**
```json
Uncaught:
MongoBulkWriteError: E11000 duplicate key error collection: social.hobbies index: _id_ dup key: { _id: "cars" }
Result: BulkWriteResult {
  insertedCount: 1,
  matchedCount: 0,
  modifiedCount: 0,
  deletedCount: 0,
  upsertedCount: 0,
  upsertedIds: {},
  insertedIds: { '0': 'photography' }
}
Write Errors: [
  WriteError {
    err: {
      index: 1,
      code: 11000,
      errmsg: 'E11000 duplicate key error collection: social.hobbies index: _id_ dup key: { _id: "cars" }',
      errInfo: undefined,
      op: { _id: 'cars', name: 'Cars' }
    }
  }
]
```
> Here, `insertedCount: 1` says it inserted one document.

### Current Data

**Command **
```json
db.hobbies.find()
```
** Output **
```json
[
  { _id: 'yoga', name: 'Yoga' },
  { _id: 'football', name: 'Football' },
  { _id: 'cars', name: 'Cars' },
  { _id: 'photography', name: 'Photography' } //Inserts this one but not the others since the second document has overlapping _id with current.
]
```
### Insert an Array of Documents Which Has Document(s) Having Overlapping ID with Current Documents

**Command**
```json
db.hobbies.insertMany([{"_id": "photography", "name": "Photography"}, 
  {"_id": "diving", "name": "Diving"}, 
  {"_id": "cars", "name": "Cars"}, 
  {"_id": "hiking", "name": "Hiking"}],
{"ordered": false}  //default value is: true
)
```
**Output**
```json
Uncaught:
MongoBulkWriteError: E11000 duplicate key error collection: social.hobbies index: _id_ dup key: { _id: "photography" }
Result: BulkWriteResult {
  insertedCount: 2,
  matchedCount: 0,
  modifiedCount: 0,
  deletedCount: 0,
  upsertedCount: 0,
  upsertedIds: {},
  insertedIds: { '1': 'diving', '3': 'hiking' }
}
Write Errors: [
  WriteError {
    err: {
      index: 0,
      code: 11000,
      errmsg: 'E11000 duplicate key error collection: social.hobbies index: _id_ dup key: { _id: "photography" }',
      errInfo: undefined,
      op: { _id: 'photography', name: 'Photography' }
    }
  },
  WriteError {
    err: {
      index: 2,
      code: 11000,
      errmsg: 'E11000 duplicate key error collection: social.hobbies index: _id_ dup key: { _id: "cars" }',
      errInfo: undefined,
      op: { _id: 'cars', name: 'Cars' }
    }
  }
]
```
> Here, `insertedCount: 2` and `insertedIds: { '1': 'diving', '3': 'hiking' }` says it inserted one document even there is duplicate key errors..

### Current Data

**Command **
```json
db.hobbies.find()
```
** Output **
```json
[
  { _id: 'yoga', name: 'Yoga' },
  { _id: 'football', name: 'Football' },
  { _id: 'cars', name: 'Cars' },
  { _id: 'photography', name: 'Photography' },
  { _id: 'diving', name: 'Diving' },  //Inserted 
  { _id: 'hiking', name: 'Hiking' }   //Inserted
]
```