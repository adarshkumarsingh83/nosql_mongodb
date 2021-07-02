### starting mongo server 
```
* c:/adarsh_k>mongod.exe --config D:\MONGO_DATABASE\mongodb\mongo.config
```

### start mongo shell
```
* c:/>Adarsh_k>mongo
```

### clearing screen in windows mongo shell
```
>cls
```

### checking the version of mongoserver
```
>db.version() 
```

### display all the dbs in the mongodb server
```
>show dbs
```

### swtiching to particular db
```
>use <dbname>
```

### display all the collection 
```
>show collections
```

### switched to db admin
```
>use admin
```

### add a user "admin" to the admin database. 
```
>db.addUser("admin","pwd")
```

### removing a user form database
```
>db.removeUser("admin")
```

### displaying all the method related to db
```
>db.help()
```

### displaying all the method realted to collection
```
>db.<collection>.help()	
```

### displaying all the method realted help 
```
>db.<collection>.<methodName>().help()
```

### selecting all the data from the document
```
>db.<collection>.find().pretty();
```

### selecting only mathcing data from the document
```
>db.<collection>.find({'key':'value'}).pretty();
>db.<collection>.find({'_id':'1'}).pretty();
```

### type of collection 
```
1.assocative array {'key2':'value1','key2':'value2'}
2.list ['val1','val2','val3']
```
# inseting all types
### integer value
```
db.<collection>.insert( {x : 3});
```
### float value
```
db.<collection>.insert( {x : 2.9} );
```
### date value
```
db.<collection>.insert( {x : new Date()} );
```
### boolean value
```
db.<collection>.insert( {x : true } );
```
### max key range
```
db.<collection>.insert( {x : MaxKey } )
```
### min key range
```
db.<collection>.insert( {x : MinKey } )
```

### inserting the data into mongo db collection
```
>db.<collection>.insert({'key1':'value1','key2':'value2'});
>db.<collection>.insert({'_id':'1','key1':'value1','key2':'value2'});
```

### same document can hold any sturcture
```
>db.<collection>.insert({'key2':'value1','key2':'value2','key3':'value3'});
>db.<collection>.insert({'_id':'1','key2':'value1','key2':'value2','key3':'value3'});
```

### same document can hold associative and list object together 
```
>db.<collection>.insert({'key2':'value1','key2':'value2','key3':'value3','key4':['val1','val2','val3']});
>db.<collection>.insert({'_id':'1','key2':'value1','key2':'value2','key3':'value3','key4':['val1','val2','val3']});
```

### inserting data of associative array with help of varable 
```
>i={'key1':'value1','key2':'value2'}
>db.<collection>.insert(i);
>i={'_id':'1','key1':'value1','key2':'value2'}
>db.<collection>.insert(i);
```

### inserting data of nesting collection with help of varable 
```
>j={'key2':'value1','key2':'value2','key3':'value3','key4':['val1','val2','val3']}
>db.<collection>.insert(j);
>j={'_id':'1','key2':'value1','key2':'value2','key3':'value3','key4':['val1','val2','val3']}
>db.<collection>.insert(j);
```

### inseting data useing loop
```
>for (var i = 1; i <= 25; i++) db.<collection>.insert( { x : i } )
>for (var i = 1; i <= 25; i++) db.<collection>.insert( { _id : i , 'key' : 'value'+i } )
```

### selecting data in variable and displaing using while loop
```
>var data = db.<collection>.find()
>while ( data.hasNext() ) printjson( data.next() ) 
```

### selecting data in variable and displaing using foreach loop
```
>var data = db.<collection>.find()
>data.forEach( function(myDoc) { 
		print( "id: " + myDoc._id ); 
	} 
 );
>data.forEach( function(myDoc) {
       printjson( myDoc); 
	} 
 );
```

### selecting data in variable and displaing using for loop
```
>var data = db.<collection>.find();
>for(i=0;i<data.count();i++){
  printjson(data[i]);
}
```


### inserting the data with the help of function
```
>function insertData(dbName, colName, num) {
	var col = db.getSiblingDB(dbName).getCollection(colName);
		for (i = 0; i < num; i++) {
			col.insert({ _id : i , 'key' : 'value'+i });
		}
	print(col.count());
}
```

### calling the funtion for inserttion
```
>insertData("test", "testData", 400)
```

