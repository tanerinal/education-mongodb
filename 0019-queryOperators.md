## Selecting a record having 60 of runtime.

**Command**
```json
use movieData
db.movies.findOne({"runtime": 60})
//or
db.movies.findOne({"runtime": {$eq: 60}})
```
**Output**
```json
switched to db social
{
  "_id": "674879d3c6ec200ac032328b",
  "id": 3,
  "url": "http://www.tvmaze.com/shows/3/bitten",
  "name": "Bitten",
  "type": "Scripted",
  "language": "English",
  "genres": ["Drama", "Horror", "Romance"],
  "status": "Ended",
  "runtime": 60,
  "premiered": "2014-01-11",
  "officialSite": "http://bitten.space.ca/",
  "schedule": {
    "time": "22:00",
    "days": ["Friday"]
  },
  "rating": {
    "average": 7.6
  },
  "weight": 75,
  "network": {
    "id": 7,
    "name": "Space",
    "country": {
      "name": "Canada",
      "code": "CA",
      "timezone": "America/Halifax"
    }
  },
  "webChannel": null,
  "externals": {
    "tvrage": 34965,
    "thetvdb": 269550,
    "imdb": "tt2365946"
  },
  "image": {
    "medium": "http://static.tvmaze.com/uploads/images/medium_portrait/0/15.jpg",
    "original": "http://static.tvmaze.com/uploads/images/original_untouched/0/15.jpg"
  },
  "summary": "<p>Based on the critically acclaimed series of novels from Kelley Armstrong. Set in Toronto and upper New York State, <b>Bitten</b> follows the adventures of 28-year-old Elena Michaels, the world's only female werewolf. An orphan, Elena thought she finally found her \"happily ever after\" with her new love Clayton, until her life changed forever. With one small bite, the normal life she craved was taken away and she was left to survive life with the Pack.</p>",
  "updated": 1534079818,
  "_links": {
    "self": {
      "href": "http://api.tvmaze.com/shows/3"
    },
    "previousepisode": {
      "href": "http://api.tvmaze.com/episodes/631862"
    }
  }
}

  ```

### Selecting a Document with Runtime Less Than or Equal to 42

**Command**
```json
db.movies.findOne({"runtime": {$lte: 42}})
```
**Output**
```json
{
  "_id": "674879d3c6ec200ac03232a0",
  "id": 25,
  "url": "http://www.tvmaze.com/shows/25/hellsing",
  "name": "Hellsing",
  "type": "Animation",
  "language": "Japanese",
  "genres": ["Anime", "Horror", "Supernatural"],
  "status": "Ended",
  "runtime": 30,
  "premiered": "2001-10-10",
  "officialSite": null,
  "schedule": {
    "time": "",
    "days": ["Wednesday"]
  },
  "rating": {
    "average": 8.3
  },
  "weight": 22,
  "network": {
    "id": 131,
    "name": "Fuji TV",
    "country": {
      "name": "Japan",
      "code": "JP",
      "timezone": "Asia/Tokyo"
    }
  },
  "webChannel": null,
  "externals": {
    "tvrage": 9139,
    "thetvdb": 71278,
    "imdb": "tt0325547"
  },
  "image": {
    "medium": "http://static.tvmaze.com/uploads/images/medium_portrait/0/247.jpg",
    "original": "http://static.tvmaze.com/uploads/images/original_untouched/0/247.jpg"
  },
  "summary": "<p><b>Hellsing</b> is a 13-part anime based on the manga of the same name. The plot is significantly different to that of the manga although the characters are the same. The show mainly focuses on the Hellsing institute that houses the anti-hero named Alucard who swore loyalty to the Hellsing family many years before. Alucard, being the first ever vampire, takes on a new apprentice named Seras.</p>",
  "updated": 1504676730,
  "_links": {
    "self": {
      "href": "http://api.tvmaze.com/shows/25"
    },
    "previousepisode": {
      "href": "http://api.tvmaze.com/episodes/398491"
    }
  }
}

```

### Selecting a Document with Runtime Greater Than 60

