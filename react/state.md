# State
State kullanım örneği

statenin constructor da kullanımı
```javascript
constructor(props) {
  super(props);
  this.state = {
    posts: [],
    comments: []
  };
}
```

set statenin güncellenmesi
```javascript
componentDidMount() {
   fetchPosts().then(response => {
     this.setState({
       posts: response.posts
     });
   });

   fetchComments().then(response => {
     this.setState({
       comments: response.comments
     });
   });
 }
 ```

 statenin alt bileşenlere aktarılması
 ```javascript
 <h2>It is {this.state.date.toLocaleTimeString()}.</h2>
 ```
 
```javascript
class Clock extends React.Component {
  constructor(props) {
    super(props);
    this.state = {date: new Date()};
  }

  componentDidMount() {
  }

  componentWillUnmount() {
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
```

> bir companenetin yaşam döngüsüne [yaşam döngüsü](react/companentyasamdongusu.md)

# statenin doğru kullanımı
setState() hakkında bilmeniz gereken 3 şey bulunmaktadır.

* State’i Doğrudan Değiştirmeyiniz
```javascript
// Yanlış kullanım
this.state.comment = 'Hello';
```

Bunun yerine setState() kullanınız:
```javascript
// Doğru kullanım
this.setState({comment: 'Hello'});
```
* this.state‘e atama yapmanız gereken tek yer, ilgili bileşenin constructor’ıdır.
* State Güncellemeleri Asenkron Olabilir
```javascript
// Yanlış kullanım
this.setState({
  counter: this.state.counter + this.props.increment,
});
```

```javascript
// Doğru kullanım
this.setState((state, props) => ({
  counter: state.counter + props.increment
}));
```
