## cors

express modulle kurduğunuz apiye hangi sitelerden istek gelecek onu belirlemenize yarayan bir paket. güvenlik amaçlı kullanılabilir


Evet, gördüğünüz üzere “cors” paketi sayesinde Node.js serverlarındaki ‘Access-Control-Allow-Origin’ hatasından kurtulunabilmekte ve belirlenen adreslere API erişim konfigürasyonu sağlanabilmektedir.


> npm install cors



ara katman olarak ayarlayara sitenin tamamına erişime sınırlandırma getirebiliriz
```js
var cors = require("cors")

app.use(cors());
```

dilersek sadece bir routere de sınırlandırma koyabiliriz.
```js
app.get("/page1", cors(), (request, response, next) => {
     response.json("...");
});
```


## ayarlar


Burada “/page1” route’unu, sade ve sadece “http://localhost:4200” adresinden gelecek talepler neticesinde tetikleyecektir.

```js
var corsOptions = {
     origin: 'http://localhost:4200',
     optionsSuccessStatus: 200
}

app.get("/page1", cors(corsOptions), (request, response, next) => {
     response.json("...");
});
```


Eğer ki, birden fazla adresi konfigure etmek istiyorsanız aşağıdaki gibi bir whitelist tanımlaması üzerinden işlemlerinizi gerçekleştirebilirsiniz.
```js
var whitelist = ['http://localhost:4200', 'http://localhost:4201']
var corsOptions = {
     origin: (origin, callback) => {
          if (whitelist.indexOf(origin) !== -1)
               callback(null, true);
          else
               callback(new Error("! ! !"));
     }
}

app.get("/page1", cors(corsOptions), (request, response, next) => {
     response.json("...");
});
```
