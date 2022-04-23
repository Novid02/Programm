# Der CODE


from pymongo import MongoClient
import datetime

cluster = "mongodb+srv://David:DavidMister@test.s72qv.mongodb.net/TEST?retryWrites=true&w=majority"
client = MongoClient(cluster)

print(client.list_database_names())

db = client.TEST

print(db.list_collection_names())

todo1 = {"name": "David", "text": "My first todo!", "status": "open", "tags": ["python", "coding"], "date": datetime.datetime.utcnow()}

todos = db.todos

result = todos.insert_one(todo1)

todos2 = {"name": "David", "text": "My second todo!", "status": "open", "tags": ["python", "coding"], "date": datetime.datetime.utcnow()}\
        ,{"name": "David", "text": "My third todo!", "status": "open", "tags": ["python", "c++"], "date": datetime.datetime.utcnow()}

result = todos.insert_many(todos2)

result = todos.delete_one({"tags": "c++"})

result = todos.update_many({"tags": "python"}, {"$set": {"status": "closed"}})

todo4 = {"name": "Nils", "text": "My first todo!", "status": "open", "tags": ["python", "coding"], "date": datetime.datetime.utcnow()}
