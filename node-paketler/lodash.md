# lodash

İçinde bir çok kütühaneyi barındıran lodash ile json datalar üzerinde arama, sıralama, silme gibi bir çok operasyonu rahatlıkla yapabilirsiniz.

https://lodash.com/docs/4.17.15#zip

ilginç :D
> npm install --save lodash

yazınca çalışmıyor ancak
> npm install --save Loadsh

yazınca çalışıyor anladığım kadarıyla aynı paket


## kullanım tablosu
  * chunk -> verilen diziyi gruplandırırı
  * compact -> false, null, 0, "", undefined, ve NaN gibi değerleri temizler
  * concat -> iki diziyi birleştirir
  * difference -> birinci diziyi referans alarak ikinci dizi ile ortak olmayanları yeni bir diziye aktarır.
  * drop -> n kadar öğeyi baştan başlayarak siler
  * dropRight -> n kadar öğeyi sondan başlayarak siler
  * dropRightWhile -> sondan başlayarak dizi içinde arama yapar ve kriterlere uyanları yeni dizi oluşturur
  * dropWhile -> baştan başlayarak dizi içinde arama yapar ve kriterlere uyanları yeni dizi oluşturur
  * fill -> diziyi istenilen değerle doldurur
  * findIndex -> dizide aranan değerin index ini döndürüyor
  * findLastIndex -> yukarıdakinin aynısı ancak sondan başlayarak arıyor.
  * flatten -> diziyi düzleştirir
  * flattenDeep -> diziyi sonuna kadar düzleştirir
  * fromPairs -> ikili grupları anahtar değer nesnesine dönüştürür
  * head -> dizinin ilk öğesini alır
  * indexOf -> dizide istenilen değerin indexini alır
  * initial -> dizinin son öğesi hariç hepsini alır
  * intersection -> iki dizide var olan ortak değerleri alır
  * intersectionBy -> float değerlerden virgülden sonraya bakmadan ortak olanları alır
  * join -> implode ile aynı işi yapıyor. diziyi string değere dönüştürüyor
  * last -> dizinin son elemanını alır.
  * lastIndexOf -> bu eleman indexOf ile aynıdır belirtilen bir elemanın indexini varir ancak bunu yapmaya sondan başlar
  * nth -> dizinin n inci elemanını alır. n index olarak verilecek. eksi verilirse sondan almaya başlar.
  * pull, pullAll, pullAllBy -> istenilen değerleri diziden kaldırır. siler pullAllBy => kaldırma işleminde anahar ilişkisine bakıyor. pullAt => index kullanarak kaldırma işlemi yapar ve kaldırdığı elemanları döner.
  * remove -> bir callback fonksiyonu sayesinde şarta uyan değerleri siler ve geriye silmediklerini döndürür.
  * reverse -> diziyi tersine çevirir.
  * slive -> diziyi indexlerine göre parçalar slice=> bölmek
  * sortedIndex -> sortedLastIndex is büyük kaçtane var ona bakıyor küçük kaçtane var ona bakıyor
  * sortedUniq -> tekrar eden elementleri (aynı) diziden çıkartır .uniq gibi sortedUniqBy => floor larda kullanılabilir.
  * tail -> dizinin ilk öğesi hariç diğerlerini alır.
  * take -> slice gibi diziyi istenilen kadar parçalara ayırır. bunu baştan başlayarak yapar takeRight => aynı işi sondan başlayarak yapar
  * takeWhile -> çoklu dizi içinde istenilen değerleri alarak yeni bir dizi oluşturur. takeRightWhile => tersten yapar
  * union, unionBy -> benzer elemanları silerek benzersiz hale getirir.
  * uniq, uniqBy -> tekrar eden elemanları siler
  * without -> Tekrar etmeyen elemanları alır
  * xor, xorBy -> Tekrar etmeyen değerleri alır































## chunk
verilen diziyi gruplandırırı

