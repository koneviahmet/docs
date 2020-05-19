# istisnalar
* throw
* try
* catch
* finally



```javascript
  // throw hata fırlatmaya yarar
  var isim = "mehmet";
  if(isim !== "mehmet"){
    /* hata fırlatıldığı anda kod çalışması ölür*/
    throw Error("Beklenmeyen isim girişi yapıldı");
  }
```

```javascript

  try{
    var sayi1 = 4;
    var sayi2 = 1;

    if(sayi2 === 0){
      //hatayı fırlattık
      throw Error('say2 0 olamaz');
    }

  }catch(error){
    //hatayı burada yakaladık
    console.log(error);
  } finally{
    /* hata oldu hiç bir kod çalışmaz ama son defa burası çalışır */
  }

```


```javascript
  #buradaya
```
