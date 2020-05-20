# lodash collection
Loadsh kütüphanesine devam ediyoruz



 * countBy -> elemanlardan kaçartane var onu sayar
 * forEach, forEachRight -> dizideki elementleri basar
 * filter -> çoklu dizilere filtre uygular ve onları döndürmemizi sağlar.
 * find -> çoklu dizi içinde istenilen değerlere göre arama yapmamızı sağlar
 * includes -> aranılan değer dizide varmı ona bakar
 * invokeMap -> çoklu diziler içinde ayrı ayrı sıralama yapar
 * map -> diziyi verilen fonksiyona göre tekrar düzenler
 * orderBy -> pek anlamadım ama bir sıralama olayı var
 * partition -> istenilen değerlere göre gruplandırma yapar
 * reject -> çoklu dizilerde şartı sağlamayan objeleri yakalar
 * sample -> kolleksiyondan rasgele bir değer döndürür.
 * sampleSize -> kolesksiyondan istenilen değer kadar rasgele değer döndürür.
 * shuffle -> kolleksiyonu karıştırır.
 * size -> kolleksiyonda kaçtane eleman olduğunu hesaplar string değerlerde de length gibi davranır.
 * some -> çoklu dizilerde istenilen değerlerde eleman varmı onu kontrol eder.
 * sortBy -> çoklu dizileri istenilen değerlere göre sıralar
 * now -> timeslamb zamanı verir











## countBy
elemanlardan kaçartane var onu sayar

```js
_.countBy([6.1, 4.2, 6.3], Math.floor);
// 4 ile başlayan 1 tane
// 6 ile başlayan 2 tane var demek
// => { '4': 1, '6': 2 }



// The `_.property` iteratee shorthand.
_.countBy(['one', 'two', 'three'], 'length');
// => { '3': 2, '5': 1 }
// 3 kelimeli 2 tane var
// 5 kelimeli 1 tane var
```




## forEach, forEachRight
dizideki elementleri basar

```js
_.forEach([1, 2], function(value) {
  console.log(value);
});
// => Logs `1` then `2`.

_.forEach({ 'a': 1, 'b': 2 }, function(value, key) {
  console.log(key);
});
// => Logs 'a' then 'b' (iteration order is not guaranteed).
```


## filter
çoklu dizilere filtre uygular ve onları döndürmemizi sağlar.

```js
var users = [
  { 'user': 'barney', 'age': 36, 'active': true },
  { 'user': 'fred',   'age': 40, 'active': false }
];

_.filter(users, function(o) { return !o.active; });
// => objects for ['fred']

// The `_.matches` iteratee shorthand.
_.filter(users, { 'age': 36, 'active': true });
// => objects for ['barney']

// The `_.matchesProperty` iteratee shorthand.
_.filter(users, ['active', false]);
// => objects for ['fred']

// The `_.property` iteratee shorthand.
_.filter(users, 'active');
// => objects for ['barney']
```




## find
çoklu dizi içinde istenilen değerlere göre arama yapmamızı sağlar

```js
var users = [
  { 'user': 'barney',  'age': 36, 'active': true },
  { 'user': 'fred',    'age': 40, 'active': false },
  { 'user': 'pebbles', 'age': 1,  'active': true }
];

_.find(users, function(o) { return o.age < 40; });
// => object for 'barney'

// The `_.matches` iteratee shorthand.
_.find(users, { 'age': 1, 'active': true });
// => object for 'pebbles'

// The `_.matchesProperty` iteratee shorthand.
_.find(users, ['active', false]);
// => object for 'fred'

// The `_.property` iteratee shorthand.
_.find(users, 'active');
// => object for 'barney'
```



## includes
aranılan değer dizide varmı ona bakar

```js
_.includes([1, 2, 3], 1);
// => true

_.includes([1, 2, 3], 1, 2);
// => false

_.includes({ 'a': 1, 'b': 2 }, 1);
// => true

_.includes('abcd', 'bc');
// => true
```




## invokeMap
çoklu diziler içinde ayrı ayrı sıralama yapar

```js
_.invokeMap([[5, 1, 7], [3, 2, 1]], 'sort');
// => [[1, 5, 7], [1, 2, 3]]

_.invokeMap([123, 456], String.prototype.split, '');
// => [['1', '2', '3'], ['4', '5', '6']]
```




## map
diziyi verilen fonksiyona göre tekrar düzenler

