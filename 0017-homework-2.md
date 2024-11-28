## Task-1: Insert multiple companies into a collection with both insertOne() and insertMany()

### Inserting One Document

**Command**
```json
use economy
db.companies.insertOne(    {
      "_id": "company_1",
      "companyName": "Example Tech Inc.",
      "foundedYear": 2015,
      "industry": "Software Development",
      "employees": 120,
      "headquarters": {
        "address": "123 Innovation Road",
        "city": "San Francisco",
        "country": "USA"
      },
      "contact": {
        "email": "contact@exampletech.com",
        "phone": "+1 415 123 4567",
        "website": "https://www.exampletech.com"
      },
      "services": ["Web Development", "Mobile Applications", "Cloud Solutions"],
      "socialMedia": {
        "linkedin": "https://www.linkedin.com/company/exampletech",
        "twitter": "https://twitter.com/exampletech"
      }
    })
```
**Output**
```json
switched to db economy

{
  "acknowledged": true,
  "insertedId": "company_1"
}

```

## Current Data
**Command**

```json
db.companies.find()
```
**Output**
```json
{
  "_id": "company_1",
  "companyName": "Example Tech Inc.",
  "foundedYear": 2015,
  "industry": "Software Development",
  "employees": 120,
  "headquarters": {
    "address": "123 Innovation Road",
    "city": "San Francisco",
    "country": "USA"
  },
  "contact": {
    "email": "contact@exampletech.com",
    "phone": "+1 415 123 4567",
    "website": "https://www.exampletech.com"
  },
  "services": [
    "Web Development",
    "Mobile Applications",
    "Cloud Solutions"
  ],
  "socialMedia": {
    "linkedin": "https://www.linkedin.com/company/exampletech",
    "twitter": "https://twitter.com/exampletech"
  }
}

```

### Inserting Many Documents

**Command**
```json
db.companies.insertMany([    {
      "_id": "company_2",
      "companyName": "Green Energy Solutions Ltd.",
      "foundedYear": 2010,
      "industry": "Renewable Energy",
      "employees": 200,
      "headquarters": {
        "address": "456 Solar Drive",
        "city": "London",
        "country": "UK"
      },
      "contact": {
        "email": "info@greenenergy.com",
        "phone": "+44 20 7890 1234",
        "website": "https://www.greenenergy.com"
      },
      "services": ["Solar Panels", "Wind Turbines", "Energy Consulting"],
      "socialMedia": {
        "linkedin": "https://www.linkedin.com/company/greenenergy",
        "twitter": "https://twitter.com/greenenergy"
      }
    },
    {
      "_id": "company_3",
      "companyName": "Smart Retail Co.",
      "foundedYear": 2018,
      "industry": "E-commerce",
      "employees": 50,
      "headquarters": {
        "address": "789 Commerce Lane",
        "city": "New York",
        "country": "USA"
      },
      "contact": {
        "email": "support@smartretail.com",
        "phone": "+1 212 987 6543",
        "website": "https://www.smartretail.com"
      },
      "services": ["Online Shopping", "Digital Payments", "Customer Analytics"],
      "socialMedia": {
        "linkedin": "https://www.linkedin.com/company/smartretail",
        "twitter": "https://twitter.com/smartretail"
      }
    }])
```
**Output**
```json
{
  "acknowledged": true,
  "insertedIds": {
    "0": "company_2",
    "1": "company_3"
  }
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
    "_id": "company_1",
    "companyName": "Example Tech Inc.",
    "foundedYear": 2015,
    "industry": "Software Development",
    "employees": 120,
    "headquarters": {
      "address": "123 Innovation Road",
      "city": "San Francisco",
      "country": "USA"
    },
    "contact": {
      "email": "contact@exampletech.com",
      "phone": "+1 415 123 4567",
      "website": "https://www.exampletech.com"
    },
    "services": [
      "Web Development",
      "Mobile Applications",
      "Cloud Solutions"
    ],
    "socialMedia": {
      "linkedin": "https://www.linkedin.com/company/exampletech",
      "twitter": "https://twitter.com/exampletech"
    }
  },
  {
    "_id": "company_2",
    "companyName": "Green Energy Solutions Ltd.",
    "foundedYear": 2010,
    "industry": "Renewable Energy",
    "employees": 200,
    "headquarters": {
      "address": "456 Solar Drive",
      "city": "London",
      "country": "UK"
    },
    "contact": {
      "email": "info@greenenergy.com",
      "phone": "+44 20 7890 1234",
      "website": "https://www.greenenergy.com"
    },
    "services": [
      "Solar Panels",
      "Wind Turbines",
      "Energy Consulting"
    ],
    "socialMedia": {
      "linkedin": "https://www.linkedin.com/company/greenenergy",
      "twitter": "https://twitter.com/greenenergy"
    }
  },
  {
    "_id": "company_3",
    "companyName": "Smart Retail Co.",
    "foundedYear": 2018,
    "industry": "E-commerce",
    "employees": 50,
    "headquarters": {
      "address": "789 Commerce Lane",
      "city": "New York",
      "country": "USA"
    },
    "contact": {
      "email": "support@smartretail.com",
      "phone": "+1 212 987 6543",
      "website": "https://www.smartretail.com"
    },
    "services": [
      "Online Shopping",
      "Digital Payments",
      "Customer Analytics"
    ],
    "socialMedia": {
      "linkedin": "https://www.linkedin.com/company/smartretail",
      "twitter": "https://twitter.com/smartretail"
    }
  }
]

```
## Task-2: Deliberately insert data with duplicate _id and "fix" failing additions with unordered inserts

