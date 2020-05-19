# Mantıksal && Operatörü ile Tek Satırda if

```javascript
function Mailbox(props) {
  const unreadMessages = props.unreadMessages;
  return (
    <div>
      <h1>Merhaba!</h1>
      {unreadMessages.length > 0 &&
        <h2>
          {unreadMessages.length} adet okunmamış mesajınız var.
        </h2>
      }
    </div>
  );
}
```
>eğer koşulunuz true ise, &&‘den sonra yazacaklarınız çıktı olur. Eğer koşulunuz false ise, React onu görmezden gelip atlayacaktır.

## tek satırda else ve if kullanımı
```javascript
condition ? true : false
```

```javascript
render() {
  const isLoggedIn = this.state.isLoggedIn;
  return (
    <div>
      Bu kullanıcı şuan <b>{isLoggedIn ? 'çevrimiçi' : 'çevrimdışı'}</b>.
    </div>
  );
}
```
```javascript
render() {
  const isLoggedIn = this.state.isLoggedIn;
  return (
    <div>
      {isLoggedIn
        ? <LogoutButton onClick={this.handleLogoutClick} />
        : <LoginButton onClick={this.handleLoginClick} />
      }
    </div>
  );
}
```

bir bileşene null eklersek o bileşen render edillmez
```javascript
function WarningBanner(props) {
  if (!props.warn) {
    return null;
  }

  return (
    <div className="warning">
      Bu konuda seni uyarıyorum!
    </div>
  );
}

class Page extends React.Component {
  constructor(props) {
    super(props);
    this.state = {showWarning: true};
    this.handleToggleClick = this.handleToggleClick.bind(this);
  }

  handleToggleClick() {
    this.setState(state => ({
      showWarning: !state.showWarning
    }));
  }

  render() {
    return (
      <div>
        <WarningBanner warn={this.state.showWarning} />
        <button onClick={this.handleToggleClick}>
          {this.state.showWarning ? 'Gizle' : 'Göster'}
        </button>
      </div>
    );
  }
}

ReactDOM.render(
  <Page />,
  document.getElementById('root')
);
```

>Bir bileşenin render metodundan null döndürmesi yaşam döngüsü metotlarının çalışmasını engellemez. Örneğin componentDidUpdate gerektiği zaman çalışmaya devam edecektir.
