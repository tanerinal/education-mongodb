## Alter the Schema Validator of posts Collection with Action Level of Warn
**Command**
```java
db.runCommand({
  collMod: 'posts',
  validator: {
    $jsonSchema: {
      bsonType: 'object',
      required: ['title', 'text', 'creator', 'comments'],
      properties: {
        title: {
          bsonType: 'string',
          description: 'must be a string and is required'
        },
        text: {
          bsonType: 'string',
          description: 'must be a string and is required'
        },
        creator: {
          bsonType: 'objectId',
          description: 'must be an objectid and is required'
        },
        comments: {
          bsonType: 'array',
          description: 'must be an array and is required',
          items: {
            bsonType: 'object',
            required: ['text', 'author'],
            properties: {
              text: {
                bsonType: 'string',
                description: 'must be a string and is required'
              },
              author: {
                bsonType: 'objectId',
                description: 'must be an objectid and is required'
              }
            }
          }
        }
      }
    }
  },
  validationAction: 'warn'  //When not given, the default is "error"
});
```
**Output**
```json
{ ok: 1 }
```

> It logs the warning into the system logs.

## Insert an Improper Post Document

**Command**
```json
db.posts.insertOne({
  "title": "My Second but improper Blog Post",
  "text": "here is  its text",
  "creator": ObjectId('67483099b95dc4b9a70d81cc'),
  "comments": [
    {
      "text": 12355,
      "author": ObjectId('67483099b95dc4b9a70d81cd')
    }
  ]
})
```
**Output**
```json
{
  acknowledged: true,
  insertedId: ObjectId('674845d5b95dc4b9a70d81d0')
}
```

## Check Whether the Improper Date Being Inserted or Not

**Command**
```json
db.posts.findOne({"title": "My Second but improper Blog Post"})
```
**Output**
```json
{
  _id: ObjectId('674845d5b95dc4b9a70d81d0'),
  title: 'My Second but improper Blog Post',
  text: 'here is  its text',
  creator: ObjectId('67483099b95dc4b9a70d81cc'),
  comments: [ { text: 12355, author: ObjectId('67483099b95dc4b9a70d81cd') } ]
}
```