# mongoDB
first configured mongoDB server
created --dbpath 
run mongod.exe in command prompt


then run mongo server by typing mongo in command prompt

created database using command (use databaseName)


delete database using command (db.databaseName.drop())

create collection using command (db.collectionName(name,option)

delete collection using command (db.collectionName.drop())

insert document using command (db.collectionName.insert({document})

for eg:db.details.insert({name:"abhishek singh",age:"21",address:"jogeshwari",mobile_no:"9029100717"})

view document using command (db.collectionName.find())

to view the document in formatted style use command (db.collectionName.find().pretty())

update document using command (db.colectionName.update(selection_criteria,update_data)

for eg:db.details.update({name:"abhishek singh"},{$set:{name:"abhishek vikram singh"}})

it will update abhishek singh to abhishek vikram singh

delete document using command (db.collectionName.delete(deletion_criteria)


create user using command(db.createUser())

for eg:db.createUser({user:"Abhi",pwd:"india1994",role:["readwrite","dbaAdmin"]})


$ mongo
MongoDB shell version v3.4.6
connecting to: mongodb://127.0.0.1:27017
MongoDB server version: 3.4.6
use mycustomers
switched to db mycustomers
db.createUser({
user:"abhishek",
pwd:"india1994",
roles:["readWrite","dbAdmin"]
})
Successfully added user: { "user" : "abhishek", "roles" : [ "readWrite", "dbAdmin" ] }
db.createCollection("customers")
{ "ok" : 1 }
show collections
customers
db.customers.insert([{first_name:"abhishek", last_name:"singh", gender:"male"},{first_name:"priya", last_name:"singh", gender:"female"}])
BulkWriteResult({
        "writeErrors" : [ ],
        "writeConcernErrors" : [ ],
        "nInserted" : 2,
        "nUpserted" : 0,
        "nMatched" : 0,
        "nModified" : 0,
        "nRemoved" : 0,
        "upserted" : [ ]
})
db.customers.find()
{ "_id" : ObjectId("59704d3077e33dfa6c1f987e"), "first_name" : "abhishek", "last_name" : "singh", "gender" : "male" }
{ "_id" : ObjectId("59704d3077e33dfa6c1f987f"), "first_name" : "priya", "last_name" : "singh", "gender" : "female" }
db.customers.insert([{first_name:"Raj", last_name:"Trivedi", gender:"male"},{first_name:"Sheela", last_name:"ghose", gender:"female"}])
BulkWriteResult({
        "writeErrors" : [ ],
        "writeConcernErrors" : [ ],
        "nInserted" : 2,
        "nUpserted" : 0,
        "nMatched" : 0,
        "nModified" : 0,
        "nRemoved" : 0,
        "upserted" : [ ]
})
db.customers.find().pretty()
{
        "_id" : ObjectId("59704d3077e33dfa6c1f987e"),
        "first_name" : "abhishek",
        "last_name" : "singh",
        "gender" : "male"
}
{
        "_id" : ObjectId("59704d3077e33dfa6c1f987f"),
        "first_name" : "priya",
        "last_name" : "singh",
        "gender" : "female"
}
{
        "_id" : ObjectId("59704def77e33dfa6c1f9880"),
        "first_name" : "Raj",
        "last_name" : "Trivedi",
        "gender" : "male"
}
{
        "_id" : ObjectId("59704def77e33dfa6c1f9881"),
        "first_name" : "Sheela",
        "last_name" : "ghose",
        "gender" : "female"
}
db.customers.update({first_name:"abhishek"},{first_name:"abhishek", middle_name:"vikram", last_name:"singh"})
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })

> db.customers.update({first_name:"priya"},{$set:{age:25}});
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> db.customers.find().pretty()
{
        "_id" : ObjectId("59704d3077e33dfa6c1f987e"),
        "first_name" : "abhishek",
        "middle_name" : "vikram",
        "last_name" : "singh"
}
{
        "_id" : ObjectId("59704d3077e33dfa6c1f987f"),
        "first_name" : "priya",
        "last_name" : "singh",
        "gender" : "female",
        "age" : 25
}
{
        "_id" : ObjectId("59704def77e33dfa6c1f9880"),
        "first_name" : "Raj",
        "last_name" : "Trivedi",
        "gender" : "male"
}
{
        "_id" : ObjectId("59704def77e33dfa6c1f9881"),
        "first_name" : "Sheela",
        "last_name" : "ghose",
        "gender" : "female"
}
> db.customers.update({first_name:"priya"},{$inc:{age:25}});
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> db.customers.find().pretty()
{
        "_id" : ObjectId("59704d3077e33dfa6c1f987e"),
        "first_name" : "abhishek",
        "middle_name" : "vikram",
        "last_name" : "singh"
}
{
        "_id" : ObjectId("59704d3077e33dfa6c1f987f"),
        "first_name" : "priya",
        "last_name" : "singh",
        "gender" : "female",
        "age" : 50
}
{
        "_id" : ObjectId("59704def77e33dfa6c1f9880"),
        "first_name" : "Raj",
        "last_name" : "Trivedi",
        "gender" : "male"
}
{
        "_id" : ObjectId("59704def77e33dfa6c1f9881"),
        "first_name" : "Sheela",
        "last_name" : "ghose",
        "gender" : "female"
}
> db.customers.update({first_name:"priya"},{$unset:{age:1}});
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> db.customers.find().pretty()
{
        "_id" : ObjectId("59704d3077e33dfa6c1f987e"),
        "first_name" : "abhishek",
        "middle_name" : "vikram",
        "last_name" : "singh"
}
{
        "_id" : ObjectId("59704d3077e33dfa6c1f987f"),
        "first_name" : "priya",
        "last_name" : "singh",
        "gender" : "female"
}
{
        "_id" : ObjectId("59704def77e33dfa6c1f9880"),
        "first_name" : "Raj",
        "last_name" : "Trivedi",
        "gender" : "male"
}
{
        "_id" : ObjectId("59704def77e33dfa6c1f9881"),
        "first_name" : "Sheela",
        "last_name" : "ghose",
        "gender" : "female"
}
>



