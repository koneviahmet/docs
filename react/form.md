# react ile form kullanımı

> Formik paketini kullanmamızı öneriyor öğren

form verilerini tutmak için state leri kullanırız.
basit bir form kullanımı

//NOTE bu kusma mehmet sevenin kullandığı çoklu içerik ekleme fonksionunu ekle o çok kıyak.

```javascript
class NameForm extends React.Component {
  constructor(props) {
    super(props);
    this.state = {value: ''};

    this.handleChange = this.handleChange.bind(this);
    this.handleSubmit = this.handleSubmit.bind(this);
  }

  handleChange(event) {
    this.setState({value: event.target.value});
  }

  handleSubmit(event) {
    alert('A name was submitted: ' + this.state.value);
    event.preventDefault();
  }

  render() {
    return (
      <form onSubmit={this.handleSubmit}>
        <label>
          Name:
          <input type="text" value={this.state.value} onChange={this.handleChange} />
        </label>
        <input type="submit" value="Submit" />
      </form>
    );
  }
}
```

## textarea kullanımı
```javascript
class EssayForm extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      value: 'Bu kısma bir şeyler yazınız.'
    };

    this.handleChange = this.handleChange.bind(this);
    this.handleSubmit = this.handleSubmit.bind(this);
  }

  handleChange(event) {
    this.setState({value: event.target.value});
  }

  handleSubmit(event) {
    alert('Gönderilen değer: ' + this.state.value);
    event.preventDefault();
  }

  render() {
    return (
      <form onSubmit={this.handleSubmit}>
        <label>
          Essay:
          <textarea value={this.state.value} onChange={this.handleChange} />
        </label>
        <input type="submit" value="Gönder" />
      </form>
    );
  }
}
```

## select kullanımın
> Coconut seçeneğinin başlangıçta selected özelliği yüzünden seçili olarak geleceğini unutmayın. React, bu selected özelliğini kullanmak yerine, select etiketinde bir value özelliği kullanır.

```html
<select>
  <option value="grapefruit">Grapefruit</option>
  <option value="lime">Lime</option>
  <option selected value="coconut">Coconut</option>
  <option value="mango">Mango</option>
</select>
```

```javascript
class FlavorForm extends React.Component {
  constructor(props) {
    super(props);
    this.state = {value: 'havuç'};

    this.handleChange = this.handleChange.bind(this);
    this.handleSubmit = this.handleSubmit.bind(this);
  }

  handleChange(event) {
    this.setState({value: event.target.value});
  }

  handleSubmit(event) {
    alert('Favori meyveniz: ' + this.state.value);
    event.preventDefault();
  }

  render() {
    return (
      <form onSubmit={this.handleSubmit}>
        <label>
          Favori meyveni seç:
          <select value={this.state.value} onChange={this.handleChange}>
            <option value="elma">Elma</option>
            <option value="armut">Armut</option>
            <option value="havuç">Havuç</option>
            <option value="muz">Muz</option>
          </select>
        </label>
        <input type="submit" value="Gönder" />
      </form>
    );
  }
}
```

multible kullanımı
```html
<select multiple={true} value={['B', 'C']}>
```

>input value yi null yaparak girişleri denetleyebilirisniz.

```javascript
<input value={null} />
```
