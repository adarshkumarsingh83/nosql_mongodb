###  To Download the docker image of mongodb 
* $ docker pull mongo


###   executing the docker image 
* $ docker run --name espark-mongodb mongo

###   on specific port 
* $ docker run -d -p 27017-27019:27017-27019 --name espark-mongodb mongo

###  To open interactive mongo bash shell 
* $ docker exec -it espark-mongodb bash

###  To get the mongo shell 
* $ mongo

###  To Show the db present
* $ show dbs

###  To Create a new db
* $ use <database_name>
* $ use espark_db

###  To know the current db 
* $ db

###  To delete the db
* $ db.dropDatabase()

###  To create a collection without inserting data 
* $ db.createCollection(name, options)
  ```
  ex db.createCollection("user")
  ```

###  To delete the collection 
* $ db.collection_name.drop()
```
ex: db.user.drop()
```

###  To Insert a data into the collection.
* $ db.collection_name.insert()
```
ex: db.user.insert({name: "Adarsh kumar", age: 30})
ex 
var userList =
 [
    {
	"name" : "adarsh",
      "age": 33
    },
    {
	"name" : "radha",
      "age": 30
    }
];
```
* $ db.user.insert(userList);

###  To list the data from collection
* $ db.collection_name.find()
* $ db.collection_name.find({"field_name":{$gt:criteria_value}}).pretty()
```
ex db.user.find()
ex db.user.find().forEach(printjson)
ex db.user.find().pretty()
ex db.user.find({name : "adarsh"}).pretty()
```

## Greater Than Criteria:
* $ db.collection_name.find({"field_name":{$gt:criteria_value}}).pretty()
```
ex db.user.find({"age":{$gt:32}}).pretty()
```

## Greater than equals Criteria:
* $ db.collection_name.find({"field_name":{$gte:criteria_value}}).pretty()
```
ex db.collection_name.find({"field_name":{$gte:criteria_value}}).pretty()
```

## Less than Criteria:
* $ db.collection_name.find({"field_name":{$lt:criteria_value}}).pretty()
```
ex db.user.find({"age":{$lt:32}}).pretty()
```

## Less than equals Criteria:
* $ db.collection_name.find({"field_name":{$lte:criteria_value}}).pretty()
```
ex db.collection_name.find({"field_name":{$lte:criteria_value}}).pretty()
```

## Not Equals Criteria:
* $ db.collection_name.find({"field_name":{$ne:criteria_value}}).pretty()
```
ex db.user.find({"id":{$ne:1002}}).pretty()
```

###  To fetch data with and show fields on conditions 
* $ db.collection_name.find({},{field_key:1 or 0})
```
1 = show in result 
0 = hide in result
ex db.user.find({}, {"_id": 0, "name": 0, "student_age": 1})
```

###   limit() method in MongoDB
* $ db.collection_name.find().limit(number_of_documents)
```
ex db.user.find({id : {$gt:202}}).limit(1).pretty()
```

###   Skip() Method to skip the record of the number in result
```
ex db.user.find({id : {$gt:2020}}).limit(1).skip(1).pretty()
```

###   Sorting Documents using sort()
* $ db.collecttion_name.find().sort({field_key:1 or -1})
```
1 is for ascending order 
-1 is for descending order. 
The default value is 1.

ex db.user.find({}, {"id": 1, _id:0}).sort({"id": -1})
ex db.user.find({}, {"id": 1, _id:0}).sort({})
```

###  To list the collections
* $ show collections


## Updating Document using update() 
* $ db.collection_name.update(criteria, update_data)
```
ex db.user.update({"name":"adarsh"},{$set:{"name":"adarsh kumar"}})
```

## update multiple documents with the update()
```
ex db.user.update({"name":"adarsh"},{$set:{"name":"adarsh kumar"}},{multi:true})
```

## To Update the data by using id 
* $ db.user.find({"name": "adarsh"}).pretty()
```
{
        "_id" : ObjectId("59bd2e73ce524b733f14dd65"),
        "name" : "adarsh",
        "age" : 32
}
```
* $ db.user.save({"_id" : ObjectId("59bd2e73ce524b733f14dd65"), "name":"adarsh kumar", "age": 32})


## Deleting Document using remove() 
* $ db.collection_name.remove(delete_criteria)
```
ex db.user.remove({"id": 100})
```

###  For single or multiple 
* $ db.collection_name.remove(delete_criteria, justOne)
```
ex db.user.remove({"age": 30},5)
```

###  To Remove all the collections in db
* $ db.collection_name.remove({})

## create index in MongoDB
* $ db.collection_name.createIndex({field_name: 1 or -1})
```
The value 1 is for ascending order and -1 is for descending order.
ex db.user.createIndex({name: 1})
```

##  Finding the indexes in a collection
* $ db.collection_name.getIndexes()

##  Drop indexes in a collection
* $ db.collection_name.dropIndex({index_name: 1})

## Dropping all the indexes:
* $ db.collection_name.dropIndexes()



