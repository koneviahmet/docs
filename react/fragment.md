# fragment kullanımı
> Fragmentler, Dom’a ekstra düğüm eklemeden bir alt elemanlar listesini gruplandırmanıza izin verir.

```javascript
render() {
  return (
    <React.Fragment>
      <ChildA />
      <ChildB />
      <ChildC />
    </React.Fragment>
  );
}

//kısa kullanımın
class Columns extends React.Component {
  render() {
    return (
      <>
        <td>Merhaba</td>
        <td>Dünya</td>
      </>
    );
  }
}

```

>Anahtarları veya nitelikleri desteklememesi dışında, diğer elementleri kullandığınız gibi <></> kullanabilirsiniz.

>Not, birçok araç henüz desteklemiyor. Bu nedenle, destekleninceye kadar <React.Fragment> yazmak isteyebilirsiniz.
