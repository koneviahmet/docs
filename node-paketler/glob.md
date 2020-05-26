# glob
belli bir sayfada bulunan istenilen formattaki dosyaların listesini almaya yarayan bir paket

https://www.npmjs.com/package/glob

> npm i glob


# örnek bir
sayfanın içindeki js dosyaları

```js
var glob = require("glob")

// options is optional
glob("jsler/*.js", {mark: true}, function (er, files) {
  // files is an array of filenames.
  // If the `nonull` option is set, and nothing
  // was found, then files is ["**/*.js"]
  // er is an error object or null.
  console.log(files);
})
```

brojedeik bütün jsleri alma


```js
var glob = require("glob")

// options is optional
glob("**/*.js", {mark: true}, function (er, files) {
  // files is an array of filenames.
  // If the `nonull` option is set, and nothing
  // was found, then files is ["**/*.js"]
  // er is an error object or null.
  console.log(files);
})
```

```
{mark: true},
```
option kısmı burada başka ayarlarda yapılabilir bakmakta fayda var



sitede şöyle bir örnek var pek anlamadım
```js
var Glob = require("../").Glob

var pattern = "test/a/**/[cg]/../[cg]"
console.log(pattern)

var mg = new Glob(pattern, {mark: true, sync:true}, function (er, matches) {
  console.log("matches", matches)
})
console.log("after")
```
