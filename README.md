# Assignment.
1.	Open mongo shell
mongo
2.	Create a new database called “meal”
use meals
3.	Create a collection called ‘saloon’ for database ‘meal’.
db.createCollection('meals')
4.	Import `saloon.json` file to “saloon” collection.
quit()
mongoimport --db meals --collection saloon --file saloon.json

```mongoimport --db <DATABASE_NAME> --collection <COLLECTION_NAME> --file <FILE_NAME>```

### Queries:
1. Print all the documents in the collection saloon.  
db.saloon.find({}).pretty()
2. Print the fields restaurant_id, name, area and cooking for all the documents in the collection saloon.  
db.saloon.find({}, {"restaurant_id": 1, "name": 1, "area": 1, "cooking": 1})
3. Print the fields restaurant_id, name, area and cooking, but exclude the field _id for all the documents in the collection saloon.  
db.saloon.find({}, {"restaurant_id": 1, "name": 1, "area": 1, "cooking": 1})
4. Print the fields restaurant_id, name, area and zip code, but exclude the field _id for all the documents in the collection saloon.  
db.saloon.find({}, {"restaurant_id": 1, "name": 1, "area": 1, "address.zipcode": 1}).pretty()
5. Print all the restaurant which is in the area Bronx.  
db.saloon.find({"area": "Bronx"}).pretty()
6. Print the first 5 restaurant which is in the area Bronx.  
db.restaurants.find({"area": "Bronx"}).limit(5);
7. Print the next 5 restaurants after skipping first 5 which are in the area Bronx.  
db.saloon.find({"area": "Bronx"}).skip(5).limit(5).pretty()
8. Find the restaurants who achieved a score more than 90.  
db.saloon.find({"grades": { $elemMatch: {"score": {$gt: 90}}}}).pretty()
9. Find the restaurants that achieved a score, more than 80 but less than 100.  
db.saloon.find({"grades": { $elemMatch: {"score": {$gt: 90, $lt: 100}}}}).pretty()
10. Find the restaurants which locate in latitude value less than -95.754168. 
db.restaurants.find({"address.coord.0" : {$lt : -95.754168}});
11. Find the restaurants that do not prepare any cooking of 'American' and their grade score more than 70 and latitude less than -65.754168.  
12. Find the restaurants which do not prepare any cooking of 'American' and achieved a score more than 70 and located in the longitude less than -65.754168.
Note : Do this query without using $and operator.  
13. Find the restaurants which do not prepare any cooking of 'American ' and achieved a grade point 'A' not belongs to the area Brooklyn. The document must be displayed according to the cooking in descending order.  
14. Find the restaurant Id, name, area and cooking for those restaurants which contain 'Wil' as first three letters for its name.  
15. Find the restaurant Id, name, area and cooking for those restaurants which contain 'ces' as last three letters for its name.  
16. Find the restaurant Id, name, area and cooking for those restaurants which contain 'Reg' as three letters somewhere in its name.
