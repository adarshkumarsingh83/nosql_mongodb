
# PROJECTION

---

* $lt,$gt,$lte,$gte,$in,$nin,$all

---
```
>db.<collection>.find( <query>, <projection> )
>db.<collection>.find( { 'key' : 'value1', '_id': { $lt: '10' } }

>db.<collection>.findOne( <query>, <projection> )
>db.<collection>.findOne( { 'key' : 'value1', '_id': { $gt: '0' } }
```

--- 
EXAMPLE 
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

## Nested collection search
```
>db.mydb.insert( {'_id':'200','key':'value200','subdoc':{'k1':'sk1','k2':'sk2'} } )
> db.mydb.find( { 'subdoc.k1':'sk1'} )
{ "_id" : "200", "key" : "value200", "subdoc" : { "k1" : "sk1", "k2" : "sk2" } }
```

