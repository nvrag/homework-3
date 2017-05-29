# Requests


1. Students with score > 87% and < 93%:

```javascript
db.resultsCollection.find({
   "scores.score": {
      $gt: 87,
      $lt: 93
   }
}).pretty()
```
2. Exam results > 90%:

```javascript
db.resultsCollection.aggregate([{
   $unwind: "$scores"
  }, {
     $match: {
        "scores.score": {
           $gt: 90
        },
        "scores.type": "exam"
     }
}])
```
3. For students with name Dusti Lemmond add field “accepted”:

```javascript
db.resultsCollection.updateMany({
   name: "Dusti Lemmond"
   }, {
      $set: {
         accepted: true
      }
})
```