**Command**
```json
db.movies.findOne({"runtime": {$gt: 60}})
```
**Output**
```json
{
  "_id": "674879d3c6ec200ac03232ca",
  "id": 70,
  "url": "http://www.tvmaze.com/shows/70/the-voice",
  "name": "The Voice",
  "type": "Reality",
  "language": "English",
  "genres": ["Family", "Music"],
  "status": "Running",
  "runtime": 120,
  "premiered": "2011-04-26",
  "officialSite": "http://www.nbc.com/the-voice",
  "schedule": {
    "time": "20:00",
    "days": ["Monday", "Tuesday"]
  },
  "rating": {
    "average": 7.3
  },
  "weight": 90,
  "network": {
    "id": 1,
    "name": "NBC",
    "country": {
      "name": "United States",
      "code": "US",
      "timezone": "America/New_York"
    }
  },
  "webChannel": null,
  "externals": {
    "tvrage": 27447,
    "thetvdb": 247824,
    "imdb": "tt1839337"
  },
  "image": {
    "medium": "http://static.tvmaze.com/uploads/images/medium_portrait/146/365331.jpg",
    "original": "http://static.tvmaze.com/uploads/images/original_untouched/146/365331.jpg"
  },
  "summary": "<p><b>The Voice</b> is a reality singing competition show where the idea is to find new singing talent via a series of auditions.</p>",
  "updated": 1536584006,
  "_links": {
    "self": {
      "href": "http://api.tvmaze.com/shows/70"
    },
    "previousepisode": {
      "href": "http://api.tvmaze.com/episodes/1454416"
    },
    "nextepisode": {
      "href": "http://api.tvmaze.com/episodes/1482230"
    }
  }
}

```
### Selecting a Document with a Field of Embedded Document

**Command**
```json
db.movies.findOne({"rating.average": {$gt: 7}})
```
**Output**
```json
{
  "_id": "674879d3c6ec200ac032328b",
  "id": 3,
  "url": "http://www.tvmaze.com/shows/3/bitten",
  "name": "Bitten",
  "type": "Scripted",
  "language": "English",
  "genres": ["Drama", "Horror", "Romance"],
  "status": "Ended",
  "runtime": 60,
  "premiered": "2014-01-11",
  "officialSite": "http://bitten.space.ca/",
  "schedule": {
    "time": "22:00",
    "days": ["Friday"]
  },
  "rating": {
    "average": 7.6
  },
  "weight": 75,
  "network": {
    "id": 7,
    "name": "Space",
    "country": {
      "name": "Canada",
      "code": "CA",
      "timezone": "America/Halifax"
    }
  },
  "webChannel": null,
  "externals": {
    "tvrage": 34965,
    "thetvdb": 269550,
    "imdb": "tt2365946"
  },
  "image": {
    "medium": "http://static.tvmaze.com/uploads/images/medium_portrait/0/15.jpg",
    "original": "http://static.tvmaze.com/uploads/images/original_untouched/0/15.jpg"
  },
  "summary": "<p>Based on the critically acclaimed series of novels from Kelley Armstrong. Set in Toronto and upper New York State, <b>Bitten</b> follows the adventures of 28-year-old Elena Michaels, the world's only female werewolf. An orphan, Elena thought she finally found her \"happily ever after\" with her new love Clayton, until her life changed forever. With one small bite, the normal life she craved was taken away and she was left to survive life with the Pack.</p>",
  "updated": 1534079818,
  "_links": {
    "self": {
      "href": "http://api.tvmaze.com/shows/3"
    },
    "previousepisode": {
      "href": "http://api.tvmaze.com/episodes/631862"
    }
  }
}
```
### Selecting a Document with an Item of an Array

