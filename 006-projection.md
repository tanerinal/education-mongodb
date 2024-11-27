## Current data

**Command**
```json
db.passangers.find()
```
**Output**
```json
[
  {
    _id: ObjectId('67474343b95dc4b9a70d81a9'),
    name: 'Max Schwarzmueller',
    age: 29
  },
  {
    _id: ObjectId('67474343b95dc4b9a70d81aa'),
    name: 'Manu Lorenz',
    age: 30
  },
  {
    _id: ObjectId('67474343b95dc4b9a70d81ab'),
    name: 'Chris Hayton',
    age: 35
  },
  {
    _id: ObjectId('67474343b95dc4b9a70d81ac'),
    name: 'Sandeep Kumar',
    age: 28
  },
  ...
  ...
  ...
]
```

## Projection
It is the declaration of which fields of the document we need.

**Command**
```json
db.passangers.find({age: 29}, {name: 1})
```
**Output**
```json
[
  {
    _id: ObjectId('67474343b95dc4b9a70d81a9'),
    name: 'Max Schwarzmueller'
  },
  { _id: ObjectId('67474343b95dc4b9a70d81b1'), 
    name: 'Elisabeth Mayr' }
]
```
If we don't need any field, here **_id**;

**Command**
```json
db.passangers.find({age: 29}, {name: 1, _id: 0})
```
**Output**
```json
[ 
  { name: 'Max Schwarzmueller' }, 
  { name: 'Elisabeth Mayr' } 
]
```