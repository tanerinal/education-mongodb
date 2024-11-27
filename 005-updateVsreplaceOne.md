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

## Using UpdateOne and Update Command
Here is the normal updateOne command;

**Command**
```json
db.flightsData.updateOne({
    _id: ObjectId('674737e7b95dc4b9a70d8192')
  }, 
  {$set:{"delayed": true}})
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
    _id: ObjectId('674737e7b95dc4b9a70d8192'),
    departureAirport: 'MUC',
    arrivalAirport: 'SFO',
    aircraft: 'Airbus A380',
    distance: 12000,
    intercontinental: true,
    delayed: true
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
And now, the update command;

**Command**
```json
db.flightsData.update({"distance": {$gt: 900}}, 
  {$set: {"delayed": false}})
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
    _id: ObjectId('674737e7b95dc4b9a70d8192'),
    departureAirport: 'MUC',
    arrivalAirport: 'SFO',
    aircraft: 'Airbus A380',
    distance: 1050,
    intercontinental: true,
    delayed: false
  },
  {
    _id: ObjectId('674737e7b95dc4b9a70d8193'),
    departureAirport: 'LHR',
    arrivalAirport: 'TXL',
    aircraft: 'Airbus A320',
    distance: 950,
    intercontinental: false,
    delayed: false
  }
]
```
## Replacing Content of a Document
**Command**
```json
 db.flightsData.replaceOne(
 { "delayed": false }, 
 { "newField": "newOneValue" })
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
    _id: ObjectId('674737e7b95dc4b9a70d8192'),
    newField: 'newOneValue'
  },
  {
    _id: ObjectId('674737e7b95dc4b9a70d8193'),
    departureAirport: 'LHR',
    arrivalAirport: 'TXL',
    aircraft: 'Airbus A320',
    distance: 950,
    intercontinental: false,
    delayed: false
  }
]
```