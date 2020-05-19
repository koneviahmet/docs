# schema oluşturma
https://www.udemy.com/course/nodejs-egitimi/learn/lecture/8747376#overview
örnek şema

```javascript
const mongoose  = require('mongoose');
const Schema    = mongoose.Schema;


const BookSchema = new Schema({
    title: String
});

module.exports = mongoose.model('book', BookSchema);
```

# import ve kayıt için

şemayı import etmek için
```javascript
//şemayı al
const Book = require('../models/Book');

//kaydetmek için
const book = new Book({
   title: "Selam Dünya ben geldim :)"
});

//kaydetmek için
book.save((err, data) => {
    if(err)
        console.log(err);

    /* hata yoksa ekrana basalım*/
    res.json(data);
})
```

## şemeda validation yapma yani sınırlandırma
```javascript
const BookSchema = new Schema({
    title: {
      type: String,
      required: true, //olması gerekir
      unique: true, //benzersiz olsun
      maxLength: 20,
      minLength: [5, '{PATH} alanı zorunlu. girilen {VALUE}  en az {MINLENGTH} değer almalı'],
      max: 2030,
      min: 2010
    }
});
```

## veri tipleri
```javascript
const book = new Book({
   title: "Selam Dünya ben geldim :)",
    published: false,
    comments: [
        {message: "harika bir kitap"},
        {message: "hadi len bir kitap"}
        ],
    meta: {
        votes: 101,
        favs: 15
    }

});

//şema
const BookSchema = new Schema({
    /*
    * şemada kullanılabilecek veri tipleri
    * String
    * Boolean
    * array []
    * nesne {}
    * Number
    * Date
    * ...
    * */
    title: String,
    published: Boolean,
    comments: [{message: String}],
    meta: {
        votes: Number,
        favs: Number
    }

});

```

## Mongoose şemalar type, Default, Required, Unique
* Unique => benzersiz olmalı
* default => varsayılan olarak ekle demek
* required => gereki olmazsa olmaz eklemelisin

bu değerler şemalar içinde kullanılır
```javascript
//default
...
title: String,
published: {
    type: Boolean,
    default: false
},
zaman: {
    type: Date,
    default: Date.now
},
comments: [{message: String}],
...

/* required */
...
title: {
  type: String,
  required: true
},
...

/* unique */
...
email: {
  type: String,
  required: true,
  unique: true
},
...
```

# arama yapma



```javascript
//şemayı dahil edelim
const Book = require('../models/Book');

/* published (yayınlanan) false olanları bul getir dedik */
Book.find({published: false}, (err, data) => {
    res.json(data);
});


/* birden değerde arama yapmak için*/
Book.find({published: false, digerKriterler}, (err, data) => {
    res.json(data);
});


/*
sdece yorumları ve titleyi almak için
ikinci paremetreye ihtiyaç duyuyuoruz
*/
Book.find({published: false}, 'title comments', (err, data) => {
    res.json(data);
});

/* bütün kayıtları almak için */
Book.find({}, 'title comments', (err, data) => {
    res.json(data);
});

/*
tek veri çekmek için
find tamamını tarar ancak findOne bulduğu zaman aramayı durdurur.
*/
Book.findOne({published: false}, 'comments', (err, data) => {
    res.json(data);
});

/*
id bazlı arama
bütün tabloda arama yapmadan direk gider alır gelir.
*/
Book.findById('idburaya', (err, data) => {
    res.json(data);
});
```

## update
```javascript
//published true olanları false yap dedik ancak update sadece 1 tanesini değiştirir.
Book.update({published: true}, {published: false}, (err, data) => {
    res.json(data);
});


//tamamını güncellemek için
Book.update({published: true}, {published: false}, {multi: true}, (err, data) => {
    res.json(data);
});

//upsert true yaparsak eğer published değeri yoksa ekler
Book.update({published: true}, {published: false}, {upsert: true}, (err, data) => {
    res.json(data);
});

/* id göre düzenleme */
Book.findByIdAndUpdate('5e9b49dc8c0c4a0fbc81bbab', {'meta.favs': 115, title: "ol len"}, (err, data) => {
    res.json(data);
});

```

