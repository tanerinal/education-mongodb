## Create a Blog Database and Insert Users

**Command**
```json
use blog
```
**Output**
```json
switched to db blog
```
### Insert User Data
**Command**
```json
db.users.insertMany([
  {
    "name": "John Doe",
    "age": 29,
    "city": "London"
  },
  {
    "name": "Jane Doe",
    "age": 40,
    "city": "New York City"
  }
])
```
**Output**
```json
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('67483099b95dc4b9a70d81cc'),
    '1': ObjectId('67483099b95dc4b9a70d81cd')
  }
}
```

### Create posts Collection with Schema
**Command**
```json
db.createCollection('posts', {
   "validator": {
  "bsonType": "object",
  "required": [
    "title",
    "text",
    "creator",
    "comments"
  ],
  "properties": {
    "title": {
      "bsonType": "string",
      "description": "must be a string and is required"
    },
    "text": {
      "bsonType": "string",
      "description": "must be a string and is required"
    },
    "creator": {
      "bsonType": "objectId",
      "description": "must be an objectid and is required"
    },
    "comments": {
      "bsonType": "array",
      "description": "must be an array and is required",
      "items": {
        "bsonType": "object",
        "required": [
          "text",
          "author"
        ],
        "properties": {
          "text": {
            "bsonType": "string",
            "description": "must be a string and is required"
          },
          "author": {
            "bsonType": "objectId",
            "description": "must be an objectid and is required"
          }
        }
      }
    }
  }}
});
```
**Output**
```json
{ ok: 1 }
```
### Insert a Proper Post Document

**Command**
```json
db.posts.insertOne({
  "title": "My First Blog Post",
  "text": "here is  its text",
  "creator": ObjectId('67483099b95dc4b9a70d81cc'),
  "comments": [
    {
      "text": "well done",
      "author": ObjectId('67483099b95dc4b9a70d81cd')
    }
  ]
})
```
**Output**
```json
{
  acknowledged: true,
  insertedId: ObjectId('674840e6b95dc4b9a70d81ce')
}
```
### Insert a Improper Post Document

**Command**
```json
db.posts.insertOne({
  "title": "My Second but improper Blog Post",
  "text": "here is  its text",
  "creator": ObjectId('67483099b95dc4b9a70d81cc'),
  "comments": [
    {
      "text": 12355,   //Should be string.
      "author": ObjectId('67483099b95dc4b9a70d81cd')
    }
  ]
})
```
**Output**
```json
Uncaught:
MongoServerError: Document failed validation
Additional information: {
  failingDocumentId: ObjectId('674840f5b95dc4b9a70d81cf'),
  details: {
    operatorName: '$jsonSchema',
    schemaRulesNotSatisfied: [
      {
        operatorName: 'properties',
        propertiesNotSatisfied: [
          {
            propertyName: 'comments',
            description: 'must be an array and is required',
            details: [
              {
                operatorName: 'items',
                reason: 'At least one item did not match the sub-schema',
                itemIndex: 0,
                details: [
                  {
                    operatorName: 'properties',
                    propertiesNotSatisfied: [
                      {
                        propertyName: 'text',
                        description: 'must be a string and is required',
                        details: [
                          {
                            operatorName: 'bsonType',
                            specifiedAs: { bsonType: 'string' },
                            reason: 'type did not match',
                            consideredValue: 1234,
                            consideredType: 'int'
                          }
                        ]
                      }
                    ]
                  }
                ]
              }
            ]
          }
        ]
      }
    ]
  }
}
```