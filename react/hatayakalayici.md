# hata yakalayıcı

https://tr.reactjs.org/docs/error-boundaries.html

```JavaScript
class ErrorBoundary extends React.Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false };
  }

  static getDerivedStateFromError(error) {
    // Bir sonraki render'da son çare arayüzünü göstermek için
    // state'i güncelleyin.
    return { hasError: true };
  }
  componentDidCatch(error, errorInfo) {
    // Hatanızı bir hata bildirimi servisine de yollayabilirsiniz.
    logErrorToMyService(error, errorInfo);
  }

  render() {
    if (this.state.hasError) {
      // İstediğiniz herhangi bir son çare arayüzünü render edebilirsiniz.
      return <h1>Something went wrong.</h1>;
    }

    return this.props.children;
  }
}
```

kullanımı bu şekilde
```html
<ErrorBoundary>
  <MyWidget />
</ErrorBoundary>
```