```javascript
_.chunk(['a', 'b', 'c', 'd'], 2);
// => [['a', 'b'], ['c', 'd']]

_.chunk(['a', 'b', 'c', 'd'], 3);
// => [['a', 'b', 'c'], ['d']]
```

## compact
false, null, 0, "", undefined, ve NaN gibi değerleri temizler

```javascrip
_.compact([0, 1, false, 2, '', 3]);
// => [1, 2, 3]
```


## concat
iki diziyi birleştirir

```javascrip
var array = [1];
var other = _.concat(array, 2, [3], [[4]]);

console.log(other);
// => [1, 2, 3, [4]]

console.log(array);
// => [1]
```


## difference
birinci diziyi referans alarak ikinci dizi ile ortak olmayanları yeni bir diziye aktarır.

```javascrip
_.difference([2, 1], [2, 3]);
// => [1]
```


## drop
n kadar öğeyi baştan başlayarak siler

```javascrip
_.drop([1, 2, 3]);
// => [2, 3]


_.drop([1, 2, 3], 2);
// => [3]
```



## dropRighy
n kadar öğeyi sondan başlayarak siler

```javascrip
_.dropRight([1, 2, 3]);
// => [1, 2]

_.dropRight([1, 2, 3], 2);
// => [1]
```


## dropRightWhile
sondan başlayarak dizi içinde arama yapar ve kriterlere uyanları yeni dizi oluşturur

```javascrip
var users = [
  { 'user': 'barney',  'active': true },
  { 'user': 'fred',    'active': false },
  { 'user': 'pebbles', 'active': false }
];

_.dropRightWhile(users, function(o) { return !o.active; });
// => objects for ['barney']

// The `_.matches` iteratee shorthand.
_.dropRightWhile(users, { 'user': 'pebbles', 'active': false });
// => objects for ['barney', 'fred']

// The `_.matchesProperty` iteratee shorthand.
_.dropRightWhile(users, ['active', false]);
// => objects for ['barney']

// The `_.property` iteratee shorthand.
_.dropRightWhile(users, 'active');
// => objects for ['barney', 'fred', 'pebbles']
```



## dropWhile
baştan başlayarak dizi içinde arama yapar ve kriterlere uyanları yeni dizi oluşturur


```javascrip
var users = [
  { 'user': 'barney',  'active': false },
  { 'user': 'fred',    'active': false },
  { 'user': 'pebbles', 'active': true }
];

_.dropWhile(users, function(o) { return !o.active; });
// => objects for ['pebbles']

// The `_.matches` iteratee shorthand.
_.dropWhile(users, { 'user': 'barney', 'active': false });
// => objects for ['fred', 'pebbles']

// The `_.matchesProperty` iteratee shorthand.
_.dropWhile(users, ['active', false]);
// => objects for ['pebbles']

// The `_.property` iteratee shorthand.
_.dropWhile(users, 'active');
// => objects for ['barney', 'fred', 'pebbles']
```

## fill
diziyi istenilen değerle doldurur

```javascrip
var array = [1, 2, 3];

_.fill(array, 'a');
console.log(array);
// => ['a', 'a', 'a']

_.fill(Array(3), 2);
// => [2, 2, 2]

_.fill([4, 6, 8, 10], '*', 1, 3);
// => [4, '*', '*', 10]
```


## findIndex
dizide aranan değerin index ini döndürüyor

```javascrip
var users = [
  { 'user': 'barney',  'active': false },
  { 'user': 'fred',    'active': false },
  { 'user': 'pebbles', 'active': true }
];

_.findIndex(users, function(o) { return o.user == 'barney'; });
// => 0

// The `_.matches` iteratee shorthand.
_.findIndex(users, { 'user': 'fred', 'active': false });
// => 1

// The `_.matchesProperty` iteratee shorthand.
_.findIndex(users, ['active', false]);
// => 0

// The `_.property` iteratee shorthand.
_.findIndex(users, 'active');
// => 2
```