---


### inserting the data with the help of function by passing json
```
>function insertJsonData(databaseName,colletionName,json){
  var collectionObject = db.getSiblingDB(databaseName).getCollection(colletionName);
  collectionObject.insert(json);
}
```
### call the function 
```
>insertJsonData("mydb","mydb",{'_id':1000,'key':'value1000'});
````

---

### selection of the documents using function with for loop
```
>function displayDataForLoop(databaseName, collectionName){  
  var collectionObject = db.getSiblingDB(databaseName).getCollection(collectionName);
  var myCursor=collectionObject.find();
	for(i=0;i<myCursor.count();i++){
		printjson(myCursor[i]);
	}
}
```

### calling the fucntion for selection
```
>displayDataForLoop("mydb","mydb");
```

---

### selection of the documents using function with while loop
```
>function displayDataWhileLoop(databaseName, collectionName){  
  var collectionObject = db.getSiblingDB(databaseName).getCollection(collectionName);
  var myCursor=collectionObject.find();
  while(myCursor.hasNext()){    
	printjson(myCursor.next());
  }
}
```
### calling the fucntion for selection
```
>displayData("mydb","mydb");
```

---

### selection of the documents using function with forEach loop
```
>function displayDataForEachLoop(databaseName, collectionName){  
  var collectionObject = db.getSiblingDB(databaseName).getCollection(collectionName);
  var myCursor=collectionObject.find();  
  myCursor.forEach( function(collectionName) {
       printjson( collectionName); 
	} 
 );
}
```
### calling the fucntion for selection
```
>displayDataForEachLoop("mydb","mydb");
```

---

### explaing the colleciton
```
>db.<collection>.find().hint().explain()
```

### dropping database
```
>show dbs
>use <db>
>db.dropDatabase()
```

### deleting all the document from the collection
```
>db.<collection>.remove()
```

### deleting only particular document in the colleciton
```
>db.<collection>.remove({'_id':idvalue})
```

### updateing all the document for the collections
```
>db.<collection>.update()
```

### updating particular document in the collections
```
>db.<collection>.update({_id:idvalue},{$set:{'key':'value'}})
```

### updaing particular doucment and removing a field 
```
>db.<collection>.update({_id:idvalue},{$unset:{'akey':'akeyvalue'}})
```

### updating an array
```
>db.<collection>.insert({'_id':'value','key':'value','akey':['value1','value2']})
>db.<collection>.update({'key':'value'},{'key':'value','akey':['val1','val2','val3']})
>db.<collection>.update({'_id':'value','key':'value'},{'key':'value','akey':['value1','value2','value3']},{ upsert: true })
```

### save ObjectId required only id with 24 digit
```
>db.<collection>.save('_id':ObjectId("507c4e138fada716c89d0014"),'key','value','akey':['v1','v2'])
>db.<collection>.find({'key':'value'})
```

### inserting date
```
> db.<collection>.insert({'_id':'value','key':'value','date':new Date('13/09/1983')})
> db.<collection>.find({'dob':new Date('13/09/1983')})
{ "_id" : "11", "key" : "value11", "dob" : ISODate("0NaN-NaN-NaNTNaN:NaN:NaNZ") }
```

---

### bulk inserttion
```
> db.<collection>.insert( [ {'_id':'value1','key':'value1'},{'_id':'value2','key':'value2'},{'_id':'value3','key':'value3'} ] )
>db.<collection>.find( { $and : [ {'_id' : { $gt : 'minValue1' } }, { '_id' : { $lt : 'maxValue2' } } ] } )
```


### renaming the column name
```
>db.<collection>.update( { '_id':'value'} , { $rename: { 'old_col_name1' : 'old_col_value' , 'new_col_name1' : 'new_col_value1' } } )
```

### $exists operator
```
>db.<collection>.find( { $nor: [ {'key' : { $exists : 'value1' } } ]  } ) 
```

### $regex operator
```
>db.<collection>.find( )
```

### $where operator
```
>db.<collection>.find( { $where: { 'this._id == 10'} } )
```
### $match operator
```
>db.<collection>.aggregate( { $match : { '_id' : 1 } } );
```
### $group operator
```
>db.<collection>.aggregate( { $match : { _id : { $gt :10 , $lte :100 } } } , { $group: { _id: null, count: { $sum: 1 } } } );
```

----
##   logical operator operator example
---

### $or operator
```
>db.<collection>.find( { '_id' : { $gt : value} , $or: [ { 'key' : 'value' } ] } )
```

### $and operator
```
>db.<collection>.find( { $and : [ {'_id' : 'value'} , { 'key' : 'value'} ] } )
db.<collection>.find( { $and : [ {'_id': { $gt:valueMin } },{ '_id':{ $lt:valueMax } } ] } )
```

### $not operator
```
>db.<collection>.find( { '_id':{ $not : { $gt : maxlimit }} } )
>db.<collection>.find( { '_id':{ $not : { $in: [1,2,3,4,5,6,7] }} } )
```
### $nor operator
```
>db.<collection>.find( { $nor : [ {'_id': { $gt : 10 } } , { '_id' : { $lt : 20 } } ] } )
```

---
## Comparison Query Operators
---

### equal 
```
>db.<collection>.find( { '_id' : 'value'  } )
```
### $ne operator
```
>db.<collection>.find( { '_id' : { $ne : value } } )
```
### $gt operator
```
>db.<collection>.find( { '_id' : { $gt : 0 } } )
```
### $lt operator
```
>db.<collection>.find( { '_id' : { $lt : value } } )
```
### $gte operator
```
>db.<collection>.find( { '_id': { $gte: 90 } } )
```
### lte operator
```
>db.<collection>.find( { '_id' : { $lte: 20 } } )
```
### $in operator
```
>db.<collection>.find( { '_id' : { $in : [ 1 , 2 , 3 ] } } )
>db.<collection>.find( { 'key' : { $in : [ 'val1' , 'val2' , 'val3' ] } } )
```

### $nin operator
```
>db.<collection>.find( { '_id' : { $nin: [ 1, 2, 3 ] } } )
```
### $all operator
```
>db.<collection>.find( { 'key' : { $all: [ 1,2,3,4,5] } } ) 
```

## Database Commands
### count
```-
> db.runCommand( { count : '<collectionName>'} )
{ "n" : 15, "ok" : 1 }
> db.runCommand( { count : 'mydb' ,query : { '_id': {$gt : '100' } } , skip : 1 } )
{ "n" : 4, "ok" : 1 }
> db.runCommand( { count : 'mydb' ,query : { '_id': {$gt : '100' } } ,limit : 2 , skip : 1 } )
{ "n" : 2, "ok" : 1 }
```

## Element
### $exists 
```
>db.<collection>.find( { 'key': { $exists: 'value'} } )
->display only those doc where key is one columns 
```

### $mod
```
> db.mydb.find( { _id: { $mod: [ 2, 0 ] } } )
->display only those doc where id is even
```

### $type
```
db.inventory.find( { 'key': { $type : typeValue } } )
typeValue:=> [ Double 1, String	2, Object 3, Array 4, Binary data 5, Undefined (deprecated)	6, Object id 7
,Boolean 8, Date 9, Null 10, Regular Expression	11, JavaScript 13, Symbol 14, JavaScript (with scope) 15 
 ,32-bit integer	16, Timestamp 17, 64-bit integer 18, Min key 255, Max key 127]