### Inserting Many Documents with overlapping _id data

**Command**
```json
db.companies.insertMany([    {
      "_id": "company_2",
      "companyName": "Green Energy Solutions Ltd.",
      "foundedYear": 2010,
      "industry": "Renewable Energy",
      "employees": 200,
      "headquarters": {
        "address": "456 Solar Drive",
        "city": "London",
        "country": "UK"
      },
      "contact": {
        "email": "info@greenenergy.com",
        "phone": "+44 20 7890 1234",
        "website": "https://www.greenenergy.com"
      },
      "services": ["Solar Panels", "Wind Turbines", "Energy Consulting"],
      "socialMedia": {
        "linkedin": "https://www.linkedin.com/company/greenenergy",
        "twitter": "https://twitter.com/greenenergy"
      }
    },
    {
      "_id": "company_4",
      "companyName": "HealthTech Innovations",
      "foundedYear": 2012,
      "industry": "Healthcare Technology",
      "employees": 300,
      "headquarters": {
        "address": "321 Wellness Blvd",
        "city": "Toronto",
        "country": "Canada"
      },
      "contact": {
        "email": "info@healthtech.com",
        "phone": "+1 416 555 7890",
        "website": "https://www.healthtech.com"
      },
      "services": ["Telemedicine", "Health Data Analytics", "Medical Devices"],
      "socialMedia": {
        "linkedin": "https://www.linkedin.com/company/healthtech",
        "twitter": "https://twitter.com/healthtech"
      }
    },
    {
      "_id": "company_5",
      "companyName": "EduSmart Systems",
      "foundedYear": 2016,
      "industry": "Education Technology",
      "employees": 80,
      "headquarters": {
        "address": "987 Knowledge Way",
        "city": "Austin",
        "country": "USA"
      },
      "contact": {
        "email": "hello@edusmart.com",
        "phone": "+1 512 123 9876",
        "website": "https://www.edusmart.com"
      },
      "services": ["E-learning Platforms", "Virtual Classrooms", "Student Management Systems"],
      "socialMedia": {
        "linkedin": "https://www.linkedin.com/company/edusmart",
        "twitter": "https://twitter.com/edusmart"
      }
    },
    {
      "_id": "company_3",
      "companyName": "Smart Retail Co.",
      "foundedYear": 2018,
      "industry": "E-commerce",
      "employees": 50,
      "headquarters": {
        "address": "789 Commerce Lane",
        "city": "New York",
        "country": "USA"
      },
      "contact": {
        "email": "support@smartretail.com",
        "phone": "+1 212 987 6543",
        "website": "https://www.smartretail.com"
      },
      "services": ["Online Shopping", "Digital Payments", "Customer Analytics"],
      "socialMedia": {
        "linkedin": "https://www.linkedin.com/company/smartretail",
        "twitter": "https://twitter.com/smartretail"
      }
    },
    {
      "_id": "company_6",
      "companyName": "TravelEase Inc.",
      "foundedYear": 2014,
      "industry": "Travel and Tourism",
      "employees": 150,
      "headquarters": {
        "address": "456 Wanderlust Ave",
        "city": "Sydney",
        "country": "Australia"
      },
      "contact": {
        "email": "support@travelease.com",
        "phone": "+61 2 1234 5678",
        "website": "https://www.travelease.com"
      },
      "services": ["Flight Booking", "Hotel Reservations", "Travel Packages"],
      "socialMedia": {
        "linkedin": "https://www.linkedin.com/company/travelease",
        "twitter": "https://twitter.com/travelease"
      }
    }], {"ordered": false})
```
**Output**
```json
Uncaught:
MongoBulkWriteError: E11000 duplicate key error collection: economy.companies index: _id_ dup key: { "_id": "company_2" }
Result: BulkWriteResult {
  "insertedCount": 3,
  "matchedCount": 0,
  "modifiedCount": 0,
  "deletedCount": 0,
  "upsertedCount": 0,
  "upsertedIds": {},
  "insertedIds": { "1": "company_4", "2": "company_5", "4": "company_6" }
}
Write Errors: [
  WriteError {
    "err": {
      "index": 0,
      "code": 11000,
      "errmsg": "E11000 duplicate key error collection: economy.companies index: _id_ dup key: { \"_id\": \"company_2\" }",
      "errInfo": null,
      "op": {
        "_id": "company_2",
        "companyName": "Green Energy Solutions Ltd.",
        "foundedYear": 2010,
        "industry": "Renewable Energy",
        "employees": 200,
        "headquarters": { 
          "address": "456 Solar Drive", 
          "city": "London", 
          "country": "UK" 
        },
        "contact": {
          "email": "info@greenenergy.com",
          "phone": "+44 20 7890 1234",
          "website": "https://www.greenenergy.com"
        },
        "services": [ "Solar Panels", "Wind Turbines", "Energy Consulting" ],
        "socialMedia": {
          "linkedin": "https://www.linkedin.com/company/greenenergy",
          "twitter": "https://twitter.com/greenenergy"
        }
      }
    }
  },
  WriteError {
    "err": {
      "index": 3,
      "code": 11000,
      "errmsg": "E11000 duplicate key error collection: economy.companies index: _id_ dup key: { \"_id\": \"company_3\" }",
      "errInfo": null,
      "op": {
        "_id": "company_3",
        "companyName": "Smart Retail Co.",
        "foundedYear": 2018,
        "industry": "E-commerce",
        "employees": 50,
        "headquarters": {
          "address": "789 Commerce Lane",
          "city": "New York",
          "country": "USA"
        },
        "contact": {
          "email": "support@smartretail.com",
          "phone": "+1 212 987 6543",
          "website": "https://www.smartretail.com"
        },
        "services": [ "Online Shopping", "Digital Payments", "Customer Analytics" ],
        "socialMedia": {
          "linkedin": "https://www.linkedin.com/company/smartretail",
          "twitter": "https://twitter.com/smartretail"
        }
      }
    }
  }
]

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
    "_id": "company_1",
    "companyName": "Example Tech Inc.",
    "foundedYear": 2015,
    "industry": "Software Development",
    "employees": 120,
    "headquarters": {
      "address": "123 Innovation Road",
      "city": "San Francisco",
      "country": "USA"
    },
    "contact": {
      "email": "contact@exampletech.com",
      "phone": "+1 415 123 4567",
      "website": "https://www.exampletech.com"
    },
    "services": ["Web Development", "Mobile Applications", "Cloud Solutions"],
    "socialMedia": {
      "linkedin": "https://www.linkedin.com/company/exampletech",
      "twitter": "https://twitter.com/exampletech"
    }
  },
  {
    "_id": "company_2",
    "companyName": "Green Energy Solutions Ltd.",
    "foundedYear": 2010,
    "industry": "Renewable Energy",
    "employees": 200,
    "headquarters": {
      "address": "456 Solar Drive",
      "city": "London",
      "country": "UK"
    },
    "contact": {
      "email": "info@greenenergy.com",
      "phone": "+44 20 7890 1234",
      "website": "https://www.greenenergy.com"
    },
    "services": ["Solar Panels", "Wind Turbines", "Energy Consulting"],
    "socialMedia": {
      "linkedin": "https://www.linkedin.com/company/greenenergy",
      "twitter": "https://twitter.com/greenenergy"
    }
  },
  {
    "_id": "company_3",
    "companyName": "Smart Retail Co.",
    "foundedYear": 2018,
    "industry": "E-commerce",
    "employees": 50,
    "headquarters": {
      "address": "789 Commerce Lane",
      "city": "New York",
      "country": "USA"
    },
    "contact": {
      "email": "support@smartretail.com",
      "phone": "+1 212 987 6543",
      "website": "https://www.smartretail.com"
    },
    "services": ["Online Shopping", "Digital Payments", "Customer Analytics"],
    "socialMedia": {
      "linkedin": "https://www.linkedin.com/company/smartretail",
      "twitter": "https://twitter.com/smartretail"
    }
  },
  {
    "_id": "company_4",
    "companyName": "HealthTech Innovations",
    "foundedYear": 2012,
    "industry": "Healthcare Technology",
    "employees": 300,
    "headquarters": {
      "address": "321 Wellness Blvd",
      "city": "Toronto",
      "country": "Canada"
    },
    "contact": {
      "email": "info@healthtech.com",
      "phone": "+1 416 555 7890",
      "website": "https://www.healthtech.com"
    },
    "services": ["Telemedicine", "Health Data Analytics", "Medical Devices"],
    "socialMedia": {
      "linkedin": "https://www.linkedin.com/company/healthtech",
      "twitter": "https://twitter.com/healthtech"
    }
  },
  {
    "_id": "company_5",
    "companyName": "EduSmart Systems",
    "foundedYear": 2016,
    "industry": "Education Technology",
    "employees": 80,
    "headquarters": {
      "address": "987 Knowledge Way",
      "city": "Austin",
      "country": "USA"
    },
    "contact": {
      "email": "hello@edusmart.com",
      "phone": "+1 512 123 9876",
      "website": "https://www.edusmart.com"
    },
    "services": [
      "E-learning Platforms",
      "Virtual Classrooms",
      "Student Management Systems"
    ],
    "socialMedia": {
      "linkedin": "https://www.linkedin.com/company/edusmart",
      "twitter": "https://twitter.com/edusmart"
    }
  },
  {
    "_id": "company_6",
    "companyName": "TravelEase Inc.",
    "foundedYear": 2014,
    "industry": "Travel and Tourism",
    "employees": 150,
    "headquarters": {
      "address": "456 Wanderlust Ave",
      "city": "Sydney",
      "country": "Australia"
    },
    "contact": {
      "email": "support@travelease.com",
      "phone": "+61 2 1234 5678",
      "website": "https://www.travelease.com"
    },
    "services": ["Flight Booking", "Hotel Reservations", "Travel Packages"],
    "socialMedia": {
      "linkedin": "https://www.linkedin.com/company/travelease",
      "twitter": "https://twitter.com/travelease"
    }
  }
]
```

