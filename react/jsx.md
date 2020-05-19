# jsx

örnek
```javascript
  const element = <h1>Hello, world!</h1>;
```
Burada acayip bir şekilde yazılan söz dizimi ne bir string ne de HTML’e aittir. Bu söz dizimi JSX olarak adlandırılır ve JavaScript’in bir söz dizimi uzantısıdır.
Bu yapı sayesinde sadece ilgili yerlerini render edebiliyoruz. Sayfanın tamamını render etmemizi engelliyor ve hız katıyor.


```javascript
const name = 'Josh Perez';
const element = <h1>Hello, {name} {2 + 2}</h1>;

//2. örnek
function formatName(user) {
  return user.firstName + ' ' + user.lastName;
}

const user = {
  firstName: 'Harper',
  lastName: 'Perez'
};

const element = (
  <h1>
    Hello, {formatName(user)}!
  </h1>
);
```
name in diğer jsx içinde kullanımı


## jfx de çif tırnak kullanma
anladığım kadarı ile çift tırnak kullanmak terine aşağıdaki gibi kullancağaız
```
//TEKRARBAK
const element = <img src={user.avatarUrl}></img>;
```

## jfx isimlendirme
>JSX ifadeleri, HTML’den ziyade JavaScript’e daha yakındırlar. Bu nedenle React DOM, özellik isimlendirme için HTML’deki gibi bir isimlendirme yerine camelCase isimlendirme standardını kullanmaktadır.
> Örneğin JSX içerisinde class özelliği className, ve tabindex özelliği de tabIndex olarak yazılmalıdır.

## JSX ile Alt Elemanların Tanımlanması

```javascript
const element = (
  <div>
    <h1>Hello!</h1>
    <h2>Good to see you here.</h2>
  </div>
);
```

> JSX, Injection Saldırılarını Engeller Çünkü varsayılan olarak React DOM, render işlemi öncesinde gömülen değerlerdeki <, & gibi bazı özel karakterleri &lt; ve &amp; olacak şekilde dönüştürür. Böylece uygulama içerisinde, kullanıcının yazabileceği kötü amaçlı kodların enjekte edilmesi engellenmiş olur. Render işlemi öncesi her şey string ifadeye dönüştürüldüğünden dolayı, XSS saldırıları engellenmiş olur.

# jsx alt elemanın açılımı
anladığım kadarıyla babel kullanılarak derleniyor
```javascript
const element = (
  <h1 className="greeting">
    Hello, world!
  </h1>
);
```
yukarıdaki kodun açılımı babel tarafından
```javascript
const element = {
  type: 'h1',
  props: {
    className: 'greeting',
    children: 'Hello, world!'
  }
};
```
bu koda çevriliyor.

Örneğin aşağıdaki kod, sayfada “Hello, Sara” mesajını görüntüler:

```javascript
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

const element = <Welcome name="Sara" />;
ReactDOM.render(
  element,
  document.getElementById('root')
);
```
> önemli: Not: Bileşen isimlendirmelerinde daima büyük harfle başlayınız. Çünkü React, küçük harfle başlayan bileşenlere DOM etiketleri gibi davranır. Örneğin <div />, bir HTML div etiketini temsil eder, fakat <Welcome /> ise bir bileşeni temsil eder ve kodun etki alanında Welcome‘ın tanımlı olmasını gerektirir.

```javascript
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

function App() {
  return (
    <div>
      <Welcome name="Sara" />
      <Welcome name="Cahal" />
      <Welcome name="Edite" />
    </div>
  );
}

ReactDOM.render(
  <App />,
  document.getElementById('root')
);
```
