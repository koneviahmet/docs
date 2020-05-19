# çok kullanılan kodlar

## değişken tanımlama
```javascript
let degisir = "bu değiştirilebilir";
const degismez = "bu değiiştirilemez değişken";

//çoklu değişken tanımlama
let degisken1, degisken2, degisken3 = 1;
```

## setTimeOut
1 saniye sonra başla
```javascript

  setTimeOut(function(){
    console.log("1 saniye sonra ben geldim");
  },1000);

  /* fonksiyona tanımlayarak kullanma */
  let fnc = function(){
    console.log("selam bende bir saniye sonra geldim");
  }
  setTimeOut(fnc, 1000);
```

## setInterval
```javascript
  let fnc = function(){
    console.log("selam ben her bir saniyede gelirim");
  }
  /** başlat */
  setInterval(fnc, 1000);
  //buurada durdurkuk
  clearInterval(fnc);

```
## for döngüsü

```javascript
  for(var i = 0; i < 10; i++){
    console.log(i);
  }
```

# nesneler
```javascript
  let insan = {};
  insan.yas = 12;
  insan.isim = "fırat";
  insan.yuru = function(){
    console.log("yürü be koçum");
  }
```

# diziler

dizileri nesnelerden ayıran en önemli özellik dizilerde indis kavramı var.
```javascript
  let dizi = ['mehmet', 24, false, 0.3];
```

# yuvarlama
```javascript
Math.round(99.3);
```





```javascript
  #buradaya
```