## Task-3: Write data for a new company with both journalling being guaranteed and not being guaranteed

### Inserting One Document with Journalling Not Guaranteed

**Command**
```json
use economy
db.companies.insertOne({
      "_id": "company_7",
      "companyName": "UrbanDesign Studio",
      "foundedYear": 2008,
      "industry": "Architecture",
      "employees": 60,
      "headquarters": {
        "address": "123 Creative Street",
        "city": "Amsterdam",
        "country": "Netherlands"
      },
      "contact": {
        "email": "contact@urbandesign.com",
        "phone": "+31 20 123 4567",
        "website": "https://www.urbandesign.com"
      },
      "services": ["Urban Planning", "Interior Design", "Sustainable Architecture"],
      "socialMedia": {
        "linkedin": "https://www.linkedin.com/company/urbandesign",
        "twitter": "https://twitter.com/urbandesign"
      }
    }, 
    {"writeConcern": {w:1, j:false}})
```
**Output**
```json
{ "acknowledged": true, "insertedId": "company_7" }
```

### Inserting One Document with Journalling Guaranteed

**Command**
```json
use economy
db.companies.insertOne({
      "_id": "company_8",
      "companyName": "FinSecure Partners",
      "foundedYear": 2005,
      "industry": "Financial Services",
      "employees": 500,
      "headquarters": {
        "address": "789 Finance Plaza",
        "city": "Singapore",
        "country": "Singapore"
      },
      "contact": {
        "email": "info@finsecure.com",
        "phone": "+65 6234 5678",
        "website": "https://www.finsecure.com"
      },
      "services": ["Investment Advisory", "Insurance Solutions", "Wealth Management"],
      "socialMedia": {
        "linkedin": "https://www.linkedin.com/company/finsecure",
        "twitter": "https://twitter.com/finsecure"
      }
    }, 
    {"writeConcern": {"w":1, "j":true}})
```
**Output**
```json
{ "acknowledged": true, "insertedId": "company_8" }
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
    "_id": "company_1",
    "companyName": "Example Tech Inc.",
    "foundedYear": 2015,
    "industry": "Software Development",
    "employees": 120,
    "headquarters": {
      "address": "123 Innovation Road",
      "city": "San Francisco",
      "country": "USA"
    },
    "contact": {
      "email": "contact@exampletech.com",
      "phone": "+1 415 123 4567",
      "website": "https://www.exampletech.com"
    },
    "services": ["Web Development", "Mobile Applications", "Cloud Solutions"],
    "socialMedia": {
      "linkedin": "https://www.linkedin.com/company/exampletech",
      "twitter": "https://twitter.com/exampletech"
    }
  },
  {
    "_id": "company_2",
    "companyName": "Green Energy Solutions Ltd.",
    "foundedYear": 2010,
    "industry": "Renewable Energy",
    "employees": 200,
    "headquarters": {
      "address": "456 Solar Drive",
      "city": "London",
      "country": "UK"
    },
    "contact": {
      "email": "info@greenenergy.com",
      "phone": "+44 20 7890 1234",
      "website": "https://www.greenenergy.com"
    },
    "services": ["Solar Panels", "Wind Turbines", "Energy Consulting"],
    "socialMedia": {
      "linkedin": "https://www.linkedin.com/company/greenenergy",
      "twitter": "https://twitter.com/greenenergy"
    }
  },
  {
    "_id": "company_3",
    "companyName": "Smart Retail Co.",
    "foundedYear": 2018,
    "industry": "E-commerce",
    "employees": 50,
    "headquarters": {
      "address": "789 Commerce Lane",
      "city": "New York",
      "country": "USA"
    },
    "contact": {
      "email": "support@smartretail.com",
      "phone": "+1 212 987 6543",
      "website": "https://www.smartretail.com"
    },
    "services": ["Online Shopping", "Digital Payments", "Customer Analytics"],
    "socialMedia": {
      "linkedin": "https://www.linkedin.com/company/smartretail",
      "twitter": "https://twitter.com/smartretail"
    }
  },
  {
    "_id": "company_4",
    "companyName": "HealthTech Innovations",
    "foundedYear": 2012,
    "industry": "Healthcare Technology",
    "employees": 300,
    "headquarters": {
      "address": "321 Wellness Blvd",
      "city": "Toronto",
      "country": "Canada"
    },
    "contact": {
      "email": "info@healthtech.com",
      "phone": "+1 416 555 7890",
      "website": "https://www.healthtech.com"
    },
    "services": ["Telemedicine", "Health Data Analytics", "Medical Devices"],
    "socialMedia": {
      "linkedin": "https://www.linkedin.com/company/healthtech",
      "twitter": "https://twitter.com/healthtech"
    }
  },
  {
    "_id": "company_5",
    "companyName": "EduSmart Systems",
    "foundedYear": 2016,
    "industry": "Education Technology",
    "employees": 80,
    "headquarters": {
      "address": "987 Knowledge Way",
      "city": "Austin",
      "country": "USA"
    },
    "contact": {
      "email": "hello@edusmart.com",
      "phone": "+1 512 123 9876",
      "website": "https://www.edusmart.com"
    },
    "services": [
      "E-learning Platforms",
      "Virtual Classrooms",
      "Student Management Systems"
    ],
    "socialMedia": {
      "linkedin": "https://www.linkedin.com/company/edusmart",
      "twitter": "https://twitter.com/edusmart"
    }
  },
  {
    "_id": "company_6",
    "companyName": "TravelEase Inc.",
    "foundedYear": 2014,
    "industry": "Travel and Tourism",
    "employees": 150,
    "headquarters": {
      "address": "456 Wanderlust Ave",
      "city": "Sydney",
      "country": "Australia"
    },
    "contact": {
      "email": "support@travelease.com",
      "phone": "+61 2 1234 5678",
      "website": "https://www.travelease.com"
    },
    "services": ["Flight Booking", "Hotel Reservations", "Travel Packages"],
    "socialMedia": {
      "linkedin": "https://www.linkedin.com/company/travelease",
      "twitter": "https://twitter.com/travelease"
    }
  },
  {
    "_id": "company_7",
    "companyName": "UrbanDesign Studio",
    "foundedYear": 2008,
    "industry": "Architecture",
    "employees": 60,
    "headquarters": {
      "address": "123 Creative Street",
      "city": "Amsterdam",
      "country": "Netherlands"
    },
    "contact": {
      "email": "contact@urbandesign.com",
      "phone": "+31 20 123 4567",
      "website": "https://www.urbandesign.com"
    },
    "services": ["Urban Planning", "Interior Design", "Sustainable Architecture"],
    "socialMedia": {
      "linkedin": "https://www.linkedin.com/company/urbandesign",
      "twitter": "https://twitter.com/urbandesign"
    }
  },
  {
    "_id": "company_8",
    "companyName": "FinSecure Partners",
    "foundedYear": 2005,
    "industry": "Financial Services",
    "employees": 500,
    "headquarters": {
      "address": "789 Finance Plaza",
      "city": "Singapore",
      "country": "Singapore"
    },
    "contact": {
      "email": "info@finsecure.com",
      "phone": "+65 6234 5678",
      "website": "https://www.finsecure.com"
    },
    "services": [
      "Investment Advisory",
      "Insurance Solutions",
      "Wealth Management"
    ],
    "socialMedia": {
      "linkedin": "https://www.linkedin.com/company/finsecure",
      "twitter": "https://twitter.com/finsecure"
    }
  }
]

```