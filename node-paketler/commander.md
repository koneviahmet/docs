# commander

> node index yaz

yukarıdaki komutun yaz kısmını aktif hale getirir.

> ahmet-deneme topla

topla diyebilmemiz ve sistemin bunu algılaması için commander diye bir eklenti ekliyoruz.
burada commanderi dışarıdan dahil ettiğim için globale kaydetmelimiyim pek bilemedim
> npm i commander --save

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
