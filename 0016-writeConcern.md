> `writeConcern` assures the data written on database

## Inserting a Document with Default writeConcern Behaviour

**Command**
```java
use social
db.hobbies.insertOne({"_id": "cycling", "name": "Cycling"})  //Equals to db.hobbies.insertOne({"_id": "cycling", "name": "Cycling"}, {writeConcern: {w:1, j:false}})
```
**Output**
```json
switched to db social
{ acknowledged: true, insertedId: 'cycling' }
```

```json
{
  writeConcern: {
    w:1,      // wait ack for database write
    j:false   // do not write insert operation to journal file
  }
}
  ```


### Inserting a Document with Fastest writeConcern Behaviour

**Command**
```json
db.hobbies.insertOne(
  {"_id": "skyDiving", "name": "Sky Diving"}, 
  {writeConcern: {w:0, j:false}})
```
**Output**
```json
{ acknowledged: false, insertedId: 'skyDiving' }
```

> Since `acknowledged: false`, we have no guarantee of the data being written into the collection

### Inserting a Document with Most Secure writeConcern Behaviour

**Command**
```json
db.hobbies.insertOne(
  {"_id": "music", "name": "Music"}, 
  {writeConcern: {w:1, j:true}})
```
**Output**
```json
{ acknowledged: true, insertedId: 'music' }
```
> Since `acknowledged: true`, we get the guarantee of the data being written into the collection. With `j:true` option, the write operation logged into the journal and if there is a server crash, it will recover the write operation due to the journal records.