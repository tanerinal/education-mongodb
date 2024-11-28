> For this practice, you should download and install [MongoDB Database Tools](https://www.mongodb.com/try/download/database-tools)

## Importing a Json File as a Collection

**Command**
![Mongo Import](resources\images\mongoimport.png)

### Current Data

**Command**
```json
use movieData
db.movies.find()
```
**Output**
```json
[
  {
    _id: ObjectId('674879d3c6ec200ac032328b'),
    id: 3,
    url: 'http://www.tvmaze.com/shows/3/bitten',
    name: 'Bitten',
    type: 'Scripted',
    language: 'English',
    genres: [ 'Drama', 'Horror', 'Romance' ],
    status: 'Ended',
    runtime: 60,
    premiered: '2014-01-11',
    officialSite: 'http://bitten.space.ca/',
    schedule: { time: '22:00', days: [ 'Friday' ] },
    rating: { average: 7.6 },
    weight: 75,
    network: {
      id: 7,
      name: 'Space',
      country: { name: 'Canada', code: 'CA', timezone: 'America/Halifax' }
    },
    webChannel: null,
    externals: { tvrage: 34965, thetvdb: 269550, imdb: 'tt2365946' },
    image: {
      medium: 'http://static.tvmaze.com/uploads/images/medium_portrait/0/15.jpg',
      original: 'http://static.tvmaze.com/uploads/images/original_untouched/0/15.jpg'
    },
    summary: `<p>Based on the critically acclaimed series of novels from Kelley Armstrong. Set in Toronto and upper New York State, <b>Bitten</b> follows the adventures of 28-year-old Elena Michaels, the world's only female werewolf. An orphan, Elena thought she finally found her "happily ever after" with her new love Clayton, until her life changed forever. With one small bite, the normal life she craved was taken away and she was left to survive life with the Pack.</p>`,
    updated: 1534079818,
    _links: {
      self: { href: 'http://api.tvmaze.com/shows/3' },
      previousepisode: { href: 'http://api.tvmaze.com/episodes/631862' }
    }
  },
  {
    _id: ObjectId('674879d3c6ec200ac032328c'),
    id: 1,
    url: 'http://www.tvmaze.com/shows/1/under-the-dome',
    name: 'Under the Dome',
    type: 'Scripted',
    language: 'English',
    genres: [ 'Drama', 'Science-Fiction', 'Thriller' ],
    status: 'Ended',
    runtime: 60,
    premiered: '2013-06-24',
    officialSite: 'http://www.cbs.com/shows/under-the-dome/',
    schedule: { time: '22:00', days: [ 'Thursday' ] },
    rating: { average: 6.5 },
    weight: 91,
    network: {
      id: 2,
      name: 'CBS',
      country: {
        name: 'United States',
        code: 'US',
        timezone: 'America/New_York'
      }
    },
    webChannel: null,
    externals: { tvrage: 25988, thetvdb: 264492, imdb: 'tt1553656' },
    image: {
      medium: 'http://static.tvmaze.com/uploads/images/medium_portrait/0/1.jpg',
      original: 'http://static.tvmaze.com/uploads/images/original_untouched/0/1.jpg'
    },
    summary: "<p><b>Under the Dome</b> is the story of a small town that is suddenly and inexplicably sealed off from the rest of the world by an enormous transparent dome. The town's inhabitants must deal with surviving the post-apocalyptic conditions while searching for answers about the dome, where it came from and if and when it will go away.</p>",
    updated: 1529612668,
    _links: {
      self: { href: 'http://api.tvmaze.com/shows/1' },
      previousepisode: { href: 'http://api.tvmaze.com/episodes/185054' }
    }
  },
  ...
  ...
  ..
]
```