## Current data

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
    intercontinental: true
  },
  {
    _id: ObjectId('67476e43b95dc4b9a70d81bf'),
    departureAirport: 'LHR',
    arrivalAirport: 'TXL',
    aircraft: 'Airbus A320',
    distance: 950,
    intercontinental: false
  }
]
```

## Updating Documents witha Nested Document

**Command**
```json
db.flightsData.updateMany({}, 
{
  $set: {"status": {
    "description": "on-time",
    "lastUpdated": "1 hour ago"
  }}
})
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
    _id: ObjectId('67476e43b95dc4b9a70d81be'),
    departureAirport: 'MUC',
    arrivalAirport: 'SFO',
    aircraft: 'Airbus A380',
    distance: 12000,
    intercontinental: true,
    status: { description: 'on-time', lastUpdated: '1 hour ago' }
  },
  {
    _id: ObjectId('67476e43b95dc4b9a70d81bf'),
    departureAirport: 'LHR',
    arrivalAirport: 'TXL',
    aircraft: 'Airbus A320',
    distance: 950,
    intercontinental: false,
    status: { description: 'on-time', lastUpdated: '1 hour ago' }
  }
]
```
## Add One More Nested Document

**Command**
```json
db.flightsData.updateMany({}, 
{
  $set: {"status": {
    "description": "on-time",
    "lastUpdated": "1 hour ago",
    "details": {
      "responsible": "Max Payne"
    }
  }}
})
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