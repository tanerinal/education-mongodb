## Current data

**Command**
```json
show.dbs
```
**Output**
```java
admin       40.00 KiB
config      60.00 KiB
flights     84.00 KiB
hospital    72.00 KiB
local       72.00 KiB
northwind    8.00 KiB
passangers  56.00 KiB
shop        72.00 KiB
shopping    40.00 KiB
```

## Deleting a Collection

**Command**
```json
use flights
db.flightsData.drop()
```
**Output**
```json
switched to db flights
true
```

## Dropping a Database

**Command**
```json
use flights
db.dropDatabase()
```
**Output**
```json
{ ok: 1, dropped: 'flights' }
```
## Current data

**Command**
```json
show.dbs
```
**Output**
```java
admin       40.00 KiB
config      60.00 KiB
hospital    72.00 KiB
local       72.00 KiB
northwind    8.00 KiB
passangers  56.00 KiB
shop        72.00 KiB
shopping    40.00 KiB
```