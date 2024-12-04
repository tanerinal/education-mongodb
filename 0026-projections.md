## Use Projections to Limit The Output Fields

**Command**
```json
use movieData
db.movies.find({}, {"name": 1, "genres": 1, "runtime": 1, "rating.average": 1}).limit(2)
```
**Output**
```json
[
  {
    "_id": "ObjectId('674879d3c6ec200ac032328b')",
    "name": "Bitten",
    "genres": ["Drama", "Horror", "Romance"],
    "runtime": 60,
    "rating": { "average": 7.6 }
  },
  {
    "_id": "ObjectId('674879d3c6ec200ac032328c')",
    "name": "Under the Dome",
    "genres": ["Drama", "Science-Fiction", "Thriller"],
    "runtime": 60,
    "rating": { "average": 6.5 }
  }
]
```
> *_id* field always shown unless deliberately opted out.

## Opting-out A Field
**Command**
```json
db.movies.find({}, {"name": 1, "genres": 1, "runtime": 1, "rating.average": 1, "_id": 0}).limit(2)
```
**Output**
```json
[
  {
    "name": "Bitten",
    "genres": ["Drama", "Horror", "Romance"],
    "runtime": 60,
    "rating": { "average": 7.6 }
  },
  {
    "name": "Under the Dome",
    "genres": ["Drama", "Science-Fiction", "Thriller"],
    "runtime": 60,
    "rating": { "average": 6.5 }
  }
]
```

## Sorting the Cursor Results

**Command**
```json
db.movies.find({$or: [{"rating.average": {$eq: 6.3}}, {"rating.average": {$eq: 6.4}}]}).sort({"rating.average": 1, "runtime": -1})
```
>Ascending with rating.average then descending wit runtime. (Results refined due to length.)

**Output**
```json
[
  {
    "_id": "ObjectId('674879d3c6ec200ac0323357')",
    "runtime": 60,
    "rating": { "average": 6.3 }
  },
  {
    "_id": "ObjectId('674879d3c6ec200ac032330a')",
    "runtime": 30,
    "rating": { "average": 6.3 }
  },
  {
    "_id": "ObjectId('674879d3c6ec200ac03232ad')",
    "runtime": 60,
    "rating": { "average": 6.4 }
  },
  {
    "_id": "ObjectId('674879d3c6ec200ac0323369')",
    "runtime": 60,
    "rating": { "average": 6.4 }
  },
  {
    "_id": "ObjectId('674879d3c6ec200ac032330c')",
    "runtime": 30,
    "rating": { "average": 6.4 }
  },
  {
    "_id": "ObjectId('674879d3c6ec200ac0323370')",
    "runtime": 30,
    "rating": { "average": 6.4 }
  }
]

```

## Skipping and Limitind the Results of a Cursor
**Command**

```json
db.userData.find().skip(20).limit(3)
```
> Skips 20 item from start then shows 3 documents

**Output**
```json
[
  {
    "_id": "ObjectId('674879d3c6ec200ac032329f')",
    "runtime": 60,
    "rating": { "average": 6.7 }
  },
  {
    "_id": "ObjectId('674879d3c6ec200ac03232a0')",
    "runtime": 30,
    "rating": { "average": 8.3 }
  },
  {
    "_id": "ObjectId('674879d3c6ec200ac03232a1')",
    "runtime": 50,
    "rating": { "average": 8.1 }
  }
]
```