---
title: Generátor hesel
demand: 3
context: lekce
lead: Vyrobte stránku na generování silných hesel.
solutionAccess: protected
---

Vyrobte stránku, která pomůže uživateli vygenerovat opravdu silné a neprůstřelné heslo. Použijte k tomu veřejné API na [psswrd.net](https://www.psswrd.net/api/v1/password/?length=17) na generování hesel. Zároveň už projekt vytvořte pomocí Vite a JSX.

1. Založte si nový projekt příkazem

   ```shell
   npm init kodim-app@latest cviceni-generator-hesel jsx
   ```

1. Otevřete si ve VS Code vytvořenou složku `cviceni-generator-hesel`.
1. Prohlédněte si URL endpointu pro generování hesla a vyzkoušejte si jej „na sucho“ v prohlížeči. Zkuste vygenerovat hesla různých délek a prohlédněte si, jak vypadá struktura dat, která API vrací.
1. V hlavním `index.jsx` promažte JSX ve funkci `render`. Nechte na stránce pouze prvek `.container` a nadpis `h1`.
1. Před voláním funkce `render` vytvořte proměnnou `data`, do které si pomocí volání `fetch` na tréninkové API uložíte vygenerované heslo délky 12.
1. Upravte JSX ve funkci `render` tak, aby zobrazila uživateli vygenerované heslo s nějakým vhodným textem pro uživatele.

### Bonus

1. Vytvořte pro zobrazení heslo komponentu `StrongPassword`, která bude mít dvě `props` s názvem `password` a `length`. Tuto komponentu pak použijte ve funkci `render`.
1. Nezapomeňte pro komponentu vytvořit vlastní složku ve složce `src/components` a správně ji importujte.

:::solution

Soubor `index.jsx`:

```jsx
import { render } from '@czechitas/render';
import '../global.css';
import './index.css';

const response = await fetch(
  'https://api.genratr.com/?length=12&uppercase&lowercase&special&numbers'
);
const json = await response.json();

document.querySelector('#root').innerHTML = render(
  <div className="container">
    <h1>Webová aplikace</h1>
    <p>Vaše heslo je: {json.password}, délka: 12</p>
  </div>
);
```

#### Bonus

Soubor `src/components/StrongPassword/index.jsx`:

```jsx
export const StrongPassword = (props) => {
  return (
    <p>
      Vaše heslo je: {props.password}, délka: {props.length}
    </p>
  );
};
```

Soubor `src/pages/index.jsx`:

```jsx
import { render } from '@czechitas/render';
import { StrongPassword } from '../components/StrongPassword';
import '../global.css';
import './index.css';

const response = await fetch(
  'https://api.genratr.com/?length=12&uppercase&lowercase&special&numbers'
);
const json = await response.json();

document.querySelector('#root').innerHTML = render(
  <div className="container">
    <h1>Webová aplikace</h1>
    <StrongPassword password={json.password} length={12} />
  </div>
);
```

:::
