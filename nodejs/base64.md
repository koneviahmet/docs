## fs kullanarak resmi base64 e çevirme

```js
const fs = require('fs');
const image       = fs.readFileSync('./image.png');
const base64Image = new Buffer.from(image).toString('base64');
const dataURI     = 'data:image/jpeg;base64,' + base64Image
```


## axios base64
```js

function getBase64(url) {
  return axios
    .get(url, {
      responseType: 'arraybuffer'
    })
    .then(response => new Buffer(response.data, 'binary').toString('base64'))
}
```
