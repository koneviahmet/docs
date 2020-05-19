# events
nodejs event mantığı ile çalışıyormuş mantık olay oluştur ve tetikle

on => oluştur <br />
emit => tetikle

```javascript
const events = require('events');
const eventEmitter = new events.EventEmitter();

eventEmitter.on('selamla', () => {
  console.log("selamun aleyküm kanka");
});

//yayınla
eventEmitter.emit('selamla');
eventEmitter.emit('selamla');
eventEmitter.emit('selamla');
```
