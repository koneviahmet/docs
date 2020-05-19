# Listeler
## map kullanımı

```javascript
const numbers = [1, 2, 3, 4, 5];
const doubled = numbers.map((number) => number * 2);
console.log(doubled);

//sonuç
[2, 4, 6, 8, 10]
```

sayıları aldık ve iki katına çıkartarak sonuç döndük
## map fonksiyonun react ta kullanımı
```javascript
const numbers = [1, 2, 3, 4, 5];
const listItems = numbers.map((number) =>
  <li>{number}</li>
);

ReactDOM.render(
  <ul>{listItems}</ul>,
  document.getElementById('root')
);


//bu daha kullanşlı fonskiyon içinde kullandk
function NumberList(props) {
  const numbers = props.numbers;
  const listItems = numbers.map((number) =>
    <li>{number}</li>
  );
  return (
    <ul>{listItems}</ul>
  );
}
```

>Bu kodu çalıştırdığınızda liste elemanları için bir anahtar verilmesi gerektiği konusunda size bir uyarı verilir. (ikinci kod)

key eklenmiş halin
```javascript
function NumberList(props) {
  const numbers = props.numbers;
  const listItems = numbers.map((number) =>
    <li key={number.toString()}>
      {number}
    </li>
  );
  return (
    <ul>{listItems}</ul>
  );
}

const numbers = [1, 2, 3, 4, 5];
ReactDOM.render(
  <NumberList numbers={numbers} />,
  document.getElementById('root')
);
```
> keyler Anahtarlar; hangi öğelerin değiştiğini, eklendiğini ya da silindiğini belirleme noktasında React’e yardımcı olur:


## map fonksiyonunda anahtar kullanımı

> anahtarı map içinde kullanmamız mantıklıdır. Anahtar olarak index kullanmak tavsiye edilmiyor doğru olan kullanımın kendi oluşturduğumuz bir anahtar olduğu söylendiyor. indexin değişme ihtimali oldıığu için buda render performansına etki edebilir diyor.

anahtar olarak index numarasını kullanabiliriz
>Dizi içindeki elemanların değişme ihtimali varsa, anahtarlar için index numaralarının kullanılmasını önermiyoruz.
```javascript
const todoItems = todos.map((todo, index) =>
  // Bunu yalnızca öğelerinizin sabit ID'leri yoksa yapın
  <li key={index}>
    {todo.text}
  </li>
);
```
