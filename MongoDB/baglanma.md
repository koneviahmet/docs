# mongodb bağlanma
mongoose paketini kuracağız

```javascript
var mongoose = require("mongoose");
/* moongoose bağlanalaım */
mongoose.connect("mongodb://localhost/deneme", { useNewUrlParser: true })
    .then(() => {
      console.log("bağlandın kanka");
    })
    .catch((err) => {
      console.log("bağlanmadı kanka");
    });
```

ikinci bağlanma şekli bunu tavsiye ediyor
```javascript
var mongoose = require("mongoose");
mongoose.connect('mongodb://localhost/deneme',{useNewUrlParser: true, useUnifiedTopology: true});
mongoose.connection.on('open', () => {
    console.log("MongoDB: Connected");
});
mongoose.connection.on('error', (err) => {
    console.log("MongoDB: Error", err);
});
```
