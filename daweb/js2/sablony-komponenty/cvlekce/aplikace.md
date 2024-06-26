---
title: Jednoduchá aplikace
demand: 1
context: lekce
lead: Vyzkoušejte si vytvořit základní strukturu aplikace
solutionAccess: protected
---

1. Založte si nový projekt:
   ```shell
   npm init kodim-app@latest aplikace-react jsx
   ```
1. Projekt spusťte pomocí `npm run dev`, jak už to znáte z dřívejška.
1. V hlavním souboru `index.jsx` vytvořte komponentu `HomePage`, která bude obsahovat základní strukturu stránky. Zatím to může být jen prázdný element `div` s třídou `container`. Komponentu zobrazte na stránce pomocí funkce `render`.
1. Založte ve složce `src` složku `components`. Vytvořte v této složce komponentu `Header`, která bude obsahovat kód pro hlavičku stránky. Jediná její `prop` bude `title` udávající obsah elementu `h1`. Správně komponentu exportujte.
1. Vytvořte pro komponentu `Header` soubor `style.css` s nějakým jednoduchým CSS pro hlavičku stránky. Soubor se styly v komponentě správně importuje.
1. V hlavním souboru `index.jsx` komponentu `Header` importujte a použijte ji uvnitř komponenty `HomePage`.
1. Následujte stejný postup jako výše a vytvořte komponentu `Footer`, která bude představovat patičku stránky. Tato komponenta bude mít také jednu `prop` s názvem `author`, která udává jméno autora stránky.
1. Do třetice vytvořte komponentu `Main`, která bude představovat hlavní obsah stránky. Tato komponenta bude mít opět jednu `prop` s názvem `content`, která bude udávat obsah odstavce.
