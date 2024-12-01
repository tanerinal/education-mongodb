## Finding a Document with Searchind Text with regex

**Command**
```json
use movieData
db.movies.findOne({"summary": {$regex: /musical/}})
```
**Output**
```json
{
  "_id": ObjectId('674879d3c6ec200ac032328d'),
  "id": 8,
  "url": "http://www.tvmaze.com/shows/8/glee",
  "name": "Glee",
  "type": "Scripted",
  "language": "English",
  "genres": ["Drama", "Music", "Romance"],
  "status": "Ended",
  "runtime": 60,
  "premiered": "2009-05-19",
  "officialSite": "http://www.fox.com/glee",
  "schedule": { "time": "21:00", "days": ["Tuesday"] },
  "rating": { "average": 6.7 },
  "weight": 71,
  "network": {
    "id": 4,
    "name": "FOX",
    "country": { "name": "United States", "code": "US", "timezone": "America/New_York" }
  },
  "webChannel": null,
  "externals": { "tvrage": 21704, "thetvdb": 83610, "imdb": "tt1327801" },
  "image": {
    "medium": "http://static.tvmaze.com/uploads/images/medium_portrait/0/73.jpg",
    "original": "http://static.tvmaze.com/uploads/images/original_untouched/0/73.jpg"
  },
  "summary": "<p><b>Glee </b>is a musical comedy about a group of ambitious and talented young adults in search of strength, acceptance and, ultimately, their voice.</p>",
  "updated": 1536145055,
  "_links": {
    "self": { "href": "http://api.tvmaze.com/shows/8" },
    "previousepisode": { "href": "http://api.tvmaze.com/episodes/142185" }
  }
}

```

## Selecting Documents with Expressions and Conditions

### Current Data

**Command**
```json
use financialData
db.sales.find()
```
**Output**
```json
[
  {
    "_id": ObjectId('674c7d0e1d8fa081900d8190'),
    "volume": 100,
    "target": 120
  },
  {
    "_id": ObjectId('674c7d0e1d8fa081900d8191'),
    "volume": 89,
    "target": 80
  },
  {
    "_id": ObjectId('674c7d0e1d8fa081900d8192'),
    "volume": 200,
    "target": 177
  }
]
```
### Searching Documents with Expressions

**Command**
```json
db.sales.find({
    $expr: {
        $gt: ["$volume", "$target"]
    }
})
```
**Output**
```json
[
  {
    "_id": ObjectId('674c7d0e1d8fa081900d8191'),
    "volume": 89,
    "target": 80
  },
  {
    "_id": ObjectId('674c7d0e1d8fa081900d8192'),
    "volume": 200,
    "target": 177
  }
]
```