## findLastIndex
yukarıdakinin aynısı ancak sondan başlayarak arıyor.



## flatten
diziyi düzleştirir

```javascrip
_.flatten([1, [2, [3, [4]], 5]]);
// => [1, 2, [3, [4]], 5]
```

## flattenDeep
diziyi sonuna kadar düzleştirir

```javascrip
_.flattenDeep([1, [2, [3, [4]], 5]]);
// => [1, 2, 3, 4, 5]
```

## fromPairs
ikili grupları anahtar değer nesnesine dönüştürür

```javascrip
_.fromPairs([['a', 1], ['b', 2]]);
// => { 'a': 1, 'b': 2 }
```

## head
dizinin ilk öğesini alır

```javascrip
_.head([1, 2, 3]);
// => 1
```



## indexOf
dizide istenilen değerin indexini alır

```javascrip
_.indexOf([1, 2, 1, 2], 2);
// => 1

// Search from the `fromIndex`.
_.indexOf([1, 2, 1, 2], 2, 2);
// => 3
```

## initial
dizinin son öğesi hariç hepsini alır

```javascrip
_.initial([1, 2, 3]);
// => [1, 2]
```


## intersection
iki dizide var olan ortak değerleri alır

```javascrip
_.intersection([2, 1], [2, 3]);
// => [2]
```



## intersectionBy
float değerlerden virgülden sonraya bakmadan ortak olanları alır

```javascrip
_.intersectionBy([2.1, 1.2], [2.3, 3.4], Math.floor);
// => [2.1]

// The `_.property` iteratee shorthand.
_.intersectionBy([{ 'x': 1 }], [{ 'x': 2 }, { 'x': 1 }], 'x');
// => [{ 'x': 1 }]
```


## join
implode ile aynı işi yapıyor. diziyi string değere dönüştürüyor

```javascrip
_.join(['a', 'b', 'c'], '~');
// => 'a~b~c'
```


## last
dizinin son elemanını alır.

```javascrip
_.last([1, 2, 3]);
// => 3
```

## lastIndexOf
bu eleman indexOf ile aynıdır belirtilen bir elemanın indexini varir ancak bunu yapmaya sondan başlar
```javascrip
_.lastIndexOf([1, 2, 1, 2], 2);
// => 3

// Search from the `fromIndex`.
_.lastIndexOf([1, 2, 1, 2], 2, 2);
// => 1
```

## nth
dizinin n inci elemanını alır. n index olarak verilecek. eksi verilirse sondan almaya başlar.

```javascrip
var array = ['a', 'b', 'c', 'd'];

_.nth(array, 1);
// => 'b'

_.nth(array, -2);
// => 'c';
```

## pull, pullAll, pullAllBy
istenilen değerleri diziden kaldırır. siler
pullAllBy => kaldırma işleminde anahar ilişkisine bakıyor.
pullAt    => index kullanarak kaldırma işlemi yapar ve kaldırdığı elemanları döner.

```javascrip
var array = ['a', 'b', 'c', 'a', 'b', 'c'];

_.pull(array, 'a', 'c');
console.log(array);
// => ['b', 'b']
```

```javascrip
var array = ['a', 'b', 'c', 'd'];
var pulled = _.pullAt(array, [1, 3]);

console.log(array);
// => ['a', 'c']

console.log(pulled);
// => ['b', 'd']
```

## remove
bir callback fonksiyonu sayesinde şarta uyan değerleri siler ve geriye silmediklerini döndürür.

```javascrip
var array = [1, 2, 3, 4];
var evens = _.remove(array, function(n) {
  return n % 2 == 0;
});

console.log(array);
// => [1, 3]

console.log(evens);
// => [2, 4]
```


## reverse
diziyi tersine çevirir.

```javascrip
var array = [1, 2, 3];

_.reverse(array);
// => [3, 2, 1]

console.log(array);
// => [3, 2, 1]
```


