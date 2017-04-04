### Homework 1.1

```
cd "Homework 1.1"
mongorestore dump
mongo
use m101
db.hw1_1.find()

// { "_id": ObjectId("..."), "answer": "Hello from MongoDB!" }
```

### Homework 1.2

```
cd "Homework 1.2"
mongorestore dump
npm install
node app.js

// Answer: I like kittens
```

### Homework 1.3

```
cd "Homework 1.3"
mongorestore dump
npm install
node app.js 

// Open your browser, navigate to http://localhost:3000 and you will see:
// Hello, Agent 007.
```

### Homework 1.4

```
cd "Homework 1.4"
npm install
node app.js 

// Open your browser, navigate to http://localhost:3000 and you will see a form. Type these values in the fields:
// title: Jaws | year: 1975 | imdb: tt0073195
// You will see "Document inserted with _id: ..." in the browser

Ctrl + C
mongo
use video
db.movies.find()

// { "_id": ObjectId("..."), "title": "Jaws", "year": "1975", "imdb": "tt0073195" }
```