# http://www.education.10gen.com

# Mongo db or Document database
-----------------------------------


* JSON=json java scropt object notation 

* BSON= BINEARY SCRIPT OBJECT NOTATION

* mongo db store json and its has the lang as the java script.
Collection = its the group of the attributes of the entities
data is store in the key value pair as type of the json

* Data is store in json inside the Collection
and collection is stored in  the document.

* PER DOC THIER IS LIMIT IS 16MB FOR SIZE 

* Transaction is not support in mongo db 
but in same doc it ensure that in one doc 
it gives the assurty of the data consistency 
but in the multiple doc it doesn't ensure the 
data consistency 

* joins aren't support in the mongo db.


* CURD OPERATION ON SHELL
* INSERT 
* FIND 
* UPDATE
* REMOVE

## NOSQL>
### WITHOUT THE ID FOR THE COLLLECTION 
```
DOC={"NAME":"ADARSH","AGE":25}
DB.PERSON.INSERT(DOC)
DB.PERSON.FIND()
```
### WITH THE ID FOR THE COLLLECTION 
```
DOC={_ID:OBJECTID("ADFASDFDREQ6424"),"NAME":"ADARSH","AGE":25}
DB.PERSON.INSERT(DOC)
DB.PERSON.FIND()
```
```
1.support rich doc
2.no constraint
3.no joins
4.no diclared schema
```
```
demon process 
Mongod
```
```
user <databsename>
show collecitons
show db
db.items.stat
db.items.find().count()
```