**Command**
```json
db.movies.findOne({"genres": "Drama"})
```
**Output**
```json
{
  "_id": "674879d3c6ec200ac032328b",
  "id": 3,
  "url": "http://www.tvmaze.com/shows/3/bitten",
  "name": "Bitten",
  "type": "Scripted",
  "language": "English",
  "genres": ["Drama", "Horror", "Romance"],
  "status": "Ended",
  "runtime": 60,
  "premiered": "2014-01-11",
  "officialSite": "http://bitten.space.ca/",
  "schedule": {
    "time": "22:00",
    "days": ["Friday"]
  },
  "rating": {
    "average": 7.6
  },
  "weight": 75,
  "network": {
    "id": 7,
    "name": "Space",
    "country": {
      "name": "Canada",
      "code": "CA",
      "timezone": "America/Halifax"
    }
  },
  "webChannel": null,
  "externals": {
    "tvrage": 34965,
    "thetvdb": 269550,
    "imdb": "tt2365946"
  },
  "image": {
    "medium": "http://static.tvmaze.com/uploads/images/medium_portrait/0/15.jpg",
    "original": "http://static.tvmaze.com/uploads/images/original_untouched/0/15.jpg"
  },
  "summary": "<p>Based on the critically acclaimed series of novels from Kelley Armstrong. Set in Toronto and upper New York State, <b>Bitten</b> follows the adventures of 28-year-old Elena Michaels, the world's only female werewolf. An orphan, Elena thought she finally found her \"happily ever after\" with her new love Clayton, until her life changed forever. With one small bite, the normal life she craved was taken away and she was left to survive life with the Pack.</p>",
  "updated": 1534079818,
  "_links": {
    "self": {
      "href": "http://api.tvmaze.com/shows/3"
    },
    "previousepisode": {
      "href": "http://api.tvmaze.com/episodes/631862"
    }
  }
}
```
### Selecting a Document with Exact Value of an Array

**Command**
```json
db.movies.findOne({"genres": ["Drama"]})
```
**Output**
```json
{
  "_id": "674879d3c6ec200ac03232be",
  "id": 48,
  "url": "http://www.tvmaze.com/shows/48/madam-secretary",
  "name": "Madam Secretary",
  "type": "Scripted",
  "language": "English",
  "genres": ["Drama"],
  "status": "Running",
  "runtime": 60,
  "premiered": "2014-09-21",
  "officialSite": "http://www.cbs.com/shows/madam-secretary/",
  "schedule": {
    "time": "22:00",
    "days": ["Sunday"]
  },
  "rating": {
    "average": 7.9
  },
  "weight": 97,
  "network": {
    "id": 2,
    "name": "CBS",
    "country": {
      "name": "United States",
      "code": "US",
      "timezone": "America/New_York"
    }
  },
  "webChannel": null,
  "externals": {
    "tvrage": 37247,
    "thetvdb": 281623,
    "imdb": "tt3501074"
  },
  "image": {
    "medium": "http://static.tvmaze.com/uploads/images/medium_portrait/0/399.jpg",
    "original": "http://static.tvmaze.com/uploads/images/original_untouched/0/399.jpg"
  },
  "summary": "<p><b>Madam Secretary</b> follows Elizabeth McCord, the shrewd, determined, newly appointed Secretary of State who drives international diplomacy, battles office politics and circumvents protocol as she negotiates global and domestic issues, both at the White House and at home. A college professor and a brilliant former CIA analyst who left for ethical reasons, Elizabeth returns to public life at the request of the President following the suspicious death of her predecessor. The President values her apolitical leanings, her deep knowledge of the Middle East, her flair for languages and her ability to not just think outside the box, but to not even acknowledge there is a box.</p>",
  "updated": 1535111282,
  "_links": {
    "self": {
      "href": "http://api.tvmaze.com/shows/48"
    },
    "previousepisode": {
      "href": "http://api.tvmaze.com/episodes/1431764"
    },
    "nextepisode": {
      "href": "http://api.tvmaze.com/episodes/1489850"
    }
  }
}

```
### Selecting a Document with Filtering a Field by Some Acceptable Values

