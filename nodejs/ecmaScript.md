# Ecma Script
ecma script 6 ile ilgili yeni gelen özellikler burada


```javascript
const name = "ahmet";
const surname = "şık";

/** bu normal kullanımı */
console.log(name + surname);


//es6 ile
console.log(`benim adım ${name}, soyadım ${surname}`);
```


```javascript
const degerler = {
  d1: "deger1",
  d2: "deger1",
  d3: {isim: "cafer"}
}

/** normal kullanım */
const  degerHayda = degerler.d1;
const  degerHobba = degerler.d2;

/* es6 ile */
const {degerHayda, degerHobba} = degerler;

//değer 3 te isime erişmek
const {deger3: {isim}} = degerler;
console.log(isim);

const {deger3: {isim: name}} = degerler;
console.log(name);
```


```javascript
const arr = [1,2,3,4];
console.log(...arr);

const arr = [1,2,3,4];
const arr2 = [...arr,5,6,7];

const arr = ['a', 'b', 'c', 'd'];
const [d1,d2,...d3] = arr;
```



## promise kullanımı then then vs..
```javascript
  const asenkronFonksiyon = () => {
    return new Promise((resulve, reject) => {
      resulve('her şey yolunad');

      reject('hata var');
      //reject ile çıktı gönderirsek
    }
  }

  //kullanımı
  asenkronFonksiyon()
    .then((data) => {
        console.log(data);

        //buradan return dediğim değer alta geçer
        return 1;
    })
    .then((data) => {
        //data ekrana yukarıdan gelen 1 i verir.
        console.log(data);
    })
    .catch((error) => {
        console.log("reject ile verdiğimiz hatayı aşağıda yakaladık");
    });
```














```javascript
  #buradaya
```
