# sunucu oluşturma

```javascript
const http = require('http');
const fs = require('fs');

const server = http.createServer((request, response) => {
  console.log("bir istekte bulunuldu");

  /* isteğin detayları burada*/
  console.log(request);
  console.log(request.headers);



  /* html dosyasını göndermek istersek */
  fs.readFile('index.html', (err, data) => {
    if(err)
      throw err;

    response.end(data);  
  });

  response.writeHead(200, {'content-type':'text/html; charset=utf-8'});
  response.write("Merhaba dünya");
  response.end();
});

server.listen(3000);
```

## http methodları
* GET
* POST
* PUT
* DELETE

```javascript
//sunucnunun hangi method ile veri gönderdiğini anlamak için
request.method === "GET"
```