**Command**
```json
db.movies.find({"genres": {$in: ["Drama", "Horror"]}})
```
**Output**
```json
[
  {
    "_id": "674879d3c6ec200ac032329e",
    "id": 22,
    "url": "http://www.tvmaze.com/shows/22/true-blood",
    "name": "True Blood",
    "type": "Scripted",
    "language": "English",
    "genres": ["Drama", "Romance", "Supernatural"],
    "status": "Ended",
    "runtime": 60,
    "premiered": "2008-09-07",
    "officialSite": "http://www.hbo.com/true-blood",
    "schedule": {
      "time": "21:00",
      "days": ["Sunday"]
    },
    "rating": {
      "average": 8
    },
    "weight": 89,
    "network": {
      "id": 8,
      "name": "HBO",
      "country": {
        "name": "United States",
        "code": "US",
        "timezone": "America/New_York"
      }
    },
    "webChannel": null,
    "externals": {
      "tvrage": 12662,
      "thetvdb": 82283,
      "imdb": "tt0844441"
    },
    "image": {
      "medium": "http://static.tvmaze.com/uploads/images/medium_portrait/0/241.jpg",
      "original": "http://static.tvmaze.com/uploads/images/original_untouched/0/241.jpg"
    },
    "summary": "<p><b>True Blood</b> is a horror/drama based on a series of novels called <i>The Southern American Vampires Mysteries</i>. It focuses on Sookie Stackhouse and her various encounters with vampires and other supernatural beings. The show is centred in the small town of Bon Temps in Louisiana. The show focuses heavily on the co-existence of humans with vampires. The show also touches on several other controversial issues involving equal rights, violence, discrimination and religion.</p>",
    "updated": 1535396317,
    "_links": {
      "self": {
        "href": "http://api.tvmaze.com/shows/22"
      },
      "previousepisode": {
        "href": "http://api.tvmaze.com/episodes/1292"
      }
    }
  },
  {
    "_id": "674879d3c6ec200ac03232a0",
    "id": 25,
    "url": "http://www.tvmaze.com/shows/25/hellsing",
    "name": "Hellsing",
    "type": "Animation",
    "language": "Japanese",
    "genres": ["Anime", "Horror", "Supernatural"],
    "status": "Ended",
    "runtime": 30,
    "premiered": "2001-10-10",
    "officialSite": null,
    "schedule": {
      "time": "",
      "days": ["Wednesday"]
    },
    "rating": {
      "average": 8.3
    },
    "weight": 22,
    "network": {
      "id": 131,
      "name": "Fuji TV",
      "country": {
        "name": "Japan",
        "code": "JP",
        "timezone": "Asia/Tokyo"
      }
    },
    "webChannel": null,
    "externals": {
      "tvrage": 9139,
      "thetvdb": 71278,
      "imdb": "tt0325547"
    },
    "image": {
      "medium": "http://static.tvmaze.com/uploads/images/medium_portrait/0/247.jpg",
      "original": "http://static.tvmaze.com/uploads/images/original_untouched/0/247.jpg"
    },
    "summary": "<p><b>Hellsing</b> is a 13-part anime based on the manga of the same name. The plot is significantly different from that of the manga, although the characters are the same. The show mainly focuses on the Hellsing Institute that houses the anti-hero named Alucard, who swore loyalty to the Hellsing family many years before. Alucard, being the first-ever vampire, takes on a new apprentice named Seras.</p>",
    "updated": 1504676730,
    "_links": {
      "self": {
        "href": "http://api.tvmaze.com/shows/25"
      },
      "previousepisode": {
        "href": "http://api.tvmaze.com/episodes/398491"
      }
    }
  },
  {
    "_id": "674879d3c6ec200ac03232a1",
    "id": 26,
    "url": "http://www.tvmaze.com/shows/26/hellsing-ultimate",
    "name": "Hellsing Ultimate",
    "type": "Animation",
    "language": "Japanese",
    "genres": ["Drama", "Action", "Anime", "Horror"],
    "status": "Ended",
    "runtime": 50,
    "premiered": "2006-02-10",
    "officialSite": null,
    "schedule": {
      "time": "12:00",
      "days": ["Wednesday"]
    },
    "rating": {
      "average": 8.1
    },
    "weight": 0,
    "network": {
      "id": 159,
      "name": "TBS",
      "country": {
        "name": "Japan",
        "code": "JP",
        "timezone": "Asia/Tokyo"
      }
    },
    "webChannel": null,
    "externals": {
      "tvrage": 29109,
      "thetvdb": 263688,
      "imdb": "tt0495212"
    },
    "image": {
      "medium": "http://static.tvmaze.com/uploads/images/medium_portrait/22/55037.jpg",
      "original": "http://static.tvmaze.com/uploads/images/original_untouched/22/55037.jpg"
    },
    "summary": "<p><b>Hellsing Ultimate</b>, unlike the 13-part <i>Hellsing</i> series, follows the manga of the same name very closely. Alucard is the main protagonist and anti-hero/vampire. <i>Hellsing Ultimate</i> is a 10-part series of OVAs where Alucard turns Seras into a vampire. The main focus of the plot is on an enemy neo-nazi group.</p>",
    "updated": 1504676814,
    "_links": {
      "self": {
        "href": "http://api.tvmaze.com/shows/26"
      },
      "previousepisode": {
        "href": "http://api.tvmaze.com/episodes/1437"
      }
    }
  }
]
```

