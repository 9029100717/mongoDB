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

