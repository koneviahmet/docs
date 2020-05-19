# stream
uzun videoları izlerken veya indirirken kullanılabilir.

```javascript
const fs = require('fs');
const file = 'video.mp4';

const readStream = fs.createReadStream(file);

/* dosyanın tam boyutunu öğrenme */
fs.state(file, (err, data) => {
  /* dosya boyutu */
  const total = data.size;
});

readStream.on('data', (chunk) => {
  /* okunan boyut */
  let boyut = chunk.length;
  console.log('bir veri geldi');
});

readStream.on('end', () => {
  console.log('veri okuma bitti');
});

```

# okunan dosyayı kaydetme
```javascript
const fs = require('fs');
const file = 'video.mp4';

const readStream = fs.createReadStream(file);
const writeStream = fs.createWriteStream("new.mp4");

/* dosyanın tam boyutunu öğrenme */
fs.state(file, (err, data) => {
  /* dosya boyutu */
  const total = data.size;
});

readStream.on('data', (chunk) => {
  /* okunan boyut */
  let boyut = chunk.length;
  console.log('bir veri geldi');
});

/* okuduklarını buraya yaz dedik */
readStream.pipe(writeStream);
readStream.on('end', () => {
  console.log('veri okuma bitti');
});

```
