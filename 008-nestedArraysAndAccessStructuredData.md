## Current data

**Command**
```json
db.passangers.find()
```
**Output**
```json
[
  ..
  ...
    {
    _id: ObjectId('67474343b95dc4b9a70d81ba'),
    name: 'Armin Glutch',
    age: 35
  },
  {
    _id: ObjectId('67474343b95dc4b9a70d81bb'),
    name: 'Klaus Arber',
    age: 53
  },
  {
    _id: ObjectId('67474343b95dc4b9a70d81bc'),
    name: 'Albert Twostone',
    age: 68
  }
]
```

## Updating a Document with a Nested Array

**Command**
```json
db.passangers.updateOne({"name": "Albert Twostone"}, 
{
  $set: {"hobbies": ["sports", "cookies"]}
})
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
## Filtering a Collection with Structured Data Access

Our current data is;

**Command**
```json
db.flightsData.find()
```
**Output**
```json
[
  {
    _id: ObjectId('67476e43b95dc4b9a70d81be'),
    departureAirport: 'MUC',
    arrivalAirport: 'SFO',
    aircraft: 'Airbus A380',
    distance: 12000,
    intercontinental: true,
    status: {
      description: 'on-time',
      lastUpdated: '1 hour ago',
      details: { responsible: 'Max Payne' }
    }
  },
  {
    _id: ObjectId('67476e43b95dc4b9a70d81bf'),
    departureAirport: 'LHR',
    arrivalAirport: 'TXL',
    aircraft: 'Airbus A320',
    distance: 950,
    intercontinental: false,
    status: {
      description: 'on-time',
      lastUpdated: '1 hour ago',
      details: { responsible: 'Max Payne' }
    }
  }
]
```

**Command**
```json
use flights
db.flightsData.findOne({
  "departureAirport": "LHR", 
  "status.description": "on-time"})
```
**Output**
```json
{
  _id: ObjectId('67476e43b95dc4b9a70d81bf'),
  departureAirport: 'LHR',
  arrivalAirport: 'TXL',
  aircraft: 'Airbus A320',
  distance: 950,
  intercontinental: false,
  status: {
    description: 'on-time',
    lastUpdated: '1 hour ago',
    details: { responsible: 'Max Payne' }
  }
}
```