# props
“props” (properties => özelikler)

react companenterin içinde kullanımı

```javascript
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```

# probslar ile ilgili önemli uyarı
```javascript
function sum(a, b) {
  return a + b;
}
```
Bu tarz fonksiyonlar, kendi girdi parametrelerini değiştirmedikleri ve her zaman aynı parametreler için aynı sonucu ürettiklerinden dolayı “pure” (saf) fonksiyonlardır.

```javascript
function withdraw(account, amount) {
  account.total -= amount;
}
```
Tam ters örnek verecek olursak, aşağıdaki fonksiyon impure’dür (saf değildir). Çünkü kendi girdi değerini değiştirmektedir:

> React, kod yazımında oldukça esnek olmasına rağmen, sadece bir tek kuralı şart koşmaktadır: Bütün React bileşenleri yalın (pure) fonksiyonlar gibi davranmalı ve prop’larını asla değiştirmemelidirler.
