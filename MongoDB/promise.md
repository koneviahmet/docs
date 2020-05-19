# Promise ile bağlanma

promise ile bağlanma

```javascript
mongoose.connect('mongodb://localhost/movie-api',{useNewUrlParser: true, useUnifiedTopology: true});
mongoose.connection.on('open',() => {
    console.log("bağlandı kanka");
});
mongoose.connection.on('error', (err) => {
    console.log("db bağlanma hatası");
})

mongoose.Promise = global.Promise;
```

```javascript
  /* promise kullanarak kaydetme */
  const promise = movie.save();
  promise.then((data) => {
    res.json(data);
  }).catch((err) => {
    res.json(err);
  })
```

promise ile veri çekme
```javascript
const promise = Movie.find({});
promise.then((data) => {
  res.json(data);
}).catch((err) => {
  res.json(err);
});
```





```javascript
#kod
```
