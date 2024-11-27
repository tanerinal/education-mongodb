## Starting the mongoDB Server and Showing the  Databases
- To startup the MongoDb server type `mongod` to command prompt. It will start the MongoDb server in port 27017

- Do not close or end the command prompt but open a new one and type `mongosh` to start new MongoDB Shell prompt.

- To see the databases type `show dbs`. Output will be like;
![Show Dbs SS](resources\images\showdbs.png)

## Creating a new Database and a Collection
**Steps:**

1. Create a database called flights, type
```javascript
use flights
```

2. See the databases, type;
```javascript
show dbs
```
![Show Dbs SS](resources\images\cretaeDatabaseFlights.png)
> There is no database called **"flights"** since we haven't insert data into it.

## Insert a Data (Document) Into a Collection
Insert a single flight data, type;
```json
db.flightsData.insertOne({
    "departureAirport": "MUC",
    "arrivalAirport": "SFO",
    "aircraft": "Airbus A380",
    "distance": 12000,
    "intercontinental": true
  })
```
![SS](resources\images\insertOneFlightData.png)

Query the data, type;
```json
db.flightsData.find()
```
![SS](resources\images\queryFlieghtsData.png)

There is no schema either; 
```json
db.flightsData.insertOne({
    "departureAirport": "IST",
    "arrivalAirport": "AYT"
  })
```

And we can use our own ID;
```json
db.flightsData.insertOne({
    "departureAirport": "SAW",
    "arrivalAirport": "AYT",
    "_id": "my_id"
  })
```

But, it should be unique;
```json
db.flightsData.insertOne({
    "departureAirport": "SAW",
    "arrivalAirport": "AYT",
    "_id": "my_id
  })
```
![SS](resources\images\insertOneWithCustomId.png)

Here is the records so far;
```json
db.flightsData.find()
```
![SS](resources\images\insertOneWithCustomIdInsertedOnes.png)