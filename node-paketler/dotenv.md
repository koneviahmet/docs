# dotenv
ortam değişkenlerini yani gizli tutulması gereken değişlenleri tutmamızı sağlayan yapı.

> npm install --save dotenv


.env isminde bir dosya oluştur
```js
DB_HOST=localhost
DB_USER=root
DB_PASS=123456
```

app.js ve diğer js lerde kullanmak için
```js
require('dotenv').config();


/* env çağırmak için*/
console.log("DB_HOST: ",process.env.DB_HOST);
console.log("DB_USER: ",process.env.DB_USER);
console.log("DB_PASS: ",process.env.DB_PASS);
```