### Selecting a Document with Filtering a Field by Some Unacceptable Values

**Command**
```json
db.movies.find({"genres": {$nin: ["Drama", "Horror"]}})
```
**Output**
```json
[
  {
    "_id": "674879d3c6ec200ac03232dc",
    "id": 84,
    "url": "http://www.tvmaze.com/shows/84/family-guy",
    "name": "Family Guy",
    "type": "Animation",
    "language": "English",
    "genres": ["Comedy"],
    "status": "Running",
    "runtime": 30,
    "premiered": "1999-01-31",
    "officialSite": "http://www.fox.com/family-guy",
    "schedule": {
      "time": "21:00",
      "days": ["Sunday"]
    },
    "rating": {
      "average": 7.8
    },
    "weight": 98,
    "network": {
      "id": 4,
      "name": "FOX",
      "country": {
        "name": "United States",
        "code": "US",
        "timezone": "America/New_York"
      }
    },
    "webChannel": null,
    "externals": {
      "tvrage": 3506,
      "thetvdb": 75978,
      "imdb": "tt0182576"
    },
    "image": {
      "medium": "http://static.tvmaze.com/uploads/images/medium_portrait/0/641.jpg",
      "original": "http://static.tvmaze.com/uploads/images/original_untouched/0/641.jpg"
    },
    "summary": "<p><b>Family Guy</b> follows Peter Griffin the endearingly ignorant dad, and his hilariously offbeat family of middle-class New Englanders in Quahog, RI. Lois is Peter's wife, a stay-at-home mom with no patience for her family's antics. Then there are their kids: 18-year-old Meg is an outcast at school and the Griffin family punching bag; 13-year-old Chris is a socially awkward teen who doesn't have a clue about the opposite sex; and one-year-old Stewie is a diabolically clever baby whose burgeoning sexuality is very much a work in progress. Rounding out the Griffin household is Brian the family dog and a ladies' man who is one step away from AA.</p>",
    "updated": 1536482572,
    "_links": {
      "self": {
        "href": "http://api.tvmaze.com/shows/84"
      },
      "previousepisode": {
        "href": "http://api.tvmaze.com/episodes/1430063"
      },
      "nextepisode": {
        "href": "http://api.tvmaze.com/episodes/1486841"
      }
    }
  },
  {
    "_id": "674879d3c6ec200ac03232dd",
    "id": 86,
    "url": "http://www.tvmaze.com/shows/86/stalker",
    "name": "Stalker",
    "type": "Scripted",
    "language": "English",
    "genres": ["Crime", "Thriller"],
    "status": "Ended",
    "runtime": 60,
    "premiered": "2014-10-01",
    "officialSite": null,
    "schedule": {
      "time": "22:00",
      "days": ["Wednesday"]
    },
    "rating": {
      "average": 7.7
    },
    "weight": 73,
    "network": {
      "id": 2,
      "name": "CBS",
      "country": {
        "name": "United States",
        "code": "US",
        "timezone": "America/New_York"
      }
    },
    "webChannel": null,
    "externals": {
      "tvrage": 41213,
      "thetvdb": 281697,
      "imdb": "tt3560094"
    },
    "image": {
      "medium": "http://static.tvmaze.com/uploads/images/medium_portrait/0/647.jpg",
      "original": "http://static.tvmaze.com/uploads/images/original_untouched/0/647.jpg"
    },
    "summary": "<p><b>Stalker</b> is a psychological thriller about detectives who investigate stalking incidents - including voyeurism, cyber harassment and romantic fixation - for the Threat Assessment Unit of the LAPD. Det. Jack Larsen is a recent transfer to the Unit from New York City's homicide division, whose confidence, strong personality and questionable behavior has landed him in trouble before - but whose past behavior may also prove valuable in his new job. His boss, Lt. Beth Davis, is strong, focused and an expert in the field, driven by her traumatic personal experience as a victim. With the rest of their team, young but eager Det. Ben Caldwell and deceptively smart Det. Janice Lawrence Larsen and Davis assess the threat level of cases and respond before the stalking and intimidation spirals out of control, all while trying to keep their personal obsessions at bay.</p>",
    "updated": 1535297749,
    "_links": {
      "self": {
        "href": "http://api.tvmaze.com/shows/86"
      },
      "previousepisode": {
        "href": "http://api.tvmaze.com/episodes/155326"
      }
    }
  }
]
```

