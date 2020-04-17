# render olayları
## renderde koşul kullanımı

```javascript
function UserGreeting(props) {
  return <h1>Hoş geldiniz!</h1>;
}

function GuestGreeting(props) {
  return <h1>Lütfen kayıt olun</h1>;
}

function Greeting(props) {
  const isLoggedIn = props.isLoggedIn;
  if (isLoggedIn) {
    return <UserGreeting />;
  }
  return <GuestGreeting />;
}

ReactDOM.render(
  // Kodu değiştirerek deneyin: isLoggedIn={true}:
  <Greeting isLoggedIn={false} />,
  document.getElementById('root')
);
```

>Greeting adında bir bileşen daha oluşturuyoruz. Bu bileşen, kullanıcının giriş yapma durumuna göre yukarıda yazdığımız bileşenleri gösterecek.

mantıksal oparatörlerin kolay kullanımı için [tıklayınız](react/mantiksaloparatorlar.md)
