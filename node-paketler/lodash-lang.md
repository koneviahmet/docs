# lodasg-lang



## castArray
verilen değeri diziye çevirir.

```js
_.castArray(1);
// => [1]

_.castArray({ 'a': 1 });
// => [{ 'a': 1 }]

_.castArray('abc');
// => ['abc']

_.castArray(null);
// => [null]

_.castArray(undefined);
// => [undefined]

_.castArray();
// => []

var array = [1, 2, 3];
console.log(_.castArray(array) === array);
// => true
```




## clone
diziyi kopyalar

```js
var objects = [{ 'a': 1 }, { 'b': 2 }];

var shallow = _.clone(objects);
console.log(shallow[0] === objects[0]);
// => true
```



## cloneDeep
diziyi kopyalarken anahtarlar almaz

```js
var objects = [{ 'a': 1 }, { 'b': 2 }];

var deep = _.cloneDeep(objects);
console.log(deep[0] === objects[0]);
// => false
```




## eq
iki değerin aynı olup olmadığını kıyaslar

```js
var object = { 'a': 1 };
var other = { 'a': 1 };

_.eq(object, object);
// => true

_.eq(object, other);
// => false

_.eq('a', 'a');
// => true

_.eq('a', Object('a'));
// => false

_.eq(NaN, NaN);
// => true
```




## gt
verilen iki değerin büyük olup olmadığını kontrol eder
gte => büyük eşit mi?

```js
_.gt(3, 1);
// => true

_.gt(3, 3);
// => false

_.gt(1, 3);
// => false
```


## isArguments
değerin arguma olup olmadığına bakar. Anladığım kadarıyla fonksiyon return veriyormu ona bakıyor.

```js
_.isArguments(function() { return arguments; }());
// => true

_.isArguments([1, 2, 3]);
// => false
```



## isArray
dizi mi kanka

```js
_.isArray([1, 2, 3]);
// => true
```


## isBoolean
mi ?

## isDate
mi ?


## isElement
element mi?

```js
_.isElement(document.body);
// => true

_.isElement('<body>');
// => false
```


## isEmpty
boş mu?

```js
_.isEmpty(null);
// => true

_.isEmpty(true);
// => true

_.isEmpty(1);
// => true

_.isEmpty([1, 2, 3]);
// => false

_.isEmpty({ 'a': 1 });
// => false
```


## isEqual
eşit mi

```js
var object = { 'a': 1 };
var other = { 'a': 1 };

_.isEqual(object, other);
// => true

object === other;
// => false
```

## isFunction
## isInteger
## isLength
integer değermi

## isMap

## isMatch
verilen dizide obje aramak için kullanılabilir.

```js
var object = { 'a': 1, 'b': 2 };

_.isMatch(object, { 'b': 2 });
// => true

_.isMatch(object, { 'b': 1 });
// => false
```

## isNaN
## isNil
null mu ?
```js
_.isNil(null);
// => true

_.isNil(void 0);
// => true

_.isNil(NaN);
// => false
```

## isNull
null mu ?
```js
_.isNull(null);
// => true

_.isNull(void 0);
// => false
```

## isNumber
## isObject
## isRegExp
regexp bir değermi

```js
_.isRegExp(/abc/);
// => true

_.isRegExp('/abc/');
// => false
```
## isString


## isUndefined
```js
_.isUndefined(void 0);
// => true

_.isUndefined(null);
// => false
```


## lt
küçük mü?
lte => kücük eşit mi?

```js
_.lt(1, 3);
// => true
```

## toArray
implode ile aynı
```js
_.toArray({ 'a': 1, 'b': 2 });
// => [1, 2]

_.toArray('abc');
// => ['a', 'b', 'c']

_.toArray(1);
// => []

_.toArray(null);
// => []
```



## toInteger
integere çevirir

```js
_.toInteger(3.2);
// => 3

_.toInteger(Number.MIN_VALUE);
// => 0

_.toInteger(Infinity);
// => 1.7976931348623157e+308

_.toInteger('3.2');
// => 3
```

## toNumber
numaraya çevirir

```js
_.toNumber(3.2);
// => 3.2

_.toNumber(Number.MIN_VALUE);
// => 5e-324

_.toNumber(Infinity);
// => Infinity

_.toNumber('3.2');
// => 3.2
```



## toString
String değere dönüştürür

```js
_.toString(null);
// => ''

_.toString(-0);
// => '-0'

_.toString([1, 2, 3]);
// => '1,2,3'
```






## taslak
açıklama

```js
#buraya kod
```
