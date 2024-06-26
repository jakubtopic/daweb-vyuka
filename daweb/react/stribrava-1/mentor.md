## Rady od vašeho mentora

Pročtěte si rady, které vám poslal váš mentor a následujte je při tvorbě projektu.

1. Dobře si přečtěte zadání od zákazníka, prohlédněte si požadovaný design stránek a zakoupenou CSS šablonu.
1. Na GitHubu si vytvořte nový repozitář pro váš projekt. Zvolte si, jakým způsobem budete spolupracovat, jestli na jedné větvi nebo párovým programováním. V repozitáři si vytvořte klasickou strukturu react projektu pomocí `init kodim-app`.

Projekt si rozdělíme do několika částí:

1. Hlavní stránka, kterou uvidí návštěvník a API pro hotelové pokoje.
1. Počítání celkové ceny poptávky.
1. API poskytující data pro objednávkový systém.
1. Zprovoznění formuáře pro odesílání poptávek.
1. Stránka pro administraci, kterou uvidí recepční.

## Hlavní stránka

1. Pomocí `apidroid` si vytvořte API s kolekcí pro jednotlivé pokoje. Naplňte tuto kolekci daty a v prohlížeči si ověřte, že API endpoint funguje. Později budeme ještě potřebovat kolekci pro jednotlivé poptávky. Tu si nechte až na později.
1. `apidroid` umí poskytovat i soubory (např. obrázky). To se bude hodit pro fotky pokojů – abyste je mohli mít hned u API a ne ve vaší frontendové aplikaci. Přidání nového pokoje pak bude znamenat jen úpravu na straně API, v reactové aplikace nebude potřeba nic měnit. Vytvořte si v kořenové složce projektu (na stejné úrovni, kde je složka `api`) složku pojmenovanou `assets`. Do ní můžete nahrávat soubory (např. obrázky). Pokud tam nahrajete třeba soubor pojmenovaný `pokoj01.jpg`, bude pak dostupný na stejné adrese jako API na cestě `http://localhost:4000/assets/pokoj01.jpg` (tj. v adrese je `assets` místo `api`).
1. Pomocí diagramu komponent si rozvhrněte, jaké komponenty budete potřebovat pro hlavní stránku, jaké tyto komponenty budou mít stavy, props a datové toky. V diagramu běžte do takových detailů, jak je vám samotným pohodlené.
1. Než se pustíte do vlastního programování, zkonzultujte váš návrh komponent s některým z koučů. Pokuste se mu/jí co nejsrozumitelněji vysvětlit, jak bude vaše stránka fungovat, jak budou komponenty mezi sebou komunikovat. Nechte si poradit, co by se na vašem návrhu dalo zlepšit.
1. Naprogramoujte hlavní stránku tak, aby uživatel viděl seznam pokojů, mohl si rozkliknout detail pokoje vyplnit formulář s poptávkou. Formulář zatím nebude odosílat žádná data, pouze se po stisknutí tlačítka zobrazí potvrzení o úspěšném odeslání. Počítání celkové ceny poptávky vyřešíme v dalším kroku.
1. Dokončete celou hlavní stránku. Až na odesílání formuláře by měla být hotová.

## Celková cena poptávky

Jelikož je potřeba celkovou cenu poptávky spočítat po každé změně stavu, můžete si založit proměnnou přímo v těle komponenty a spočítat do ní výslednou cenu podle toho, co je uloženo ve stavech. Pokud chcete mít výpočet oddělený od komponenty, můžete si vytvořit pomocnou funkci, která bude mít jako parametry stavy a vrátí výslednou cenu.

