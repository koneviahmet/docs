# hooklar
> Hook’lar React 16.8’deki yeni bir eklentidir. Bir sınıf yazmadan state ve diğer React özelliklerini kullanmanıza olanak sağlarlar.

hook => kanca

> Hook’lar class’ların içerisinde çalışmazlar React’ı class’lar olmadan kullanmanıza yararlar

>Effect Hook’u; useEffect, fonksiyonel bir bileşene yan etkileri kullanabilme yetkisini ekler. React class’larındaki componentDidMount, componentDidUpdate, ve componentWillUnmount ile aynı işleve sahiptir fakat tek bir API içerisinde birleştirilmiştir.


## hook kuralları
* hook companentleri artık sınıf şeklinde değil fonksiyon şeklinde olması gerekkir
* Hook’ları Sadece En Üst Seviyede Çağırın
* Döngülerde, koşullarda veya iç içe geçmiş fonksiyonlarda Hook çağrısı yapmayın


```javascript
import React, { useState } from 'react';

function Example() {
  // "count" diyeceğimiz yeni bir state değişkeni tanımlayın
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

useEffect ile update stati yakalama
```javascript
import React, { useState, useEffect } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  // Similar to componentDidMount and componentDidUpdate:
  useEffect(() => {
    // Update the document title using the browser API
    document.title = `You clicked ${count} times`;
  });

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

önemli
> useEffect ikinci bir paramatre atayrak istediğimiz statelerin değişme durumuna göre update olmasını sağlayabiliyoruz.

burada anlatmış eleman
https://www.youtube.com/watch?v=XIJL0r7I3kk

useEffect yerine useLayoutEffect te kullanabilir aradaki farklar
* useEffect sayfa renderi bitince çalışır
* useLayoutEffect renderi beklemeden çalışır
https://www.youtube.com/watch?v=7O9qQzkqbhI

> İsteğe bağlı olarak Efect’lerin nasıl kendi “arkalarını toplayacakları”, bir fonksiyon döndürülerek belirtilebilir. Örneğin, bu bileşen bir effect kullanarak, bir arkadaşın online bilgisine bağlanıyor ve kendi arkasını bu bağlantıyı kapatarak topluyor:

```javascript
import React, { useState, useEffect } from 'react';

function FriendStatus(props) {
  const [isOnline, setIsOnline] = useState(null);

  function handleStatusChange(status) {
    setIsOnline(status.isOnline);
  }

  useEffect(() => {
    ChatAPI.subscribeToFriendStatus(props.friend.id, handleStatusChange);
    return () => {
      ChatAPI.unsubscribeFromFriendStatus(props.friend.id, handleStatusChange);
    };
  });

  if (isOnline === null) {
    return 'Loading...';
  }
  return isOnline ? 'Online' : 'Offline';
}
```

```javascript
const Example = (props) => {
  // Hook'ları burada kullanabilirsiniz!
  return <div />;
}
```

anlamadım iç içe hook kullanmaktan bahsediyor ama tam anlamadım

>Peki React, hangi state’in hangi useState çağrısına karşılık geldiğini nasıl biliyor? Cevap, React’in Hook’ların çağrılma sırasına dayalı olmasıdır. Örneğimiz çalışıyor çünkü Hook çağrılarının sırası her render etmede aynı:

```javascript
function Form() {
  // 1. name state değişkenini kullan
  const [name, setName] = useState('Onur');

  // 2. Formun devamlılığını sağlamak için bir efekt kullan
  useEffect(function persistForm() {
    localStorage.setItem('formData', name);
  });

  // 3. surname state değişkenini kullan
  const [surname, setSurname] = useState('Şuyalçınkaya');

  // 4. Başlığı güncellemek için bir efekt kullan
  useEffect(function updateTitle() {
    document.title = name + ' ' + surname;
  });

  // ...
}
```

kural hatası


```javascript
// 🔴 Bir koşul içerisinde Hook kullanarak ilk kuralı çiğniyoruz
if (name !== '') {
  useEffect(function persistForm() {
    localStorage.setItem('formData', name);
  });
}
```
doğru kullanım
```javascript
useEffect(function persistForm() {
    // 👍 Artık ilk kuralı çiğnemiyoruz
    if (name !== '') {
      localStorage.setItem('formData', name);
    }
  });
```