```
### Javascript
```----
### $where
> db.mydb.insert( { '_id':'300','key':'value300','subdoc':['val1','val2','val3']} )
> db.mydb.find( { $where : "Array.isArray(this.subdoc)"} )
{ "_id" : "300", "key" : "value300", "subdoc" : [  "val1",  "val2",  "val3" ] }
```

### $regex
```
> db.mydb.find( { 'key':{ $regex : /^value.*$/ } } )
```

### $elemMatch
```
>db.mydb.insert({'_id':500,'mydata':{'key','val1','key1':'val2'} } )
> db.mydb.find( { 'mydata':{ $elemMatch:{ 'key':'val1'} } } )
```

### $size
```
> db.mydb.find( { 'mydata': { $size: 2 } } );
```

---
# creating user
---

```
> use testtdb
switched to db testtdb
> db.createUser( { user:'adarsh' , pwd:'radha' , roles:['readWrite','dbAdmin'] } )
{
        "user" : "adarsh",
        "pwd" : "34ab4ce912add4b5eaabb6d7f7f62815",
        "roles" : [
                "readWrite",
                "dbAdmin"
        ],
        "_id" : ObjectId("52007c6103450349b6db8f8c")
}
```



### finding user
```
> db.system.users.find()
{ "_id" : ObjectId("52007d3103450349b6db8f8d"), "user" : "adarsh", "pwd" : "34ab4ce912add4b5eaabb6d7f7f62815", "roles" : [  "readWrite",  "dbAdmin" ] }
```

### removing user
```
> db.removeUser('adarsh')
```

### chaning pwd
```
>db = db.getSiblingDB('<dbname>')
>db.changeUserPassword('<userName>', "SOhSS3TbYhxusooLiW8ypJPxmt1oOfL")
```

---

## Export from mongodb
```
>mongoexport --collection <collection_name> --out <file_name>.json
>mongoexport --db <db_name> --collection <collection_name> --query '{"field": 1}'
>mongoexport --db <db_name> --collection <collection_name> --dbpath <path of the mongo db []>
>mongoexport --host <hostname> --port <portno> --username <username> --password <password> --collection <collection_name> --file <file_name>.json
````

