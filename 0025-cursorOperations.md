## Getting Cursor and Checking if There is Any Item Can Be Fetched

**Command**
```json
use movieData
var movieCursor = db.movies.find()
movieCursor.count()   //Getting the size of the cursor
movieCursor.hasNext() //Checking if there is any item can be fetched.
```
**Output**
```json
240
true
```

## Iterate Over the Cursor and Doing Something with Each Item
**Command**
```json
movieCursor.forEach(doc => {if (doc.rating.average > 9) printjson(doc)})
```
**Output**
```json
{
  "_id": ObjectId("674879d3c6ec200ac032334d"),
  "id": 204,
  "url": "http://www.tvmaze.com/shows/204/stargate-sg-1",
  "name": "Stargate SG-1",
  "type": "Scripted",
  "language": "English",
  "genres": ["Action", "Adventure", "Science-Fiction"],
  "status": "Ended",
  "runtime": 60,
  "premiered": "1997-07-27",
  "officialSite": "http://stargate.mgm.com/view/series/1/index.html",
  "schedule": { "time": "20:00", "days": ["Friday"] },
  "rating": { "average": 9.3 },
  "weight": 93,
  "network": {
    "id": 16,
    "name": "Syfy",
    "country": {
      "name": "United States",
      "code": "US",
      "timezone": "America/New_York"
    }
  },
  "webChannel": null,
  "externals": { "tvrage": 5325, "thetvdb": 72449, "imdb": "tt0118480" },
  "image": {
    "medium": "http://static.tvmaze.com/uploads/images/medium_portrait/1/3027.jpg",
    "original": "http://static.tvmaze.com/uploads/images/original_untouched/1/3027.jpg"
  },
  "summary": "<p><b>Stargate SG-1</b> is a science fiction series based on the original film <i>Stargate</i>. It involves the team SG-1 going on various adventures to different alien worlds through Stargates. Throughout the series they encounter various alien threats and allies including but not limited to the Goa'uld and the Asgard.</p>",
  "updated": 1533412426,
  "_links": {
    "self": { "href": "http://api.tvmaze.com/shows/204" },
    "previousepisode": { "href": "http://api.tvmaze.com/episodes/13649" }
  }
},
{
  "_id": ObjectId("674879d3c6ec200ac0323354"),
  "id": 216,
  "url": "http://www.tvmaze.com/shows/216/rick-and-morty",
  "name": "Rick and Morty",
  "type": "Animation",
  "language": "English",
  "genres": ["Comedy", "Adventure", "Science-Fiction"],
  "status": "Running",
  "runtime": 30,
  "premiered": "2013-12-02",
  "officialSite": "http://www.adultswim.com/videos/rick-and-morty",
  "schedule": { "time": "23:30", "days": ["Sunday"] },
  "rating": { "average": 9.4 },
  "weight": 92,
  "network": {
    "id": 10,
    "name": "Adult Swim",
    "country": {
      "name": "United States",
      "code": "US",
      "timezone": "America/New_York"
    }
  },
  "webChannel": null,
  "externals": { "tvrage": 33381, "thetvdb": 275274, "imdb": "tt2861424" },
  "image": {
    "medium": "http://static.tvmaze.com/uploads/images/medium_portrait/1/3603.jpg",
    "original": "http://static.tvmaze.com/uploads/images/original_untouched/1/3603.jpg"
  },
  "summary": "<p>Rick is a mentally gifted, but sociopathic and alcoholic scientist and a grandfather to Morty; an awkward, impressionable, and somewhat spineless teenage boy. Rick moves into the family home of Morty, where he immediately becomes a bad influence.</p>",
  "updated": 1533638739,
  "_links": {
    "self": { "href": "http://api.tvmaze.com/shows/216" },
    "previousepisode": { "href": "http://api.tvmaze.com/episodes/1285113" }
  }
}
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