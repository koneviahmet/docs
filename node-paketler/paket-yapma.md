# npm paket nasıl hazırlanır
dosya oluşutr
> mkdir deneme

dosyaya giriş yap
> cd deneme


package.json ekle
> npm init -y


* index.js dosyasını oluştur

package dosyasını aç bin dizini ekle
```js
"main": "index.js",
"bin": {
  "ahmet-deneme": "./index.js"
},
```


ahmet deneme paketin ismi olacak ve çağırıldığında index.js yi tetikleyecek


paketi kurmak için veya tekrar güncellemek için bu komudu kullancağız
> sudo npm i -g

merhaba dünya demesi için
> ahmet-deneme

söz dizilimi hatası verecek onu düzeltmek için index.js nin üst kısmına dizinin yolunu belirtmemiz lazım

```js
#!/usr/bin/env node
console.log("nerhaba dünya");
```

> ahmet-deneme topla

topla diyebilmemiz ve sistemin bunu algılaması için commander diye bir eklenti ekliyoruz.
burada commanderi dışarıdan dahil ettiğim için globale kaydetmelimiyim pek bilemedim
> npm i commander

index.js ye aşağıdaki kodu eklicez

burası önemli aşağıdaki kod js dosyaları çağırıyor
-> node index bol
yazdığımız zaman aslında index-bol.js dosyasını çağırıyor olacak


```js
#!/usr/bin/env node
const { program } = require('commander');
program.version('0.0.2');

program
  .version('0.1.0')
  .command('bol [name]', 'install one or more packages')
  .command('search [query]', 'search with optional query')
  .command('update', 'update installed packages', {executableFile: 'myUpdateSubCommand'})
  .command('topla', 'list packages installed', {isDefault: true})
  .parse(process.argv);
```