## Import from mongodb
```
>mongoimport --collection collection --file collection.json
>mongoimport --db <db_name> --collection <collection_name> --stopOnError --dbpath <mongodb path>
>mongoimport --db <db_name> --collection <collection_name> --type <json|csv|tsv> --file <filepath/filename>.csv
>mongoimport --host <hostname> --port <portno> --username <username> --password <password> --collection <collection_name> --db <dbname> --file <filepath/filename>.json
```

### help
```
> db.help()
DB methods:
        db.addUser(userDocument)
        db.adminCommand(nameOrDocument) - switches to 'admin' db, and runs command [ just calls db.runCommand(...) ]
        db.auth(username, password)
        db.cloneDatabase(fromhost)
        db.commandHelp(name) returns the help for the command
        db.copyDatabase(fromdb, todb, fromhost)
        db.createCollection(name, { size : ..., capped : ..., max : ... } )
        db.currentOp() displays currently executing operations in the db
        db.dropDatabase() ### dorpping database
        db.eval(func, args) run code server-side
        db.fsyncLock() flush data to disk and lock server for backups
        db.fsyncUnlock() unlocks server following a db.fsyncLock()
        db.getCollection(cname) same as db['cname'] or db.cname
        db.getCollectionNames()
        db.getLastError() - just returns the err msg string
        db.getLastErrorObj() - return full status object
        db.getMongo() get the server connection object
        db.getMongo().setSlaveOk() allow queries on a replication slave server
        db.getName() ###  display the name of the database
        db.getPrevError()
        db.getProfilingLevel() - deprecated
        db.getProfilingStatus() - returns if profiling is on and slow threshold
        db.getReplicationInfo()
        db.getSiblingDB(name) get the db at the same server as this one
        db.hostInfo() get details about the server's host
        db.isMaster() check replica primary status
        db.killOp(opid) kills the current operation in the db
        db.listCommands() lists all the db commands
        db.loadServerScripts() loads all the scripts in db.system.js
        db.logout()
        db.printCollectionStats()
        db.printReplicationInfo()
        db.printShardingStatus()
        db.printSlaveReplicationInfo()
        db.removeUser(username)
        db.repairDatabase()
        db.resetError()
        db.runCommand(cmdObj) run a database command.  if cmdObj is a string, turns it into { cmdObj: 1 }
        db.serverStatus()
        db.setProfilingLevel(level,<slowms>) 0=off 1=slow 2=all
        db.setVerboseShell(flag) display extra information in shell output
        db.shutdownServer()
        db.stats()
        db.version() current version of the server
```

