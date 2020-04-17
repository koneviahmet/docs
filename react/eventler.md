# eventler

react olayları constructor da tanımlayarak kullanmamızı tavsiye ediyor. hata fonksionlarını pek önermiyor. sebebini altta belirttim.

## onClick kullanımı

html için normak kullanım
```html
<button onclick="activateLasers()">
  Activate Lasers
</button>
```

react ile kıllanımı
```html
<button onClick={activateLasers}>
  Activate Lasers
</button>
```

> React’teki diğer bir farklılık ise, olaylardaki varsayılan davranışın false değeri döndürülerek engellenemiyor oluşudur.

```javascript
 //jqueryde return false diyerek formu engelliyorduk reacta ise e.preventDefault() diyerek engelliyeceğiz.

function handleClick(e) {
   e.preventDefault();
   console.log('The link was clicked.');
 }
```

bindin tanımlanması
```javascript
class Toggle extends React.Component {
  constructor(props) {
    super(props);
    this.state = {isToggleOn: true};

    // Callback içerisinde `this` erişiminin çalışabilmesi için, `bind(this)` gereklidir
    this.handleClick = this.handleClick.bind(this);
  }

  handleClick() {
    this.setState(state => ({
      isToggleOn: !state.isToggleOn
    }));
  }

  render() {
    return (
      <button onClick={this.handleClick}>
        {this.state.isToggleOn ? 'ON' : 'OFF'}
      </button>
    );
  }
}

ReactDOM.render(
  <Toggle />,
  document.getElementById('root')
);
```

>JSX callback’lerinde this kullanırken dikkat etmeniz gerekmektedir. Çünkü JavaScript’te, sınıf metotları varsayılan olarak this‘e bağlı değillerdir. Bu nedenle, this.handleClick‘i bind(this) ile bağlamayı unutarak onClick‘e yazarsanız, fonksiyon çağrıldığında this değişkeni undefined hale gelecek ve hatalara sebep olacaktır.


binde eklemeden sınıfın için this aktarmak istersek hata fonksiyonu kullanabiliriz. react bunun hala deneysel olduğunu söylüyor
```javascript

class LoggingButton extends React.Component {
  // Bu yazım şekli, `this`'in handleClick içerisinde bağlanmasını sağlar.
  // Uyarı: henüz *deneysel* bir özelliktir.
  handleClick = () => {
    console.log('this is:', this);
  }

  render() {
    return (
      <button onClick={this.handleClick}>
        Click me
      </button>
    );
  }
}
```

aynı methodun farklı kullanımı
```javascript
class LoggingButton extends React.Component {
  handleClick() {
    console.log('this is:', this);
  }

  render() {
    // Bu yazım şekli, `this`'in handleClick içerisinde bağlanmasını sağlar.
    return (
      <button onClick={() => this.handleClick()}>
        Click me
      </button>
    );
  }
}
```

>Fakat bu yöntemin bir dezavantajı vardır. LoggingButton bileşeni her render edildiğinde, yeni bir callback oluşturulur. Birçok durumda bu olay bir sorun teşkil etmez. Ancak ilgili callback, prop aracılığıyla alt bileşenlere aktarılırsa, bu bileşenler fazladan render edilebilir. Bu tarz problemlerle karşılaşmamak için binding işleminin, ya sınıfın constructor’ında ya da class fields yöntemi ile yapılmasını öneririz.


## olay yöneticileri ile parametre göndermek
```html
<button onClick={(e) => this.deleteRow(id, e)}>Delete Row</button>
<button onClick={this.deleteRow.bind(this, id)}>Delete Row</button>
```