### Selecting a Document with OR

**Command**
```json
db.movies.find({$or: [{"rating.average": {$lt: 6}}, {"rating.average": {$gt: 9.4}}]})
```
**Output**
```json
[
  {
    "_id": "ObjectId('674879d3c6ec200ac03232b3')",
    "id": 50,
    "url": "http://www.tvmaze.com/shows/50/the-lottery",
    "name": "The Lottery",
    "type": "Scripted",
    "language": "English",
    "genres": ["Drama", "Science-Fiction", "Thriller"],
    "status": "Ended",
    "runtime": 60,
    "premiered": "2014-07-20",
    "officialSite": null,
    "schedule": { "time": "22:00", "days": ["Sunday"] },
    "rating": { "average": 5.9 },
    "weight": 87,
    "network": {
      "id": 18,
      "name": "Lifetime",
      "country": {
        "name": "United States",
        "code": "US",
        "timezone": "America/New_York"
      }
    },
    "webChannel": null,
    "externals": { "tvrage": 37857, "thetvdb": 278447, "imdb": "tt3314228" },
    "image": {
      "medium": "http://static.tvmaze.com/uploads/images/medium_portrait/146/366444.jpg",
      "original": "http://static.tvmaze.com/uploads/images/original_untouched/146/366444.jpg"
    },
    "summary": "<p>Set within a dystopian future driven by a global fertility crisis, <b>The Lottery</b> reveals a world staring down the barrel of impending extinction as women have mysteriously stopped bearing children. After years of research, Dr. Alison Lennon and her team remarkably fertilize 100 embryos. However, her victory is short-lived when the Director of the U.S. Fertility Commission, Darius Hayes, takes government control of the lab and informs the President of the monumental scientific breakthrough. To determine which women will carry the prized embryos to term, Chief of Staff Vanessa Keller convinces the President to hold a national lottery and a battle over the control of the 100 embryos begins.</p>",
    "updated": 1519024903,
    "_links": {
      "self": { "href": "http://api.tvmaze.com/shows/50" },
      "previousepisode": { "href": "http://api.tvmaze.com/episodes/2045" }
    }
  },
  {
    "_id": "ObjectId('674879d3c6ec200ac03232ce')",
    "id": 71,
    "url": "http://www.tvmaze.com/shows/71/dancing-with-the-stars",
    "name": "Dancing with the Stars",
    "type": "Reality",
    "language": "English",
    "genres": ["Music"],
    "status": "Running",
    "runtime": 120,
    "premiered": "2005-06-01",
    "officialSite": "http://abc.go.com/shows/dancing-with-the-stars",
    "schedule": { "time": "20:00", "days": ["Monday"] },
    "rating": { "average": 4.7 },
    "weight": 84,
    "network": {
      "id": 3,
      "name": "ABC",
      "country": {
        "name": "United States",
        "code": "US",
        "timezone": "America/New_York"
      }
    },
    "webChannel": null,
    "externals": { "tvrage": 3220, "thetvdb": 79590, "imdb": "tt0463398" },
    "image": {
      "medium": "http://static.tvmaze.com/uploads/images/medium_portrait/0/501.jpg",
      "original": "http://static.tvmaze.com/uploads/images/original_untouched/0/501.jpg"
    },
    "summary": "<p><b>Dancing with the Stars</b> is an american dance competition show and especially the american version of the british show <i>Strictly Come Dancing</i>.</p>",
    "updated": 1532455112,
    "_links": {
      "self": { "href": "http://api.tvmaze.com/shows/71" },
      "previousepisode": { "href": "http://api.tvmaze.com/episodes/1446662" },
      "nextepisode": { "href": "http://api.tvmaze.com/episodes/1501076" }
    }
  }
]

```
### Selecting a Document with NOR (Inverse of OR)

