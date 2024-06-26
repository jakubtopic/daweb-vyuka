---
title: Řady sedadel
lead: Zařídíme zobrazení sedadel v řadách.
demand: 3
context: lekce
solutionAccess: protected
---

Nyní zařídíme zobrazování sedadel v řadách. Plánek sedadel bude vypadat tak, že v HTML bude pro každou řadu sedadel jedna komponenta `SeatRow` a teprve uvnitř této komponenty budou jednotlivá sedadla – komponenty `Seat`.

::fig[náhled]{src=assets/nahled.png}

1. V projektu vytvořte komponentu `SeatRow`, která představuje jednu řadu sedadel. Bude vracet `div` s třídou `seat-row`, který v dalších krocích naplníme sedadly tak, jak nám přijdou z API. Zatím do komponenty natvrdo vložte pár sedadel jen pro testovací účely. Komponentu `SeatRow` pak vložte do `div`u `seats` v komponentě `SeatPicker`.
1. Komponenta `SeatRow` bude očekávat _prop_ s názvem `row`, ve které budou v poli data pro jednu řadu sedadel. Pro testovací účely si vytvořte v `SeatPicker` proměnnou `testRow`, která bude obsahovat takovéto pole:
   ```js
   const testRow = [
     {
       number: 33,
       isOccupied: false,
     },
     {
       number: 29,
       isOccupied: true,
     },
     {
       number: 25,
       isOccupied: false,
     },
   ];
   ```
1. Předejte tuto proměnmou komponentě `SeatRow` a uvnitř ní pomocí funkce `map` zobrazte jednotlivá sedadla. Jako `key` _prop_ u jednotlivých sedadel můžete použít samotné číslo sedadla, to je v řadě vždy unikátní. Ověřte, že se testovací řada sedadel správně zobrazuje v prohlížeči.
1. Nyní máme vše připraveno pro zobrazení správného plánku sedadel podle dat z API. Pracovat budeme v komponentě `SeatPicker` – tam, kde máme testovací řadu sedadel. Když se podíváte, jaká odpověď chodí z API při vyhledání spojení (ta, kterou pak máte uloženou ve stavu `journey` komponenty `HomePage`), uvidíte, že máte velké štěstí. Ve vlastnosti `seats` je pole, které představuje přímo jednotlivé řady v autobusu.
1. Nyní je tedy potřeba údaje o sedadlech předat z komponenty `HomePage` do komponenty `SeatPicker`. Do komponenty `SeatPicker` tedy přidejte _prop_ `seats` (vloží se do ní `journey.seats`).
1. Ještě je potřeba upravit komponentu `HomePage` tak, aby komponenta `SeatPicker` byla vidět jedině v případě, že je stav `journey` jiný než `null` – tedy stejně, jako se zobrazuje komponenta `JourneyDetail`. Ověřte v prohlížeči, že po vyhledání spoje se zobrazí podrobnosti cesty a také komponenta pro výběr sedadel – zatím s vašimi testovacími sedadly.
1. Uvnitř komponenty `SeatPicker` projděte pole `seats` pomocí funkce `map`, a pro každý řádek pole vytvořte jednu komponentu `SeatRow`. I komponenty `SeatRow` potřebují prop `key`. Zde bohužel nemáme žádnou rozumnou datovou položku, kterou bychom jako klíč mohli použít. Vzpomeňme si však, že funkce vložená do funkce `map` může mít dva parametry, druhý parametr je pořadové číslo (takzvaný index) aktuálního prvku. V tomto případě jej výjimečně můžeme použít jako `key` pro `SeatRow`.
1. Pokud jste všechno zařídili správně, měli byste po vyhledání cesty vidět sedadla rozmístěná stejně jako ve vzorovém designu stránky.
1. V tuto chvíli už nám stačí pouze správně zobrazit barvu sedadel. Zda je sedadlo obsazené udává vlastnost `isOccupied` v datech z API. Stačí tedy komponentě `Seat` přidat prop `isOccupied` a poslat do ní hodnotu obdrženou z API.
1. Uvnitř komponenty `Seat` zařiďte, aby se na element `svg` přidala CSS třída `seat--occupied` ve chvíli, kdy je sedadlo obsazené.
1. Pokochejte se krásným plánkem sedadel a commitněte změny.
