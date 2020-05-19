# MongoDB kurulum
windows için indir
https://www.mongodb.com/download-center/community

> dblerin ekleneceği bir dosya oluştur diyor

## kurulumda mongo --version çalışmazsa
- win ara => Ortam Değişkenleri
- path -> düzenle
-> yeni ekle => C:\Program Files\MongoDB\Server\4.2\bin \\mongodb pin yolu

```javascript
cd C:\
md "\data\db"
```
sonra başlattığın kısayola ekle bunu diyor
```javascript
"C:\Program Files\MongoDB\Server\4.2\bin\mongod.exe" --dbpath="c:\data\db"
```

yüklendimi kontrole etmek için
> mongo --version

## robomongo
mongo için grafik arayüzü sağlıyor.
https://robomongo.org/download

robomongo açışışında bağlanamadı gibi bir hata verirse
* win ara => hizmetler
* mongoDB serveri bul ve sağ tuş ile çalıştır de yani servisin çalışıyor olması gerekir.

## mongoose
veritabanına bağlanabilmek ve işlem yapabilmek için gerekli node paketi
https://mongoosejs.com/

>npm install mongoose --save
