---
title: Házení kostkou
demand: 3
context: nadoma
lead: Vymyslete funkci, která simuluje hod kostkou.
solutionAccess: protected
---

Vymyslete, jak použít funkci `Math.random` a různé zaokrouhlovací funkce probírané v této lekci k simulování hodu klasickou šestistěnnou kostkou. S použitím vhodných funkcí sestavte výraz, který vygeneruje náhodné celé číslo **mezi 1 a 6**.

Zamyslete se nad tím, zda vámi vytvořený výraz generuje všechna čísla skutečně se stejnou pravděpodobností. Vemte v úvahu, že funkce `Math.random` generuje náhodná čísla mezi 0 (včetně) a 1 (vyjma). Je tedy malinká pravěpodobnost, že **občas padne přesně číslo 0**. Naopak **číslo 1 padnout nemůže**.

:::solution

```js
const cisloNaKostce = 1 + Math.floor(Math.random() * 6);
```

Nelze použít funkci `Math.round()`. Její použití by znamenalo, že **1** padne pouze s pravděpodobností 1:12. Navíc by s pravděpodobností 1:12 také mohla padnout hodnota **7**.

:::
