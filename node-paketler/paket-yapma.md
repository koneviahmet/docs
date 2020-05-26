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


## önemli
yaptığın paketi başka bir dizinde açtığın zaman o dizinin url ini almak için kullanılacak kod

```js
let dizin = process.env.PWD;
```
