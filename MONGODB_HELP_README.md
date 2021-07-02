# $ mongo
```
MongoDB shell version: 2.2.3
connecting to: test
```
# 1.connect to the "admin" database.
```
> use admin             		
switched to db admin			
```

# 2. add a user "admin" to the admin database. 
```
> db.addUser("admin","password")	
{
	"user" : "admin",
	"readOnly" : false,
	"pwd" : "90f500568434c37b61c8c1ce05fdf3ae",
	"_id" : ObjectId("513af8cac115e7a6b4bcceb9")
}
addUser succeeded, but cannot wait for replication since we no longer have auth
```

# 3. connect to the "testdb" database. 
```
> use testdb				
switched to db testdb
```

# 4. now, read and write need authentication
```
> show collections			
Sat Mar  9 16:54:57 uncaught exception: error: {
	"$err" : "unauthorized db:testdb ns:testdb.system.namespaces lock type:0 client:127.0.0.1",
	"code" : 10057
}
```
# 5. connect back to the "admin" database.
```
> use admin				
```

# 6. performs authentication, 1 means succeed, 0 means failed
```
switched to db admin
> db.auth("admin","password")		
1
```

# 7. connect to the "testdb" database.
```
> use testdb				
switched to db testdb
```

# 8. no problem, it shows all collections
```
> show collections			
system.indexes
user
```

# 9. add another user "testdb" to the "testdb" database.
```
> db.addUser("testdb","password")       
{
	"user" : "testdb",
	"readOnly" : false,
	"pwd" : "b9ff75cbf18bd98d8554efec12c72090",
	"_id" : ObjectId("513af934c115e7a6b4bcceba")
}
> show collections
system.indexes
```

# 10. All users' data are stored in this system.users collection.
```
system.users				
user
> db.system.users.find()
{ "_id" : ObjectId("513af934c115e7a6b4bcceba"), "user" : "testdb", "readOnly" : false, "pwd" : "b9ff75cbf18bd98d8554efec12c72090" }
>
```

# 11.clearing screen in windows mongo shell
```
>cls
```

# 12.display all the dbs in the mongodb
```
>show dbs
```

# 13.swtiching the db
```
>use <dbname>
```

# 14.display all the collection 
```
>show collections
```

# 15.switched to db admin
```
>use admin
```

# 16.add a user "admin" to the admin database. 
```
>db.addUser("admin","pwd")
```

# 17.displaying all the method related to db
```
>db.help()
```

# 18.displaying all the method realted to collection
```
>db.<collection>.help()	
```

# 19.selecting all the data from the document
```
>db.<collection>.find().pretty();
```
# 19.selecting only mathcing data from the document
```
>db.<collection>.find({'key':'value'}).pretty();
```
# 20.type of collection 
```
1.assocative array {'key2':'value1','key2':'value2'}
2.list ['val1','val2','val3']
```
# 21.inserting the data into mongo db collection
```
>db.<collection>.insert({'key2':'value1','key2':'value2'});
```

# 22.same document can hold any sturcture
```
>db.<collection>.insert({'key2':'value1','key2':'value2','key3':'value3'});
```
# 23.same document can hold associative and list object together 
```
>db.<collection>.insert({'key2':'value1','key2':'value2','key3':'value3','key4':['val1','val2','val3']});
```