Pro zjištění ceny je důležité nejprve spočítat počet strávených nocí. K tomu použijte knihovnu [Day.js](https://day.js.org/). Tuto knihovnu už jste mohli vidět na začátku výuky JavaScriptu.

Bude potřeba Day.js do vašeho projektu nainstalovat. Bohužel Day,js nemá v dokumentaci popsánu instalaci do projektů, které používají moderní JavaScript, jako jsou i naše projekty. Vězte tedy, že knihovnu nainstalujete příkazem

```shell
npm install dayjs
```

Po provedení příkazu `npm install` je lepší ukončit a znovu nastartovat `npm run dev`, aby se Vite.js dozvěděl o nové knihovně.

Následně můžete ve svých komponentách nebo javascriptových souborech naimportovat dayjs:

```javascript
import dayjs from 'dayjs';
```

Po importu už můžete `dayjs` používat tak, jak je popsáno v dokumentaci. Najdete tam [příklady](https://day.js.org/docs/en/display/difference) pro výpočet rozdílu mezi dvěma daty.

## API pro objednávkový systém

Navhrněte API pro kolekci poptávek. U každé poptávky budeme chtít evidovat v jaké je fázi:

- `new` - nová poptávka, kterou ještě nikdo nezkontroloval,
- `confirmed` - poptávka byla přijata,
- `rejected` - poptávka byla zamítnuta.

Navhrněte tedy datovou strukturu pro objednávky, kde u každé objednávky budou informace, které zadal návštěvník na hlavní stránce a také informace o tom, v jaké fázi se poptávka nachází.

## Formulář pro odesílání poptávek

Nyní chceme umožnit odeslat formulář s poptávkou a dano poptáku uložit do naší databáze. Zde stačí přidat do kolekce s poptávkami objekt ve správném tvaru – pomocí dotazu POST na API endpoint s poptávkami. Dotaz POST automaticky přidává nový záznam na konec kolekce, takže se poptávky v administraci zobrazí rovnou v požadovaném pořadí od nejstarších po nejnovější.

## Stránka pro administraci

Nyní si rozmyslete, jak bude fungovat administrace.

1. Nejdříve navhrněte, jak bude vypadat stránka s administrací. Použijte Figmu, tužku a papír, nebo nějaký nástroj pro wireframing, cokoliv co je vám pohodlné. U každé poptávky budeme chtít vidět, jaké informace nám zákazník zadal. Chceme také mít možnost poptávku označit jako vyřízenou nebo zamítnutou.
1. Můžete si nakreslit diagram komponent, ale vhledem k tomu, že jde o jednoduchý vzor zobrazení seznamu, možná jej ani nepotřebujete.
1. Server `apidroid` umí filtrování dat pomocí parametrů v URL. Pokud chceme pouze poptávky ve fázi `new`, napíšeme do URL `filter=phase:eq:new`. Celá adresa tak může vypadat například takto: `http://localhost:4000/api/poptavky?filter=phase:eq:new`. Vytvořte si několik fiktivních poptávek přímo v souboru JSON a vyzkoušejte si, jak funguje filtrování.
1. Naprogramujte zobrazní poptávek a vyzkoušejte si na vašich testovacích datech, že umíte zobrazit pouze poptávky ve fázi `new`.

Nyní přichází zajímavá část, kdy budeme chtít označovat poptávky jako vyřízené nebo zamítnuté. Při kliknutí na tlačíko pro označení poptávky jako vyřízené nebo zamítnuté je potřeba odeslat na API dotaz PATCH, abychom změnili fázi poptávky, a hned po jeho dokončení znovu načíst filtrovaný seznam poptávek, aby se komponenta zobrazující seznam poptávek překreslila.

Server `apidroid` používá pro aktualizaci záznamu v kolekci metodu PATCH. Do těla požadavku se vkládá objekt, který popisuje, jak se má záznam změnit. V našem případě chceme změnit pouze fázi poptávky. V těle požadavku tedy pošleme objekt, který bude vypadat například takto:

```json
[
  {
    "op": "replace",
    "path": "/phase",
    "value": "confirmed"
  }
]
```

Naprogramujte označování poptávek a ověřte, že administrace funguje. V této fázi byste měli mít projekt hotový. Uživatel by měl mít možnost provést poptávku a recepční by měla mít možnost poptávky zobrazit a označit jako vyřízené nebo zamítnuté.
