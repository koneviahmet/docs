# token
* kullanıcı şeması oluştur
* üye kaydı gerçekleştir
* üye şifresini şifreleyerek kaydet
* token oluşturucuyu kur


kullanıcının parolasını şifrelemek için (md5 gibi) bcrypt paketi kullanacağız
## bcrypt
 bu paket ile şifreleri veri tabanına şifreleyerek kaydedeceğiz


> npm i bcrypt

```javascript
const bcrypt = require('bcrypt');

const saltRounds = 10; //şifreleme kalitesi
const myPlaintextPassword = 's0/\/\P4$$w0rD';


//şifrelemek için
bcrypt.hash(myPlaintextPassword, saltRounds).then(function(hash) {

  //database işlemleri burada

});

//çözmek için
bcrypt.compare(myPlaintextPassword, hash).then(function(result) {
    // result == true
});

```

## token oluşturma
https://www.udemy.com/course/nodejs-egitimi/learn/lecture/8822934#overview

bunun için kullnacağımız paket jsonwebtoken
> npm install jsonwebtoken

tokeni ürettik artık gelen isteklerde tokeni karşılayabiliriz
```javascript
const express = require('express');
const router = express.Router();

const User    = require('../models/User');
const bcrypt  = require('bcrypt');
const jwt     = require('jsonwebtoken');

/* kullanıcı kaydedelim */
router.post('/', (req, res, next) => {

  const {username, password} = req.body;

  bcrypt.hash(password, 10).then((hash) => {

    const  uye = new User({
      username: username,
      password: hash
    });

    const promise = uye.save();
    promise.then((data) => {
      res.json(data);
    }).catch((err) => {
      res.json(err);
    })

  });
  });


/* giriş işlemi yapalım token üreteceğiz */
router.post('/login', (req, res, next) => {
  const {username, password} = req.body;
  User.findOne({
    username: username
  },(err, data) => {
    if(!data){
      next({message: "bağlanma hatası", code: 1});
    }else{


      /* data geliyor ise şifresini de kontrol edelim */
      bcrypt.compare(password, data.password).then(function(result) {
        if(result){
          /* şifresi doğru ise token oluşturacağız */
          const payload = {
            username: username
          };

          //req.app.get('token_key') api.jsen den geldi rasgele bir anahtar
          const token = jwt.sign(payload, req.app.get('token_key'), {
            expiresIn: 720 //720 dakika geçerli olacak demektir.
          })

          res.json({status: 1, token: token});
        }else{
          next({message: "şifre hatası", code: 1});
        }

      });

    }

  });

});

module.exports = router;
```

## token isteğine karşılık verme
bunun için bir ara katman yazmamız gerekecek
* klasor aç arakatman diye
* tokendogrula.js oluştur
* api.js ye ara katmanı dahil et
* ve ara katmanı çağır


api.js
```javascript
//ara katman dahil et
const tokenDogrula = require('./arakatman/tokendogrula');

app.use('/', indexRouter);
//apiye gelen bütün istekler tokenden geçecek dedik
app.use('/api', tokenDogrula);

app.use('/api/movie', movieRouter);
```

tokendogrula.js
```javascript
const jwt = require('jsonwebtoken');

module.exports = (req, res, next) => {

    /* token header gelebilir post gelebilir uada get olarak gelebilir tokeni yakala */
    const token = req.headers['x-access-token'] || req.body.token || req.query.token

    if(token){

        jwt.verify(token, req.app.get('token_key'), (err, decoded) => {
            if (err){
                res.json({
                    status: false,
                    message: 'token doğrulanamadı'
                })
            }else{
                req.decode = decoded;
                /* herşey yolunda ilerle dedik */
                next();
            }
        });
    }else{
        res.json({
            status: false,
            message: 'token gelmedi'
        })
    }
};
```

bundan sonra aldığım tokeni ister header ister post ister get olarak gönderir ara katmanda doğrulamadan geçirtebilirim


asdsad
