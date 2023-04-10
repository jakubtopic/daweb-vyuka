---
title: Na dobrou noc
demand: 2
---

Vytvořte JavaScriptový program, který vepíše do stránky ovčí příběh pro děti na dobrou noc. Výsledkem by měl být text počítající ovečky.

::fig[ovce]{src=assets/ovce.jpg}

Využijte násjedujících dvacet jmen oveček:

```js
const ovciJmena = [
  'Bětuška',
  'Cína',
  'Dolly',
  'Heidy',
  'Líza',
  'Belinda',
  'Celia',
  'Elvíra',
  'Karla',
  'Otýlie',
  'Škraboška',
  'Pampeliška',
  'Berta',
  'Růženka',
  'Bobinka',
  'Žofka',
  'Dášenka',
  'Vlnka',
  'Květuše',
  'Pampeliška',
];
```

Pomocí metody `forEach` do stránky vepište deset za sebou jdoucích vět v následující podobě:

> Ovečka Bětuška jako 1. přeskočila přes plot. Ovečka Cína jako 2. přeskočila přes plot. Ovečka Dolly jako 3. přeskočila přes plot…

---solution

```js
ovciJmena.forEach((jmeno, index) => {
  document.body.textContent += `Ovečka ${jmeno} jako ${
    index + 1
  }. přeskočila přes plot. `;
});
```