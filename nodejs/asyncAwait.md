# async - await yapısı

https://www.udemy.com/course/nodejs-egitimi/learn/lecture/8699702#overview
> async altında bulunan fonksiyon ları sıraya koymak için kullanılıyor. örneğin alttaki fonksiyonda asenkron içindeki fonksiyonlar sırasıyla biri bitmeden diğeri çalışmayacak şekilde çalışacaklar.


## promise kullanım örneği
```js
const asynFonksiyon = () => {
  return new Promise((resolve, reject) => {
    resolve("her şey yolunda")
    //reject("hata var kanka");
  });
};


asynFonksiyon()
.then((data) => {
  console.log(data);
})
.catch((err) => {
  /* reject hata yakalarsa hata var kanka diye catch e düşer*/
  console.log(err);
});
```


## async örnek
```js
const user = { id: 10, name: 'mehmet' };
const friends = [ { id: 11, name: 'kenan' }, { id: 12, name: 'murat' } ];

const getUser = () => {
  return new Promise((resolve, reject) => {
     setTimeout(() => {
         resolve(user);
     }, 500);
  });
};

const getFriends = (userId) => {
  return new Promise((resolve, reject) => {
     setTimeout(() => {
        resolve(friends);
     }, 1000);
  });
};

// async/await
async function asenkronAkis(){
    const user = await getUser();
    const friends = await getFriends(user.id);
    console.log(user, friends);
}
asenkronAkis();
```


## asyn - aweit de hata yakalama

try cahtc ile yakalıyoruz promise resolve verdiği zaman try içine reject verdiği zamanda catch içine düşüyor

```js
// async/await
async function asenkronAkis(){

    try {
      const silx  = await sil();
      const copyx = await copy();
      const createx = await create();
      const appendx = await append();

      console.log(silx);
      console.log(copyx);
      console.log(createx);
      console.log(appendx);

    } catch (e) {
      console.log('hata oldu: ', e);
    }
}
asenkronAkis();
```

## sıra ile dosya oluşturma ve kopyalama örneği
```js
const fs = require('fs');

/* komut satırının başlatıldığı dizini alalım */
const dizin = process.env.PWD;

/* bu uygulamanın yüklü olduğu dizin */
const dir = __dirname;

const sil = () => {
  return new Promise((resolve, reject) => {
    fs.unlink('package.json', (err) => {
      if(err){
        reject("1 - silinme anında hata oldu");
      }else{
        resolve("1 - silme tamam");
      }
    });
  });
};


const copy = () => {
  return new Promise((resolve, reject) => {
    fs.copyFile(dir + '/copy/package.json', 'package.json', (err) => {
      if(err){
        reject("2 - kopyalama anında hata oldu");
      }else{
        resolve("2 - kopyalama tamam");
      }
    });
  });
}


const create = () => {
  return new Promise((resolve, reject) => {
    fs.mkdir('deneme', { recursive: true }, (err) => {
      if(err){
        reject("3 - dosya oluşturma anında hata oldu");
      }else{
        resolve("3 - dosya oluşturma tamam");
      }
    });

  })
}

const append = () => {
  return new Promise((resolve, reject) => {
    fs.appendFile('deneme/newfile_2.txt', 'Learn Node FS module', function (err) {
      if(err){
        reject("4 - dosya ekleme anında hata oldu");
      }else{
        resolve("4 - dosya ekleme tamam");
      }
    });

  });
}


// async/await
async function asenkronAkis(){

    try {
      const silx  = await sil();
      const copyx = await copy();
      const createx = await create();
      const appendx = await append();

      console.log(silx);
      console.log(copyx);
      console.log(createx);
      console.log(appendx);

    } catch (e) {
      console.log('hata oldu: ', e);
    }
}
asenkronAkis();```


## önemli
promise içinde doğrudan async kullanabiliriz.
```js
new Promise(function(resolve, reject) {
  /* sor cevapla 1 */
  (async () => {

    /* buradaki akış asenkron şekilde olacak */

  })();


});
```
