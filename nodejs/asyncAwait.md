# async - await yapısı

> async altında bulunan fonksiyon ları sıraya koymak için kullanılıyor. örneğin alttaki fonksiyonda asenkron içindeki fonksiyonlar sırasıyla biri bitmeden diğeri çalışmayacak şekilde çalışacaklar.


```javascript
const getFriends = (userId) => {
  return new Promise((resolve, reject){
    resolve("hayda hobba");


    //buradab hata fırlatırsak
    //Buradaki hatayı yakalamak için asyn içindeki await fonksiyonlarını try catch yapısında kullanmamız gerekir
    reject("hata kanka");
  });
}

async function asenkronFonksiyon (){  
  const user = await getUser();
  const friends = await getFriends(user.id);
}
```

## hata yakalama
