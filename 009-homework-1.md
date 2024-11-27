## Task-1: Insert 3 patient records with at least 1 history record per patient

**Command**
```json
use hospital
db.patients.insertMany([
    {
      "firstName": "John",
      "lastName": "Doe",
      "age": 28,
      "history": [
        {
          "disease": "Cold",
          "treatment": "Rest and hydration"
        },
        {
          "disease": "Migraine",
          "treatment": "Painkillers"
        }
      ]
    },
    {
      "firstName": "Jane",
      "lastName": "Smith",
      "age": 35,
      "history": [
        {
          "disease": "Allergy",
          "treatment": "Antihistamines"
        },
        {
          "disease": "Sprained Ankle",
          "treatment": "Physical therapy"
        }
      ]
    },
    {
      "firstName": "Ali",
      "lastName": "Yilmaz",
      "age": 40,
      "history": [
        {
          "disease": "Hypertension",
          "treatment": "Medication and diet"
        },
        {
          "disease": "Back Pain",
          "treatment": "Exercise and physiotherapy"
        }
      ]
    }
  ])
```
**Output**
```json
switched to db hospital

{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('67478d68b95dc4b9a70d81c3'),
    '1': ObjectId('67478d68b95dc4b9a70d81c4'),
    '2': ObjectId('67478d68b95dc4b9a70d81c5')
  }
}
```

## Current Data
**Command**

```json
db.patients.find()
```
**Output**
```json
[
  {
    _id: ObjectId('67478d68b95dc4b9a70d81c3'),
    firstName: 'John',
    lastName: 'Doe',
    age: 28,
    history: [
      { disease: 'Cold', treatment: 'Rest and hydration' },
      { disease: 'Migraine', treatment: 'Painkillers' }
    ]
  },
  {
    _id: ObjectId('67478d68b95dc4b9a70d81c4'),
    firstName: 'Jane',
    lastName: 'Smith',
    age: 35,
    history: [
      { disease: 'Allergy', treatment: 'Antihistamines' },
      { disease: 'Sprained Ankle', treatment: 'Physical therapy' }
    ]
  },
  {
    _id: ObjectId('67478d68b95dc4b9a70d81c5'),
    firstName: 'Ali',
    lastName: 'Yilmaz',
    age: 40,
    history: [
      { disease: 'Hypertension', treatment: 'Medication and diet' },
      { disease: 'Back Pain', treatment: 'Exercise and physiotherapy' }
    ]
  }
]
```

## Task-2: Update patient data of 1 patient with new age, name and history entry
**Command**
```json
db.patients.updateOne(
  { _id: ObjectId('67478d68b95dc4b9a70d81c5') },
  [
    {
      $set: {
        age: 45,
        name: { $concat: ["$firstName", " ", "$lastName"] }
      }
    }
  ]
)

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
**Command**
```json
db.patients.updateOne(
  { _id: ObjectId('67478d68b95dc4b9a70d81c5') },
  {$push: {"history":  {
    "disease": "Diabetes",
    "treatment": "Insulin therapy and dietary changes"
    }
  }}
)


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

## Current Data
**Command**

```json
db.patients.find({"_id": ObjectId('67478d68b95dc4b9a70d81c5')})
```
**Output**
```json
[
  {
    _id: ObjectId('67478d68b95dc4b9a70d81c5'),
    firstName: 'Ali',
    lastName: 'Yilmaz',
    age: 45,
    history: [
      { disease: 'Hypertension', treatment: 'Medication and diet' },
      { disease: 'Back Pain', treatment: 'Exercise and physiotherapy' },
      {
        disease: 'Diabetes',
        treatment: 'Insulin therapy and dietary changes'
      }
    ],
    name: 'Ali Yilmaz'
  }
]
```
## Task-3: Find all patients who are older than age 30
**Command**

```json
db.patients.find({"age": {$gt: 30}})
```
**Output**
```json
[
  {
    _id: ObjectId('67478d68b95dc4b9a70d81c4'),
    firstName: 'Jane',
    lastName: 'Smith',
    age: 35,
    history: [
      { disease: 'Allergy', treatment: 'Antihistamines' },
      { disease: 'Sprained Ankle', treatment: 'Physical therapy' }
    ]
  },
  {
    _id: ObjectId('67478d68b95dc4b9a70d81c5'),
    firstName: 'Ali',
    lastName: 'Yilmaz',
    age: 45,
    history: [
      { disease: 'Hypertension', treatment: 'Medication and diet' },
      { disease: 'Back Pain', treatment: 'Exercise and physiotherapy' },
      {
        disease: 'Diabetes',
        treatment: 'Insulin therapy and dietary changes'
      }
    ],
    name: 'Ali Yilmaz'
  }
]
```
## Task-4: Find all patients who has a cold as a disease
**Command**

```json
db.patients.deleteMany({"history.disease": "Cold"})
```
**Output**
```json
{ acknowledged: true, deletedCount: 1 }
```
## Final Data
**Command**
```json
db.patients.find()
```
**Output**
```json
[
  {
    _id: ObjectId('67478d68b95dc4b9a70d81c4'),
    firstName: 'Jane',
    lastName: 'Smith',
    age: 35,
    history: [
      { disease: 'Allergy', treatment: 'Antihistamines' },
      { disease: 'Sprained Ankle', treatment: 'Physical therapy' }
    ]
  },
  {
    _id: ObjectId('67478d68b95dc4b9a70d81c5'),
    firstName: 'Ali',
    lastName: 'Yilmaz',
    age: 45,
    history: [
      { disease: 'Hypertension', treatment: 'Medication and diet' },
      { disease: 'Back Pain', treatment: 'Exercise and physiotherapy' },
      {
        disease: 'Diabetes',
        treatment: 'Insulin therapy and dietary changes'
      }
    ],
    name: 'Ali Yilmaz'
  }
]
```