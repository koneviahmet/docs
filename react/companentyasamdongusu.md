# Companenet yaşam döngüsü
companenet birer saniye arayla dinleniyor statelerde değişim olup olmadığı kontrol ediliyor..

```javascript
class Clock extends React.Component {
  constructor(props) {
    super(props);
    this.state = {date: new Date()};
  }

  componentDidMount() {
    this.timerID = setInterval(
      () => this.tick(),
      1000
    );
  }

  componentWillUnmount() {
    clearInterval(this.timerID);
  }

  tick() {
    this.setState({
      date: new Date()
    });
  }

  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        <h2>It is {this.state.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}

ReactDOM.render(
  <Clock />,
  document.getElementById('root')
);
```

* ReactDOM.render() metoduna <Clock /> aktarıldığı zaman React, Clock bileşeninin constructor’ını çağırır. Clock bileşeni, mevcut saati görüntülemesi gerektiğinden dolayı, this.state‘e o anki zamanı atar. Daha sonra bu state güncellenecektir.
* Devamında React, Clock bileşeninin render() metodunu çağırır. Bu sayede React, ekranda nelerin gösterilmesi gerektiğini bilir. Sonrasında ise Clock‘un render edilmiş çıktısı ile eşleşmek için ilgili DOM güncellemelerini gerçekleştirir.
* Clock bileşeninin çıktısı DOM’a eklendiğinde, yaşam döngüsündeki componentDidMount() metodu çağrılır. Bu metodda Clock bileşeni, her saniyede bir tick() metodunun çalıştırılması gerektiğini tarayıcıya bildirir.
* Tarayıcı her saniyede bir tick() metodunu çağırır. tick() metodunda Clock bileşeni, kullanıcı arayüzünü güncellemek için setState() metodunu çağırır ve bu metoda mevcut tarih/saat değerini aktarır. setState()‘in çağrılması sayesinde React, state’in değiştiğini anlar ve ekranda neyin görüntüleneceğini anlamak için tekrar render() metodunu çağırır. Artık render() metodundaki this.state.date‘in değeri eski halinden farklı olduğundan dolayı, render çıktısı güncellenmiş zamanı içerecek demektir. Buna göre React,  DOM’u ilgili şekilde günceller.
* Eğer Clock bileşeni, DOM’dan çıkarılırsa, yaşam döngüsündeki componentWillUnmount() metodu çağrılır ve tarayıcı tarafından zamanlayıcı durdurulmuş olur.
