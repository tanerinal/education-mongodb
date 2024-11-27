## Current data

**Command**
```json
db.flightsData.find()
```
**Output**
```json
[
  {
    _id: ObjectId('67471edcb95dc4b9a70d8190'),
    departureAirport: 'MUC',
    arrivalAirport: 'SFO',
    aircraft: 'Airbus A380',
    distance: 12000,
    intercontinental: true
  },
  {
    _id: ObjectId('67472fc9b95dc4b9a70d8191'),
    departureAirport: 'IST',
    arrivalAirport: 'AYT'
  },
  { _id: 'my_id', departureAirport: 'SAW', arrivalAirport: 'AYT' }
]
```

## Deleting One Document
**Command**
```json
db.flightsData.deleteOne({
    "departureAirport": "MUC"
  })
```
**Output**
```json
{ acknowledged: true, deletedCount: 1 }
```
## Updating One Document
**Command**
```json
db.flightsData.updateOne({
    "_id": "my_id"
  }, 
  {$set: {"marker": "delete"}})
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
```
## Current data

**Command**
```json
db.flightsData.find()
```
**Output**
```json
[
  {
    _id: ObjectId('67472fc9b95dc4b9a70d8191'),
    departureAirport: 'IST',
    arrivalAirport: 'AYT'
  },
  {
    _id: 'my_id',
    departureAirport: 'SAW',
    arrivalAirport: 'AYT',
    marker: 'delete'
  }
]
```
## Updating Many Document
**Command**
```json
db.flightsData.updateMany({}, {$set: {"marker": "toBeDeleted"}})
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
```
## Current data

**Command**
```json
db.flightsData.find()
```
**Output**
```json
[
  {
    _id: ObjectId('67472fc9b95dc4b9a70d8191'),
    departureAirport: 'IST',
    arrivalAirport: 'AYT',
    marker: 'toBeDeleted'
  },
  {
    _id: 'my_id',
    departureAirport: 'SAW',
    arrivalAirport: 'AYT',
    marker: 'toBeDeleted'
  }
]
```
## Deleting Many Document
**Command**
```json
db.flightsData.deleteMany({"marker": "toBeDeleted"})
```
**Output**
```json
{ acknowledged: true, deletedCount: 2 }
```
## Current data

**Command**
```json
db.flightsData.find()
```
**Output**
```java
//No output at all...
```
## Inserting Many Document
**Command**
```json
db.flightsData.insertMany([
  {
    "departureAirport": "MUC",
    "arrivalAirport": "SFO",
    "aircraft": "Airbus A380",
    "distance": 12000,
    "intercontinental": true
  },
  {
    "departureAirport": "LHR",
    "arrivalAirport": "TXL",
    "aircraft": "Airbus A320",
    "distance": 950,
    "intercontinental": false
  }
])
```
**Output**
```json
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('674737e7b95dc4b9a70d8192'),
    '1': ObjectId('674737e7b95dc4b9a70d8193')
  }
}
```
## Current data

**Command**
```json
db.flightsData.find()
```
**Output**
```json
[
  {
    _id: ObjectId('674737e7b95dc4b9a70d8192'),
    departureAirport: 'MUC',
    arrivalAirport: 'SFO',
    aircraft: 'Airbus A380',
    distance: 12000,
    intercontinental: true
  },
  {
    _id: ObjectId('674737e7b95dc4b9a70d8193'),
    departureAirport: 'LHR',
    arrivalAirport: 'TXL',
    aircraft: 'Airbus A320',
    distance: 950,
    intercontinental: false
  }
]
```
## Finding Many Documents With Filtering
**Command**
```json
db.flightsData.find({"intercontinental": true})
```
**Output**
```json
[
  {
    _id: ObjectId('674737e7b95dc4b9a70d8192'),
    departureAirport: 'MUC',
    arrivalAirport: 'SFO',
    aircraft: 'Airbus A380',
    distance: 12000,
    intercontinental: true
  }
]
```
**Command**
```json
db.flightsData.find({"distance": {$gt: 900}})
```
**Output**
```json
[
  {
    _id: ObjectId('674737e7b95dc4b9a70d8192'),
    departureAirport: 'MUC',
    arrivalAirport: 'SFO',
    aircraft: 'Airbus A380',
    distance: 12000,
    intercontinental: true
  },
  {
    _id: ObjectId('674737e7b95dc4b9a70d8193'),
    departureAirport: 'LHR',
    arrivalAirport: 'TXL',
    aircraft: 'Airbus A320',
    distance: 950,
    intercontinental: false
  }
]
```
**Command**
```json
db.flightsData.find({"distance": {$gt: 1000}})
```
**Output**
```json
[
  {
    _id: ObjectId('674737e7b95dc4b9a70d8192'),
    departureAirport: 'MUC',
    arrivalAirport: 'SFO',
    aircraft: 'Airbus A380',
    distance: 12000,
    intercontinental: true
  }
]
```
## Finding One Document With Filtering
It filters the results and returns the very first document.

**Command**
```json
db.flightsData.findOne({"distance": {$gt: 900}})
```
**Output**
```json
{
  _id: ObjectId('674737e7b95dc4b9a70d8192'),
  departureAirport: 'MUC',
  arrivalAirport: 'SFO',
  aircraft: 'Airbus A380',
  distance: 12000,
  intercontinental: true
}
```