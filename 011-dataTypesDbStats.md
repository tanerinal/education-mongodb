## Different Data Types in One Document

**Command**
```json
use companyData
db.companies.insertOne({
  "name": "Frexh Apples Inc",
  "isStartup": true,
  "employees": 33,
  "fnding": 12345678901234567000,
  "details": {
    "ceo": "Mark Super"
  },
  "tags": [
    {
      "title": "super"
    },
    {
      "title": "perfect"
    }
  ],
  "foundingDate": new Date(),
  "insertedAt": new Timestamp()
})
```
**Output**
```json
{
  acknowledged: true,
  insertedId: ObjectId('674807feb95dc4b9a70d81c6')
}
```

## Current Data

**Command**
```json
db.companies.find()
```
**Output**
```json
[
  {
    _id: ObjectId('674807feb95dc4b9a70d81c6'),
    name: 'Frexh Apples Inc',
    isStartup: true,
    employees: 33,
    fnding: 12345678901234567000,
    details: { ceo: 'Mark Super' },
    tags: [ { title: 'super' }, { title: 'perfect' } ],
    foundingDate: ISODate('2024-11-28T06:04:46.871Z'),
    insertedAt: Timestamp({ t: 1732773886, i: 1 })
  }
]
```

## Learning Data Type of a Field

**Command**
```json
typeof db.companies.findOne({_id: ObjectId('674807feb95dc4b9a70d81c6')}).employees
```
**Output**
```json
number
```
## Retrieving Database Data Statistics

**Command**
```json
db.stats()
```
**Output**
```json
{
  db: 'companyData',
  collections: Long('1'),
  views: Long('0'),
  objects: Long('1'),
  avgObjSize: 231,
  dataSize: 231,
  storageSize: 20480,
  indexes: Long('1'),
  indexSize: 20480,
  totalSize: 40960,
  scaleFactor: Long('1'),
  fsUsedSize: 101126676480,
  fsTotalSize: 208439570432,
  ok: 1
}
```