```js
function square(n) {
  return n * n;
}

_.map([4, 8], square);
// => [16, 64]

_.map({ 'a': 4, 'b': 8 }, square);
// => [16, 64] (iteration order is not guaranteed)

var users = [
  { 'user': 'barney' },
  { 'user': 'fred' }
];

// The `_.property` iteratee shorthand.
_.map(users, 'user');
// => ['barney', 'fred']
```




## orderBy
pek anlamadım ama bir sıralama olayı var

```js
var users = [
  { 'user': 'fred',   'age': 48 },
  { 'user': 'barney', 'age': 34 },
  { 'user': 'fred',   'age': 40 },
  { 'user': 'barney', 'age': 36 }
];

// Sort by `user` in ascending order and by `age` in descending order.
_.orderBy(users, ['user', 'age'], ['asc', 'desc']);
// => objects for [['barney', 36], ['barney', 34], ['fred', 48], ['fred', 40]]
```




## partition
istenilen değerlere göre gruplandırma yapar

```js
var users = [
  { 'user': 'barney',  'age': 36, 'active': false },
  { 'user': 'fred',    'age': 40, 'active': true },
  { 'user': 'pebbles', 'age': 1,  'active': false }
];

_.partition(users, function(o) { return o.active; });
// => objects for [['fred'], ['barney', 'pebbles']]

// The `_.matches` iteratee shorthand.
_.partition(users, { 'age': 1, 'active': false });
// => objects for [['pebbles'], ['barney', 'fred']]

// The `_.matchesProperty` iteratee shorthand.
_.partition(users, ['active', false]);
// => objects for [['barney', 'pebbles'], ['fred']]

// The `_.property` iteratee shorthand.
_.partition(users, 'active');
// => objects for [['fred'], ['barney', 'pebbles']]
```


## reject
çoklu dizilerde şartı sağlamayan objeleri yakalar

```js
var users = [
  { 'user': 'barney', 'age': 36, 'active': false },
  { 'user': 'fred',   'age': 40, 'active': true }
];

_.reject(users, function(o) { return !o.active; });
// => objects for ['fred']

// The `_.matches` iteratee shorthand.
_.reject(users, { 'age': 40, 'active': true });
// => objects for ['barney']

// The `_.matchesProperty` iteratee shorthand.
_.reject(users, ['active', false]);
// => objects for ['fred']

// The `_.property` iteratee shorthand.
_.reject(users, 'active');
// => objects for ['barney']
```



## sample
kolleksiyondan rasgele bir değer döndürür.

```js
_.sample([1, 2, 3, 4]);
// => 2
```



## sampleSize
kolesksiyondan istenilen değer kadar rasgele değer döndürür.

```js
_.sampleSize([1, 2, 3], 2);
// => [3, 1]

_.sampleSize([1, 2, 3], 4);
// => [2, 3, 1]
```




## shuffle
kolleksiyonu karıştırır.

```js
_.shuffle([1, 2, 3, 4]);
// => [4, 1, 3, 2]
```




## size
kolleksiyonda kaçtane eleman olduğunu hesaplar string değerlerde de length gibi davranır.

```js
_.size([1, 2, 3]);
// => 3

_.size({ 'a': 1, 'b': 2 });
// => 2

_.size('pebbles');
// => 7
```


## some
çoklu  dizilerde istenilen değerlerde eleman varmı onu kontrol eder.

```js
_.some([null, 0, 'yes', false], Boolean);
// => true

var users = [
  { 'user': 'barney', 'active': true },
  { 'user': 'fred',   'active': false }
];

// The `_.matches` iteratee shorthand.
_.some(users, { 'user': 'barney', 'active': false });
// => false

// The `_.matchesProperty` iteratee shorthand.
_.some(users, ['active', false]);
// => true

// The `_.property` iteratee shorthand.
_.some(users, 'active');
// => true
```




## sortBy
çoklu dizileri istenilen değerlere göre sıralar

```js
var users = [
  { 'user': 'fred',   'age': 48 },
  { 'user': 'barney', 'age': 36 },
  { 'user': 'fred',   'age': 40 },
  { 'user': 'barney', 'age': 34 }
];

_.sortBy(users, [function(o) { return o.user; }]);
// => objects for [['barney', 36], ['barney', 34], ['fred', 48], ['fred', 40]]

_.sortBy(users, ['user', 'age']);
// => objects for [['barney', 34], ['barney', 36], ['fred', 40], ['fred', 48]]
```




## now
timeslamb zamanı verir

```js
_.now());
```





## taslak
açıklama

```js
#buraya kod
```















burada
