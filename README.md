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
// use the dump from Homework 2.1
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
// use the dump from Homework 2.1
db.movieDetails.find({ "countries.1": "Sweden" }).count()

// 6
```

### Homework 2.4

```
cd "Homework 2.4"
// use the dump from Homework 2.1
db.movieDetails.find({ genres: ["Comedy", "Crime"] }).count()

// 20
```

### Homework 2.5

```
cd "Homework 2.5"
// use the dump from Homework 2.1
db.movieDetails.find({ genres: { $all: ["Comedy", "Crime"] } }).count()

// 56
```

### Homework 2.6

[$set](https://docs.mongodb.com/manual/reference/operator/update/set/): The $set operator replaces the value of a field with the specified value.

### Homework 2.7

```
cd "Homework 2.7 - Challenge"
// use the dump from Homework 2.1
db.movieDetails.insertOne({
  title: "Challenge 1",
  "awards": {
    "oscars": [
      {
        "award": "bestAnimatedFeature",
        "result": "won"
      },
      {
        "award": "bestMusic",
        "result": "won"
      },
      {
        "award": "bestPicture",
        "result": "nominated"
      },
      {
        "award": "bestSoundEditing",
        "result": "nominated"
      },
      {
        "award": "bestScreenplay",
        "result": "nominated"
      }
    ],
    "wins": 56,
    "nominations": 86,
    "text": "Won 2 Oscars. Another 56 wins and 86 nominations."
  }
})

db.movieDetails.find({ "awards.oscars.award": "bestPicture" })

/* result: */
{
  "_id": ObjectId("590b192e29d4029bf2df7897"),
  "title": "Challenge 1",
  "awards": {
    "oscars": [
      {
        "award": "bestAnimatedFeature",
        "result": "won"
      },
      {
        "aw ard": "bestMusic",
        "result": "won"
      },
      {
        "award": "bestPicture",
        "result": "nominated"
      },
      {
        "award": "bestSoundEditing",
        "result": "nominated"
      },
      {
        "award ": "bestScreenplay",
        "result": "nominated"
      }
    ],
    "wins": 56,
    "nominations": 86,
    "text": "Won 2 Oscars. Another 56 wins and 86 nominations."
  }
}
```

### Homework 2.8

```
cd "Homework 2.8 - Challenge 2"
// use the dump from Homework 2.1

db.movieDetails.find({
  "imdb.votes": {
    $lt: 10000
  },
  "year": {
    $gt: 2010,
    $lte: 2013
  },
  $and: [
    {
      "tomato.consensus": null
    },
    {
      "tomato.consensus": {
        $exists: true
      }
    }
  ]
}).count()

// 11

db.movieDetails.updateMany({
  "imdb.votes": {
    $lt: 10000
  },
  "year": {
    $gt: 2010,
    $lte: 2013
  },
  $and: [
    {
      "tomato.consensus": null
    },
    {
      "tomato.consensus": {
        $exists: true
      }
    }
  ]
}, { $set: { "tomato.consensus": "" }})

```
