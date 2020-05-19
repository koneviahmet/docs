# import kullanım örnekleri
```JavaScript

```

```JavaScript
// math.js
export function add(a, b) {
  return a + b;
}

// app.js
import { add } from './math.js';

console.log(add(16, 26)); // 42
```

> porplar yüklenirken sayfada yükleniyru göstermek için Suspense diye bir method kullanıyoruz. bu Suspense yi yukarıda kullanmamız gerekiyor

Suspense  => belirsizlik demek

```JavaScript
import React, { Suspense } from 'react';

//companenetleri lizy ile aktarmamızı tavsiye ediyor.
const OtherComponent = React.lazy(() => import('./OtherComponent'));

function MyComponent() {
  return (
    <div>
      <Suspense fallback={<div>Yükleniyor...</div>}>
        <OtherComponent />
      </Suspense>
    </div>
  );
}
```

//import MyErrorBoundary from './MyErrorBoundary';
https://tr.reactjs.org/docs/code-splitting.html u kısımda hata eğer companenet yüklenmezse diye bir kısım var ama anlamadım bu kısmı

* [lazy routers](react/routes.md) lazy ile import ve sayfalama nasıl yapılır için buraya bakabilirsiniz.


## import örnek

```JavaScript
//theme-context.js

export const themes = {
  light: {
    foreground: '#000000',
    background: '#eeeeee',
  },
  dark: {
    foreground: '#ffffff',
    background: '#222222',
  },
};

export const ThemeContext = React.createContext(
  themes.dark // varsayılan değer
);
```

```JavaScript
//app.js

import {ThemeContext} from './theme-context';

class ThemedButton extends React.Component {
  render() {
    let props = this.props;
    let theme = this.context;
    return (
      <button
        {...props}
        style={{backgroundColor: theme.background}}
      />
    );
  }
}
ThemedButton.contextType = ThemeContext;

export default ThemedButton;
```

```JavaScript
//themed-button.js

import {ThemeContext, themes} from './theme-context';
import ThemedButton from './themed-button';

// ThemedButton'u kullanan bir ara bileşen
function Toolbar(props) {
  return (
    <ThemedButton onClick={props.changeTheme}>
      Change Theme
    </ThemedButton>
  );
}

class App extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      theme: themes.light,
    };

    this.toggleTheme = () => {
      this.setState(state => ({
        theme:
          state.theme === themes.dark
            ? themes.light
            : themes.dark,
      }));
    };
  }

  render() {
    // ThemeProvider içinde bulunan ThemedButton
    // tema bilgisini state'ten alır. Dışarıda bulunan ise
    // varsayılan temayı kullanır.
    return (
      <Page>
        <ThemeContext.Provider value={this.state.theme}>
          <Toolbar changeTheme={this.toggleTheme} />
        </ThemeContext.Provider>
        <Section>
          <ThemedButton />
        </Section>
      </Page>
    );
  }
}

ReactDOM.render(<App />, document.root);
```
