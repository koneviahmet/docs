# prompts
terminalde select box işlemi yapmamızı sağlar

>  npm i --save prompts

neler yapabiliyorsun
* sırasıyla  terminalden bilgi alabiliyorsun
* aldığın bilgileri type belirleyerek validation ile doğrulama yaptırabiliyorsun
* text
* password
* invisible
* number
* confirm
* list
* toggle
* select
* multiselect
* autocompleteMultiselect
* autocomplete
* date

örnek 1
```js
const prompts = require('prompts');

/* sor cevapla 1 */
(async () => {
  const response = await prompts({
    type: 'number',
    name: 'value',
    message: 'How old are you?',
    validate: value => value < 18 ? `Nightclub is 18+ only` : true
  });

  console.log(response); // => { value: 24 }
})();
```

örnek 2
```js
const prompts = require('prompts');

/* sor cevapla 1 */
(async () => {
  const response = await prompts({
    type: 'number',
    name: 'value',
    message: 'How old are you?',
    validate: value => value < 18 ? `Nightclub is 18+ only` : true
  });

  const response2 = await prompts({
    type: 'number',
    name: 'value',
    message: 'masolsın',
    validate: value => value < 18 ? `Nightclub is 18+ only` : true
  });

  console.log(response); // => { value: 24 }
  console.log(response2); // => { value: 24 }
})();
```

örnek 3 arka arkaya soruyor
```js
const prompts = require('prompts');



const questions = [
  {
    type: 'text',
    name: 'username',
    message: 'What is your GitHub username?'
  },
  {
    type: 'number',
    name: 'age',
    message: 'How old are you?'
  },
  {
    type: 'text',
    name: 'about',
    message: 'Tell something about yourself',
    initial: 'Why should I?'
  }
];

(async () => {
  const response = await prompts(questions);

  console.log(response);
  // => response => { username, age, about }
})();
```


örnek 3
```js
const prompts = require('prompts');

const questions = [
  {
    type: 'text',
    name: 'dish',
    message: 'Do you like pizza?'
  },
  {
    type: prev => prev == 'pizza' ? 'text' : null,
    name: 'topping',
    message: 'Name a topping'
  }
];

(async () => {
  const response = await prompts(questions);
  console.log(response);
})();

```

çoklu seçmeli
```js
const prompts = require('prompts');
prompts.override(require('yargs').argv);

(async () => {
  const response = await prompts([
    {
      type: 'text',
      name: 'twitter',
      message: `What's your twitter handle?`
    },
    {
      type: 'multiselect',
      name: 'color',
      message: 'Pick colors',
      choices: [
        { title: 'Red', value: '#ff0000' },
        { title: 'Green', value: '#00ff00' },
        { title: 'Blue', value: '#0000ff' }
      ],
    }
  ]);

  console.log(response);
})();
```

tekli seçme
```js
const prompts = require('prompts');
prompts.override(require('yargs').argv);

(async () => {
  const response = await prompts([
    {
      type: 'text',
      name: 'twitter',
      message: `What's your twitter handle?`
    },
    {
      type: 'select',
      name: 'value',
      message: 'Pick a color',
      choices: [
        { title: 'Red', description: 'This option has a description', value: '#ff0000' },
        { title: 'Green', value: '#00ff00', disabled: true },
        { title: 'Blue', value: '#0000ff' }
      ],
      initial: 1
    }
  ]);

  console.log(response);
})();
```

bir sürü özellikler var typeri değiştirebiliyorsun yeni özellik atayabiliyorsun vs.
https://www.npmjs.com/package/prompts



## örnekler
```js
{
  type: 'text',
  name: 'value',
  message: `What's your twitter handle?`
}
```
![](https://github.com/terkelg/prompts/raw/master/media/text.gif)


```js
{
  type: 'password',
  name: 'value',
  message: 'Tell me a secret'
}
```

![](https://github.com/terkelg/prompts/raw/master/media/password.gif)



```js
{
  type: 'invisible',
  name: 'value',
  message: 'Enter password'
}
```

![](https://github.com/terkelg/prompts/raw/master/media/invisible.gif)


```js
{
  type: 'number',
  name: 'value',
  message: 'How old are you?',
  initial: 0,
  style: 'default',
  min: 2,
  max: 10
}
```

![](https://github.com/terkelg/prompts/raw/master/media/number.gif)

```js
{
  type: 'confirm',
  name: 'value',
  message: 'Can you confirm?',
  initial: true
}
```

![](https://github.com/terkelg/prompts/raw/master/media/confirm.gif)



```js
{
  type: 'list',
  name: 'value',
  message: 'Enter keywords',
  initial: '',
  separator: ','
}
```

![](https://github.com/terkelg/prompts/raw/master/media/list.gif)


```js
{
  type: 'toggle',
  name: 'value',
  message: 'Can you confirm?',
  initial: true,
  active: 'yes',
  inactive: 'no'
}
```

![](https://github.com/terkelg/prompts/raw/master/media/toggle.gif)

```js
{
  type: 'select',
  name: 'value',
  message: 'Pick a color',
  choices: [
    { title: 'Red', description: 'This option has a description', value: '#ff0000' },
    { title: 'Green', value: '#00ff00', disabled: true },
    { title: 'Blue', value: '#0000ff' }
  ],
  initial: 1
}
```

![](https://github.com/terkelg/prompts/raw/master/media/select.gif)


```js
{
  type: 'multiselect',
  name: 'value',
  message: 'Pick colors',
  choices: [
    { title: 'Red', value: '#ff0000' },
    { title: 'Green', value: '#00ff00', disabled: true },
    { title: 'Blue', value: '#0000ff', selected: true }
  ],
  max: 2,
  hint: '- Space to select. Return to submit'
}
```
![](https://github.com/terkelg/prompts/raw/master/media/multiselect.gif)



```js
{
  type: 'autocomplete',
  name: 'value',
  message: 'Pick your favorite actor',
  choices: [
    { title: 'Cage' },
    { title: 'Clooney', value: 'silver-fox' },
    { title: 'Gyllenhaal' },
    { title: 'Gibson' },
    { title: 'Grant' }
  ]
}

```

![](https://github.com/terkelg/prompts/raw/master/media/autocomplete.gif)


```js
{
  type: 'date',
  name: 'value',
  message: 'Pick a date',
  initial: new Date(1997, 09, 12),
  validate: date => date > Date.now() ? 'Not in the future' : true
}
```

![](https://github.com/terkelg/prompts/raw/master/media/date.gif)