```
> db.<collection>.help()
DBCollection help
        db.<collection>.find().help() - show DBCursor help
        db.<collection>.count()
        db.<collection>.copyTo(newColl) - duplicates collection by copying all documents to newColl; no indexes are copied.
        db.<collection>.convertToCapped(maxBytes) - calls {convertToCapped:'<collection>', size:maxBytes}} command
        db.<collection>.dataSize()
        db.<collection>.distinct( key ) - e.g. db.<collection>.distinct( 'x' )
        db.<collection>.drop() drop the collection
        db.<collection>.dropIndex(index) - e.g. db.<collection>.dropIndex( "indexName" ) or db.<collection>.dropIndex( { "indexKey" : 1 } )
        db.<collection>.dropIndexes()
        db.<collection>.ensureIndex(keypattern[,options]) - options is an object with these possible fields:name, unique, dropDups
        db.<collection>.reIndex()
        db.<collection>.find([query],[fields]) - query is an optional query filter. fields is optional set of fields to return.
                                                      e.g. db.<collection>.find( {x:77} , {name:1, x:1} )
        db.<collection>.find(...).count()
        db.<collection>.find(...).limit(n)
        db.<collection>.find(...).skip(n)
        db.<collection>.find(...).sort(...)
        db.<collection>.findOne([query])
        db.<collection>.findAndModify( { update : ... , remove : bool [, query: {}, sort: {}, 'new': false]} )
        db.<collection>.getDB() get DB object associated with collection
        db.<collection>.getIndexes()
        db.<collection>.group( { key : ..., initial: ..., reduce : ...[, cond: ...] } )
        db.<collection>.insert(obj)
        db.<collection>.mapReduce( mapFunction , reduceFunction , <optional params> )
        db.<collection>.remove(query)
        db.<collection>.renameCollection( newName , <dropTarget> ) renames the collection.
        db.<collection>.runCommand( name , <options> ) runs a db command with the given name where the first param is the collection name
        db.<collection>.save(obj)
        db.<collection>.stats()
        db.<collection>.storageSize() - includes free space allocated to this collection
        db.<collection>.totalIndexSize() - size in bytes of all the indexes
        db.<collection>.totalSize() - storage allocated for all data and indexes
        db.<collection>.update(query, object[, upsert_bool, multi_bool]) - instead of two flags, you can pass an object with fields: upsert, multi
        db.<collection>.validate( <full> ) - SLOW
        db.<collection>.getShardVersion() - only for use with sharding
        db.<collection>.getShardDistribution() - prints statistics about data distribution in the cluster
        db.<collection>.getSplitKeysForChunks( <maxChunkSize> ) - calculates split points over all chunks and returns splitter function
````


## var cursor=db.<collection>.find()
```
cursor.addOption()			Adds special wire protocol flags that modify the behavior of the query.�
cursor.batchSize()			Controls the number of documents MongoDB will return to the client in a single network message.
cursor.count()				Returns a count of the documents in a cursor.
cursor.explain()			Reports on the query execution plan, including index use, for a cursor.
cursor.forEach()			Applies a JavaScript function for every document in a cursor.
cursor.hasNext()			Returns true if the cursor has documents and can be iterated.
cursor.hint()				Forces MongoDB to use a specific index for a query.
cursor.limit()				Constrains the size of a cursor�s result set.
cursor.map()				Applies a function to each document in a cursor and collects the return values in an array.
cursor.max()				Specifies an exclusive upper index bound for a cursor. For use with cursor.hint()
cursor.min()				Specifies an inclusive lower index bound for a cursor. For use with cursor.hint()
cursor.next()				Returns the next document in a cursor.
cursor.objsLeftInBatch()	Returns the number of documents left in the current cursor batch.
cursor.readPref()			Specifies a read preference to a cursor to control how the client directs queries to a replica set.
cursor.showDiskLoc()		Returns a cursor with modified documents that include the on-disk location of the document.
cursor.size()				Returns a count of the documents in the cursor after applying skip() and limit() methods.
cursor.skip()				Returns a cursor that begins returning results only after passing or skipping a number of documents.
cursor.snapshot()			Forces the cursor to use the index on the _id field. Ensures that the cursor returns each document, with regards to the value of the _id field, only once.
cursor.sort()				Returns results ordered according to a sort specification.
cursor.toArray()			Returns an array that contains all documents returned by the cursor.
```


## Connection Methods
```
Name								Description
Mongo.getDB()						Returns a database object.
Mongo.getReadPrefMode()				Returns the current read preference mode for the MongoDB connection.
Mongo.getReadPrefTagSet()			Returns the read preference tag set for the MongoDB connection.
Mongo.setReadPref()					Sets the read preference for the MongoDB connection.
Mongo.setSlaveOk()					Allows operations on the current connection to read from secondary members.
Mongo()								Creates a new connection object.
connect()							Connects to a MongoDB instance and to a specified database on that instance.
```