## slice
diziyi indexlerine göre parçalar slice=> bölmek

```javascrip
const animals = ['ant', 'bison', 'camel', 'duck', 'elephant'];

console.log(animals.slice(2));
// expected output: Array ["camel", "duck", "elephant"]

console.log(animals.slice(2, 4));
// expected output: Array ["camel", "duck"]

console.log(animals.slice(1, 5));
// expected output: Array ["bison", "camel", "duck", "elephant"]

```


## sortedIndex
=> sortedLastIndex is büyük kaçtane var ona bakıyor
küçük kaçtane var ona bakıyor

```javascrip
_.sortedIndex([30, 50], 60);
//60 tan küçük 2 tane olduğu için değer 2 olacak
```


## sortedUniq
tekrar eden elementleri (aynı)  diziden çıkartır .uniq gibi
sortedUniqBy => floor larda kullanılabilir.


```javascrip
_.sortedUniq([1, 1, 2]);
// => [1, 2]
```





## tail
dizinin ilk öğesi hariç diğerlerini alır.

```javascrip
_.tail([1, 2, 3]);
// => [2, 3]
```


## take
slice gibi diziyi istenilen kadar parçalara ayırır. bunu baştan başlayarak yapar
takeRight => aynı işi sondan başlayarak yapar

```javascrip
_.take([1, 2, 3]);
// => [1]

_.take([1, 2, 3], 2);
// => [1, 2]

_.take([1, 2, 3], 5);
// => [1, 2, 3]

_.take([1, 2, 3], 0);
// => []
```

## takeWhile
çoklu dizi içinde istenilen değerleri alarak yeni bir dizi oluşturur.
takeRightWhile => tersten yapar

```javascrip
var users = [
  { 'user': 'barney',  'active': false },
  { 'user': 'fred',    'active': false },
  { 'user': 'pebbles', 'active': true }
];

_.takeWhile(users, function(o) { return !o.active; });
// => objects for ['barney', 'fred']

// The `_.matches` iteratee shorthand.
_.takeWhile(users, { 'user': 'barney', 'active': false });
// => objects for ['barney']

// The `_.matchesProperty` iteratee shorthand.
_.takeWhile(users, ['active', false]);
// => objects for ['barney', 'fred']

// The `_.property` iteratee shorthand.
_.takeWhile(users, 'active');
// => []
```



## union, unionBy
benzer elemanları silerek benzersiz hale getirir.

```javascrip
_.union([2], [1, 2]);
// => [2, 1]

_.unionBy([2.1], [1.2, 2.3], Math.floor);
// => [2.1, 1.2]

// The `_.property` iteratee shorthand.
_.unionBy([{ 'x': 1 }], [{ 'x': 2 }, { 'x': 1 }], 'x');
// => [{ 'x': 1 }, { 'x': 2 }]
```

## uniq, uniqBy
tekrar eden elemanları siler

```javascrip
_.uniq([2, 1, 2]);
// => [2, 1]

_.uniqBy([2.1, 1.2, 2.3], Math.floor);
// => [2.1, 1.2]

// The `_.property` iteratee shorthand.
_.uniqBy([{ 'x': 1 }, { 'x': 2 }, { 'x': 1 }], 'x');
// => [{ 'x': 1 }, { 'x': 2 }]
```

## without
Tekrar etmeyen elemanları alır


```javascrip
_.without([2, 1, 2, 3], 1, 2);
// => [3]
```


## xor, xorby
Tekrar etmeyen değerleri alır

```javascrip
_.xor([2, 1], [2, 3]);
// => [1, 3]

_.xorBy([2.1, 1.2], [2.3, 3.4], Math.floor);
// => [1.2, 3.4]
```


## taslak
açıklama

```javascrip
#buraya kod
```





## taslak
açıklama

```javascrip
#buraya kod
```





















burada