**Command**
```json
db.movies.find().count()
db.movies.find({$or: [{"rating.average": {$lt: 6}}, {"rating.average": {$gt: 9.4}}]}).count()
db.movies.find({$nor: [{"rating.average": {$lt: 6}}, {"rating.average": {$gt: 9.4}}]}).count()
```
**Output**
```json
240
6
234
```
### Selecting a Document with AND

**Command**
```json
db.movies.findOne({$and: [{"rating.average": {$gt: 9}}, {"genres": "Horror"}]})
```
**Output**
```json
{
  "_id": ObjectId('674879d3c6ec200ac03232a4'),
  "id": 27,
  "url": "http://www.tvmaze.com/shows/27/berserk",
  "name": "Berserk",
  "type": "Animation",
  "language": "Japanese",
  "genres": ["Anime", "Fantasy", "Horror"],
  "status": "Ended",
  "runtime": 25,
  "premiered": "1997-10-07",
  "officialSite": null,
  "schedule": { "time": "", "days": ["Tuesday"] },
  "rating": { "average": 9.2 },
  "weight": 58,
  "network": {
    "id": 137,
    "name": "NTV",
    "country": { "name": "Japan", "code": "JP", "timezone": "Asia/Tokyo" }
  },
  "webChannel": null,
  "externals": { "tvrage": 2764, "thetvdb": 73752, "imdb": "tt0318871" },
  "image": {
    "medium": "http://static.tvmaze.com/uploads/images/medium_portrait/0/249.jpg",
    "original": "http://static.tvmaze.com/uploads/images/original_untouched/0/249.jpg"
  },
  "summary": "<p><b>Berserk</b> is a 25-part anime set in a dark fantasy/horror environment whereby the series focuses on the main character Guts; a lone swordsman who later meets up with a group of mercenaries called the Band of the Hawk. The leader of this band holds a strange necklace called a behelit that will only lead to evil.</p>",
  "updated": 1504676900,
  "_links": {
    "self": { "href": "http://api.tvmaze.com/shows/27" },
    "previousepisode": { "href": "http://api.tvmaze.com/episodes/1462" }
  }
}

```
### Selecting a Document with NOT

**Command**
```json
 db.movies.findOne({"genres": {$not: {$eq: "Horror"}}})
```
**Output**
```json
{
  "_id": ObjectId('674879d3c6ec200ac032328c'),
  "id": 1,
  "url": "http://www.tvmaze.com/shows/1/under-the-dome",
  "name": "Under the Dome",
  "type": "Scripted",
  "language": "English",
  "genres": ["Drama", "Science-Fiction", "Thriller"],
  "status": "Ended",
  "runtime": 60,
  "premiered": "2013-06-24",
  "officialSite": "http://www.cbs.com/shows/under-the-dome/",
  "schedule": { "time": "22:00", "days": ["Thursday"] },
  "rating": { "average": 6.5 },
  "weight": 91,
  "network": {
    "id": 2,
    "name": "CBS",
    "country": { "name": "United States", "code": "US", "timezone": "America/New_York" }
  },
  "webChannel": null,
  "externals": { "tvrage": 25988, "thetvdb": 264492, "imdb": "tt1553656" },
  "image": {
    "medium": "http://static.tvmaze.com/uploads/images/medium_portrait/0/1.jpg",
    "original": "http://static.tvmaze.com/uploads/images/original_untouched/0/1.jpg"
  },
  "summary": "<p><b>Under the Dome</b> is the story of a small town that is suddenly and inexplicably sealed off from the rest of the world by an enormous transparent dome. The town's inhabitants must deal with surviving the post-apocalyptic conditions while searching for answers about the dome, where it came from and if and when it will go away.</p>",
  "updated": 1529612668,
  "_links": {
    "self": { "href": "http://api.tvmaze.com/shows/1" },
    "previousepisode": { "href": "http://api.tvmaze.com/episodes/185054" }
  }
}
```