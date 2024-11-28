## Create Related Data of Authors and Books

**Command**
```json
use bookStore
```
**Output**
```json
switched to db bookStore
```
### Insert Author Data
**Command**
```json
db.authors.insertMany([
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
    '0': ObjectId('67481bebb95dc4b9a70d81c9'),
    '1': ObjectId('67481bebb95dc4b9a70d81ca'),
    '2': ObjectId('67481bebb95dc4b9a70d81cb')
  }
}
```

### Insert Books Data
**Command**
```json
db.books.insertMany([
  {
    "title": "Book 1",
    "isbn": 123,
    "authors": [
      ObjectId('67481b07b95dc4b9a70d81c7')
    ]
  },
  {
    "title": "Book 2",
    "isbn": 456,
    "authors": [
      ObjectId('67481b07b95dc4b9a70d81c8')
    ]
  },
  {
    "title": "Book 12",
    "isbn": 891,
    "authors": [
      ObjectId('67481b07b95dc4b9a70d81c7'),
      ObjectId('67481b07b95dc4b9a70d81c8')
    ]
  }
])
```
**Output**
```json
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('67481bebb95dc4b9a70d81c9'),
    '1': ObjectId('67481bebb95dc4b9a70d81ca'),
    '2': ObjectId('67481bebb95dc4b9a70d81cb')
  }
}
```
### Current Authors Data

**Command**
```json
db.authors.find()
```
**Output**
```json
[
  {
    _id: ObjectId('67481b07b95dc4b9a70d81c7'),
    name: 'John Doe',
    age: 29,
    city: 'London'
  },
  {
    _id: ObjectId('67481b07b95dc4b9a70d81c8'),
    name: 'Jane Doe',
    age: 40,
    city: 'New York City'
  }
]
```
### Current Books Data

**Command**
```json
db.books.find()
```
**Output**
```json
[
  {
    _id: ObjectId('67481bebb95dc4b9a70d81c9'),
    title: 'Book 1',
    isbn: 123,
    authors: [ ObjectId('67481b07b95dc4b9a70d81c7') ]
  },
  {
    _id: ObjectId('67481bebb95dc4b9a70d81ca'),
    title: 'Book 2',
    isbn: 456,
    authors: [ ObjectId('67481b07b95dc4b9a70d81c8') ]
  },
  {
    _id: ObjectId('67481bebb95dc4b9a70d81cb'),
    title: 'Book 12',
    isbn: 891,
    authors: [
      ObjectId('67481b07b95dc4b9a70d81c7'),
      ObjectId('67481b07b95dc4b9a70d81c8')
    ]
  }
]
```
## Generate a Lookup with References

**Command**
```json
db.books.aggregate([{$lookup:{"from": "authors", "localField": "authors", "foreignField": "_id", "as": "writers"}}])
```
**Output**
```json
[
  {
    _id: ObjectId('67481bebb95dc4b9a70d81c9'),
    title: 'Book 1',
    isbn: 123,
    authors: [ ObjectId('67481b07b95dc4b9a70d81c7') ],
    writers: [
      {
        _id: ObjectId('67481b07b95dc4b9a70d81c7'),
        name: 'John Doe',
        age: 29,
        city: 'London'
      }
    ]
  },
  {
    _id: ObjectId('67481bebb95dc4b9a70d81ca'),
    title: 'Book 2',
    isbn: 456,
    authors: [ ObjectId('67481b07b95dc4b9a70d81c8') ],
    writers: [
      {
        _id: ObjectId('67481b07b95dc4b9a70d81c8'),
        name: 'Jane Doe',
        age: 40,
        city: 'New York City'
      }
    ]
  },
  {
    _id: ObjectId('67481bebb95dc4b9a70d81cb'),
    title: 'Book 12',
    isbn: 891,
    authors: [
      ObjectId('67481b07b95dc4b9a70d81c7'),
      ObjectId('67481b07b95dc4b9a70d81c8')
    ],
    writers: [
      {
        _id: ObjectId('67481b07b95dc4b9a70d81c7'),
        name: 'John Doe',
        age: 29,
        city: 'London'
      },
      {
        _id: ObjectId('67481b07b95dc4b9a70d81c8'),
        name: 'Jane Doe',
        age: 40,
        city: 'New York City'
      }
    ]
  }
]
```