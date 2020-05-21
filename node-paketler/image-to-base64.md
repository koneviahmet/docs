# image-to-base64

> npm i image-to-base64

sabit diskten
```js
const imageToBase64 = require('image-to-base64');

imageToBase64("img/araba.jpg") // you can also to use url
    .then(
        (response) => {
            console.log(response); //cGF0aC90by9maWxlLmpwZw==
        }
    )
    .catch(
        (error) => {
            console.log(error); //Exepection error....
        }
)
```

internetten
```js
const imageToBase64 = require('image-to-base64');

imageToBase64("https://www.karakterdukkani.com/ferrari-isikli-sesli-araba-2-arabalar-diger-karakterler-50958-28-B.jpg")
    .then(
        (response) => {
            console.log(response); //iVBORw0KGgoAAAANSwCAIA...
        }
    )
    .catch(
        (error) => {
            console.log(error); //Exepection error....
        }
    )
```