## silme işlemi
silme işlemi iki şekilde yapılabiliyor
* bul ve sil
* direk sil

```javascript
//bul ve sil
Book.findById('5e9b49dc8c0c4a0fbc81bbab', (err, book) => {
    book.remove((err, data) => {
        res.json(data);
    })
});

//bir tane bul ve sil
Book.findOneAndRemove({_id:'5e9b49eb8c0c4a0fbc81bbae'}, (err, data) => {
    res.json(data);
});

//kriterlere uyanların hepsinisil
Book.remove({_id:'5e9b49eb8c0c4a0fbc81bbae'}, (err, data) => {
    res.json(data);
});
```


## sıralama
```javascript
//küçükten büyüğe
Book.find({}, (err, data) => {
    res.json(data);
}).sort({'meta.favs': 1});

//büyükten küçüğe
Book.find({}, (err, data) => {
    res.json(data);
}).sort({'meta.favs': -1});
```


## limit belirleme
* limit
* skip

```javascript
Book.find({}, (err, data) => {
    res.json(data);
}).limit(1);

//skipte 2 tane geç oyle göster demek
//2. başlayarak göster demek
Book.find({}, (err, data) => {
    res.json(data);
}).skip(2).limit(1);
```

## kümeleme işlemleri
* $match => eşleşenleri getir demek
* $group => gruplandırma işlemleri yapar
* $project => selectin ta kendisi istenilen alanları getirir
* $sort, $limit, $skip
* $lookup => iki tabloyu birbirine bağlar
* $exist => aramalara filtre koyar

```javascript
Book.aggregate([
    {
        $match: {
            published: true
        }
    }
],(err, data) => {
    res.json(data);
});
```

burası güzel burada aslında select içinde sum yaptık yani her kategoride kaç kitap var onu adete yazdırdık
```javascript
Book.aggregate([
    {
        $match: {
            published: true
        }
    },
    {
        $group: {
            _id: "$catagory",
            adet: {$sum: 1} //1 er 1 er topla demek
        }
    }
],(err, data) => {
    res.json(data);
});
```

sadece title leri göster demek için project kullandık
```javascript
Book.aggregate([
    {
        $match: {
            published: true
        }
    },
    {
        $project: {
            title: true
        }
    }
],(err, data) => {
    res.json(data);
});
```

//sıralama işlemleri
```javascript
Book.aggregate([
    {
        $match: {
            published: true
        }
    },
    {
        $sort: {title: -1}
    },
    {
        $limit: 2
    },
    {
        $skip: 2
    }
],(err, data) => {
    res.json(data);
});
```

## inner join işlemi
https://www.udemy.com/course/nodejs-egitimi/learn/lecture/8747396#overview

sadece lookup kısmıda işimi görür ancak diğer kısımlarda ikinci tablodan hangi değişkenlerin gelebileceklerini belirleyebiliyoruz.

```javascript
Book.aggregate([
    {
        $lookup: {
            from: 'users',
            localField: 'userId',
            foreignField: '_id',
            as: 'kullanici'

        }
    },
    {
        $unwind: '$user'
    },
    {
        $project: {
            title: 1,
            user: '$user'
        }
    }

],(err, data) => {
    res.json(data);
});
```


## kümelemede object id olarak arama yapma
```javascript
const mongoose  = require('mongoose');

{
    $match: {
        _id: mongoose.Types.ObjectId('idolacakasda');
    }
}

```

## exist kullanımı

$exists: true ile kategorisi olanları getir dedik

```javascript
Book.find({
  category: {
    $exists: true
  }
}, (err, data) => {
    res.json(data);
});
```


```javascript
#kod
```
