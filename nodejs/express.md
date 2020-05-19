# express
normal http her resim, style veya script dosyası için ayrı ayrı talepte bulunur. Bunu engellemek için express kullanıyoruz
> npm install express --save

```javascript
const express = require('express');
const app   = express();


app.get('/', (req, res) => {
  res.send('merhaba dünya');
});


app.listen(3000, () => {
  console.log("express başlatıldı");
})

```

## express-generator
kolay ekspress kurulumu sağlegal
* npm install -g express-generator
* express .
* npm install

# yönlendirme (routing)
- get
- post
- put
- delete
- all


> yukarıdaki tlepleri servere yapmak için [postman](uygulamalar/postman.md) kullanabilrizi

* ? => zorunlu olmayan > örneğin
   * ilet?isim => (iletisim, ileisim)   ikisinide kabul eder çoklu harf için parantez içine alınır
   * ah(me)?t => me olsada olur olmasada demek
* \* => yerine herhangi bir ifade gelebilir
  * ilet*isim => iletisim olur yada yıldız yerine herhangi bir kelime yada ifade gelebilri
    * iletisim => ok
    * iletASDisim => ok
+ => soldaki ifadenin aynısı olmalı
  * ahm+et => istediğin kadar m yazabilirsin demek
    * ahmmet => ok
    * ahmmmet => ok


```javascript

/*
  ahmete soru işareti eklersen olsada olur olmasada olur anlamına gelir
*/
app.get('/users/:id/:postId/:ahmet?', (req, res) => {
  /* bana bir nesne gönderir*/
  let url = req.params;
  let id  = url.id;
  let {id} = url;

  res.send('merhaba dünya');
});
```

## hata yönetimi
https://www.udemy.com/course/nodejs-egitimi/learn/lecture/8774076#overview

# rootları import sayfası ile derleme

kullanım kaynakları
* https://github.com/meseven/node-egitimi/tree/master/express/routing
* https://www.udemy.com/course/nodejs-egitimi/learn/lecture/8772210#overview

routes sayfasının için ekle signIn.js
```javascript
const express = require('express');
const router = express.Router();

router.get('/signIn', (req, res) => {
    res.send("signIn sayfası");
});

router.post('/signIn', (req, res) => {
    res.send("signIn sayfası (POST Method)");
});

module.exports = router;
```

routes sayfasının için ekle signUp.js
```javascript
const express = require('express');
const router = express.Router();

router.get('/signUp', (req, res) => {
    res.send("signUp sayfası");
});

router.post('/signUp', (req, res) => {
    res.send("signUp sayfası (POST Method)");
});

module.exports = router;
```

api.js
```javascript
const express = require('express');
const app = express();

const signIn = require('./routes/signIn');
const signUp = require('./routes/signUp');

// => /user/signIn e post edersek tetiklenecek
app.use('/user', signIn);

// => /signUp e post edersek tetiklenecek
app.use('/', signUp);

app.listen(3000, () => {
    console.log("express server çalıştı.");
});
```

## ara katman (middleware) yazma
bu kısım kullanıcı giriş yapmışmı yapmamış mı gibi amaçlar için kullanılabilir.
ara katmanın daha doğru kullanımı helper dosyasında bir js aç ve sonradan sayfaya import et
https://www.udemy.com/course/nodejs-egitimi/learn/lecture/8772642#overview

sonradan midilvare kullanımını baya değiştirmiş
https://github.com/meseven/node-egitimi/tree/master/express/middleware
anladığım kadarıyla direk  app.use('/profile', profile); buradaki sayfaların içine dahil etmiş

```javascript
...
app.use('/profile', profile);
app.use('/user', signIn);

/* ara katman */
//profile ve user ikisinde de çalışır
app.use((req, res, next) => {
    const isLogin = true;

    if (isLogin)
        /* next dersem ara katmandan geçti demektir. yani giriş yapmış anlamında */
        next();
    else
        res.send("Lütfen giriş yapın.");
});


/* sadece profil sayfasında çalışır */
app.use('/profile',(req, res, next) => {
    const isLogin = true;

    if (isLogin)
        /* next dersem ara katmandan geçti demektir. yani giriş yapmış anlamında */
        next();
    else
        res.send("Lütfen giriş yapın.");
});



```




```javascript
#kod
```
