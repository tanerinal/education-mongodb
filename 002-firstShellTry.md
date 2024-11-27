## Starting mongo Shell
Open Command Prompt and type `mongosh`
![Console Screenshot](resources\images\mongosh.png)

## Switching to a Database
- Type `use shopping` to switch to shopping database (will create)
![Use Screenshot](resources\images\use.png)

## Inserting One Record
```json
db.products.insertOne({
    name: "A Book",
    price: 29.33
})
```
![insertOne Screenshot](resources\images\insertOne.png)

## Querying Records
```json
db.products.find().pretty()
```
![insertOne Screenshot](resources\images\quryingRecords.png)