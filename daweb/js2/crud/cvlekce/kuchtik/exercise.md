---
title: Kuchtík
lead: Vytvořte aplikaci pro správu receptů
demand: 4
context: lekce
solutionAccess: protected
---

Podle následujícího zadání vytvořte aplikaci pro správu receptů. Aplikace bude mít dvě stránky, jedna bude v mřížce zobrazovat seznam receptů, druhá bude zobrazovat detail jednoho receptu, který si uživatel vybere na hlavní stránce. Aplikaci uživateli umožní přidávat nové recepty nebo mazat recepty již neaktuální.

**Toto cvičení dělejte ve dvojicích** v režimu takzvaného párového programování. To je způsob práce, kdy jeden programátor pracuje na svém počítači a druhý je pouze konzultant. Po nějakém čase si pak role prohoďte. Zadání cvičení je záměřně popsáno v obecných krocích, abyste měli prostor sami si rozymyslet a vzájmně prodiskutovat, jakým způsobem budete jednotlivé kroky řešit.

Co se týče vzhledu aplikace, můžete se inspirovat layoutem hlavní stránky, kterou pro nás laskavě vytvořila umělá inteligence [Midjourny](https://www.midjourney.com/):

::fig{src=assets/recipes.jpg}

1.  Nejprve si rozmyslete jaká data bude vaše aplikace potřebovat. Jak mohou vypadat informace o receptu se můžete inspirovat třeba na webu [Rohlik.cz](https://www.rohlik.cz/chef). Výhoda tohoto webu je, že mají i hezké obrázky, které si můžete pro účely tohoto cvičení vypůjčit. Rozmyslete si, jaké informace budete potřebovat pro seznam receptů a jaké pro detail jednoho receptu. S bohatostí informací to zároveň nepřehánějte, abyste nestrávili většinu času hledáním obrázků a psaním textů.
1.  Jakmile máte rozmyšlenou datovou strukturu, založte si API backend pomocí `apidroid`. Založte na backendu kolekci s recepty a naplňte ji několika recepty, které budeme později zobrazovat na hlavní stránce.
1.  Založte si Vite/JSX projekt pro frontend aplikace. Na hlavní stránce stáhněte z API seznam receptů a zobrazte je na stránce.
1.  Vytvořte komponentu `RecipeCard`, která bude zobrazovat jednu kartu s receptem. V této komponentě zobrazte název receptu, obrázek a popis. Vytvořte si pro tuto komponentu nějaké rozumné CSS styly.
1.  Do stránky přidejte formulář, do kterého uživatel může zadat nový recept. Formulář osaďte spoluchačem události `submit` a pomocí požadavku `POST` odešlete nový recept na server. Po úspěšném přidání receptu proveďte refresh stránky.
1.  Na kartu receptu přidejte možnost smazání. Protože je na stránce více receptů, potřebujete poznat, který recept chce uživatel smazat. Na tlačitko pro mazání proto přidejte `data-id` atribut s ID receptu.
1.  Na všechny tlačítka pro mazání navěsíte posluchače události. V posluchači události si přečtete ID receptu z vlastnosti `event.target.dataset.id`. Pomocí tohoto ID smažete recept na serveru. Nezapomeňte na refresh stránky.
1.  Na karty receptu přidejte odkaz pro přechod na detail receptu. Vytvořte stránku pro detail receptu a pomocí search parametrů jí předejte `id` receptu, který má zobrazit. Zobrazte recept na stránce.
1.  Na stránce s detaily receptu přidejte odkaz pro návrat na hlavní stránku, aby se uživatel mohl vrátit zpět na seznam receptů.

:::solution
Příklad možného řešení je v repository: [cviceni-kuchtik-reseni](https://github.com/Czechitas-podklady-WEB/cviceni-kuchtik-reseni).
:::
