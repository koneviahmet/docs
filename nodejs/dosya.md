# dosya işlemleri

```javascript
//dosya ismiyle beraber yolunu verdi.
const fileName = __filename;

//sadece dosya yolunu verir
const dir = __dirname;
```

## dizin oluşturma
```js
fs.mkdir('deneme', { recursive: true }, (err) => {
  if (err) throw err;
});
```

## kopyalama
```js
fs.copyFile(dir + '/copy/package.json', 'package.json', (err) => {
  if(err) throw err;

  console.log("kopyalama tamam");
});
```

## dosya oluşturma
```js
/* dosya ekleme */
fs.appendFile('newfile_2.txt', 'Learn Node FS module', function (err) {
  if (err) throw err;
  console.log('File is created successfully.');
})
```



## dosya okuma
```javascript
const fs = require('fs');

//fonksiyon asenkron çalışıyor
fs.readFile('demo.txt', (error, data) => {
  console.log(data.toString());
  console.log("dosya okuma işlemi bitti");
});



/*
senkron çalışan halide var
önce okur sonra ekrana log yazılır
pek tavsiye edilmiyoor.
*/
const demofDosyasi = fs.readFileSync('demo.txt');
console.log("dosya okuma bitti");
```

## dosya yazma
```javascript
const fs = require('fs');
/*
  fs.appendFile() => metni altına eklemeye devam eder
  fs.writeFile() => metni her defasında baştan yazar
*/

fs.appendFile('demo.txt', 'merhaba dünya', (err) => {
  if(err)
    throw err;

    console.log("dosya yazıldı");
});

```

## dosya silme
```javascript
const fs = require('fs');
/*
  fs.unlink()
*/

fs.unlink('demo.txt', (err) => {
  if(err)
    throw err;

    console.log("dosya silindi");
});

```
