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

### Homework 2.1

```
cd "Homework 2.1"
mongorestore dump
mongo
use video
db.movieDetails.find({ year: 2013, rated: "PG-13", "awards.wins": 0 }, { _id: 0, title: 1 })

// { "title" : "A Decade of Decadence, Pt. 2: Legacy of Dreams" }
```

### Homework 2.2

```
cd "Homework 2.2"
// use the dump of the Homework 2.1
db.movieDetails.find({}, { title: 1, _id: 0 }) ✓
db.movieDetails.find({}, { title: 1 })
db.movieDetails.find({ title: "" }, { title: 1 })
db.movieDetails.find({}, { title })
db.movieDetails.find({ year: 1964 }, { title: 1, _id: 0 }) ✓
db.movieDetails.find({ title: "Muppets from Space" }, { title: 1 })
```

### Homework 2.3

```
cd "Homework 2.3"
// use the dump of the Homework 2.1
db.movieDetails.find({ "countries.1": "Sweden" }).count()

// 6
```