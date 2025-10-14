#### 1️⃣ `<head>`, `<meta>`, `<title>` a `<link>`

V HTML má každá stránka dvě hlavní části: `<head>` a `<body>`.
`<body>` už známe – tam je obsah, který návštěvník vidí.
Naopak `<head>` slouží pro „neviditelné“ informace o stránce – říká prohlížeči a vyhledávačům, co to je za stránku, jak se má zobrazit, jaký používá jazyk nebo znakovou sadu.

V `<head>` bývá několik základních elementů:

-   `<meta charset="UTF-8">` – určuje, že stránka používá české znaky správně (bez toho by třeba „č“ a „ř“ byly rozházené).
-   `<meta name="viewport" content="width=device-width, initial-scale=1.0">` – zajišťuje, že se stránka správně škáluje na mobilu. Bez toho by se stránka načetla zmenšená a museli bychom zoomovat.
-   `<title>` – titulek, který se ukazuje nahoře na záložce nebo v historii prohlížeče.
-   `<meta name="description" content="Krátký popis stránky">` – stručný popis stránky, který se často zobrazí pod odkazem ve výsledcích vyhledávání.

Kromě toho můžeme přidat i meta tagy pro sociální sítě – například `og:title` nebo `og:description` (tzv. Open Graph). Ty říkají, co se má zobrazit, když stránku sdílíme na Facebooku nebo Discordu.

A nakonec, velmi důležitý tag:
`<link rel="stylesheet" href="soubor.css">`
Ten připojuje externí CSS soubor, ve kterém máme všechny styly.
Je to nejlepší způsob, jak se CSS používá v reálných projektech –
je přehledné, znovupoužitelné a prohlížeč si ho může načíst a uložit do cache.
Zkusíme si otevřít soubor `01-meta-and-link.html`, zakomentujeme `<link>`, a uvidíme, že bez něj stránka vypadá úplně „nahá“.

---

#### 2️⃣ `display` – jak se elementy chovají na stránce

Teď už víme, jak připojit CSS, takže se podíváme na první opravdu důležitou vlastnost – `display`.
Každý HTML element má nějaké výchozí chování – to, jak se zobrazí vedle ostatních.

##### 🟦 `display: block`

„Blockový“ element je základní stavební kámen webu.
Takové elementy se skládají **pod sebe**, jeden po druhém, každý zabere **celou šířku** svého rodiče (například celou šířku stránky nebo kontejneru).
Typickými block elementy jsou `<div>`, `<p>`, `<h1>`, `<section>`, `<header>` a podobně.

Můžeme si to představit jako krabice na polici – každá krabice má vlastní řádek.
Když přidáme další block element, automaticky se odsadí dolů a začne na novém řádku.

##### 🟨 `display: inline`

Inline elementy se chovají úplně jinak.
Neskládají se pod sebe, ale **vedle sebe** – proudí jako text.
Typickými inline elementy jsou třeba `<span>`, `<a>`, `<strong>`, `<em>`, nebo `<img>`.
Inline elementy **nereagují na šířku a výšku** – mají jen tak velkou plochu, jak velký je jejich obsah.

Ukázka: když do odstavce napíšu
`<span>slovo</span>`, tak se to prostě chová jako součást textu, a neodskočí to na nový řádek.

##### 🟩 `display: inline-block`

A pak je tu kompromis mezi těmito dvěma – `inline-block`.
Ten se chová **jako inline**, takže může stát vedle jiných elementů,
ale zároveň **se chová jako block**, protože mu můžeme dát vlastní šířku a výšku.
Používá se často třeba pro tlačítka nebo malé boxíky, které chceme mít vedle sebe, ale nechceme, aby se chovaly jako prostý text.

---

### 3️⃣ `position` – jak říct prvku, kde přesně má být

Už víme, jak se prvky skládají přirozeně — pod sebou (`block`) nebo vedle sebe (`inline`).
Ale co když chceme, aby nějaký prvek byl **na konkrétním místě**, třeba v pravém rohu obrazovky, nebo aby se držel nahoře při scrollování?
K tomu slouží vlastnost `position`.

Každý prvek má jednu ze šesti základních hodnot, ale my si dnes ukážeme pět nejdůležitějších:
`static`, `relative`, `absolute`, `fixed` a `sticky`.

---

#### 🩶 `position: static`

Tohle je **výchozí chování** všech prvků.
Když nenastavíme nic, prvek má `position: static`.
To znamená, že se prostě skládá podle normálního toku stránky —
vedle nebo pod ostatními podle `display`.
U `static` prvků **nejdou použít** vlastnosti jako `top`, `left`, `bottom` nebo `right` — prohlížeč je ignoruje,
protože prvek nemá být nikam posunutý.

---

#### 🩵 `position: relative`

`relative` říká: „Buď tam, kde bys normálně byl, ale **můžeš se trošku posunout**.“
Když elementu dáme `position: relative` a například `top: 10px`, posune se o 10 pixelů dolů — ale **jeho původní místo na stránce zůstane prázdné**.
Takže se tváří, že se jen trochu nadzvedl, ale pořád je součástí běžného rozložení.

Tohle se používá hlavně proto, že když uvnitř něj bude element s `position: absolute`,
tak ten absolutní prvek bude brát **tento relativní rodič jako svůj „vztažný bod“**.
A to je strašně důležité.

---

#### 💛 `position: absolute`

Absolutní pozicování znamená:
„Odpoj mě z normálního toku stránky a umísti mě přesně tam, kde chci.“
Takový prvek **už nezabírá místo** — ostatní se chovají, jako by tam vůbec nebyl.
Můžeme ho pak přesně umístit pomocí `top`, `left`, `right`, `bottom`.

Klíčové pravidlo:
Absolutní pozicování se **vždy vztahuje k nejbližšímu rodiči, který má `position: relative`, `absolute`, nebo `fixed`**.
Pokud žádný takový rodič neexistuje, tak se prvek umístí podle celé stránky (tedy vůči `<body>`).

Typické použití — ikonky v rohu karty, nebo bubliny s tooltipem.

---

#### ❤️ `position: fixed`

Tahle hodnota říká: „Buď pořád na stejném místě okna, i když stránku scrolluju.“
Používá se třeba pro navigační lišty, „zpět nahoru“ tlačítka, nebo malé chatovací okno v rohu.

`fixed` prvky se **vždy vztahují k oknu prohlížeče** – ne k rodiči.
Takže když scrollujeme, zůstávají pořád viditelné.
Když dáme `bottom: 0; right: 0;`, bude prvek přilepený vpravo dole bez ohledu na scroll.

---

#### 💚 `position: sticky`

`sticky` je takový chytrý hybrid mezi `relative` a `fixed`.
Začíná jako `relative`, ale když stránku posuneme dolů a ten prvek by zmizel z obrazovky,
tak se **„přilepí“** a chvíli zůstane vidět.
Jakmile přejedeme za určenou oblast, zase se odlepí a chová se normálně.

Prakticky se používá třeba pro záhlaví tabulek nebo pro sticky navigace –
např. nadpis sekce, který zůstane chvíli přilepený, dokud nezačne další sekce.

---

#### 🧩 Shrnutí a praktická ukázka

Otevřeme si soubor `02-display-position.html`.
Uvidíme tam několik barevných boxů:

-   zelený „static“,
-   modrý „relative“,
-   žlutý „absolute“,
    a v rohu malý červený „fixed“.
    Když začneme scrollovat, všimněte si, že ten červený zůstává stále vpravo dole.
    A úplně nahoře máme `sticky header`, který se drží nahoře, dokud ho nahradí další sekce.

Tady studenti krásně uvidí rozdíl mezi „běžným“ a „pozicovaným“ chováním.
Doporučuji nechat je chvíli zkoušet měnit čísla `top`, `left` nebo `right`,
aby viděli, jak přesně se jednotlivé hodnoty chovají.

---

### 4️⃣ Flexbox – rozložení do řádku nebo sloupce

Teď přejdeme k jednomu z nejpoužívanějších layout systémů v moderním webu – **Flexbox**.

Flexbox se používá k tomu, aby se prvky **uspořádaly pružně** –
například několik karet vedle sebe, zarovnané na střed, nebo toolbar s tlačítky na krajích.

Abychom Flexbox mohli použít, musíme nastavit rodiči `display: flex`.
Tím z něj uděláme **flex-kontejner** a všechny jeho přímé potomky se stanou **flex-itemy**.

---

#### 🧭 Hlavní a křížová osa

Když si to představíme, Flexbox má vždy dvě osy:

-   **hlavní osa** – ta, po které se prvky skládají (ve výchozím stavu vodorovně),
-   **křížová osa** – ta, která je na ni kolmá (tedy svisle).

Směr hlavní osy určujeme pomocí `flex-direction`.
Ve výchozím stavu je to `row` (tedy zleva doprava).
Můžeme ale použít i `column`, čímž se prvky skládají pod sebe.

---

#### ⚙️ Zarovnání a mezery

Nyní můžeme ovlivňovat zarovnání:

-   `justify-content` – zarovnává prvky **na hlavní ose** (např. `flex-start`, `center`, `space-between`).
-   `align-items` – zarovnává **na křížové ose** (např. `center`, `flex-end`, `stretch`).
-   `gap` – určuje mezery mezi jednotlivými prvky, místo toho, abychom museli řešit marginy.

Ukážeme si to v souboru `03-flex.html` na horním toolbaru –
všimni si, že tři prvky (`Zpět`, vyhledávací pole a `Uložit`) jsou zarovnány tak,
že prostřední input zabírá zbylé místo. To dělá vlastnost `flex: 1` – říká, že ten prvek může růst, pokud je volné místo.

---

#### 🌱 `flex: grow shrink basis`

Zkratka `flex` má tři části:

1. **grow** – jak moc může prvek růst, když je volné místo (např. `1` znamená, že se může roztáhnout).
2. **shrink** – jak moc se může zmenšovat, když místa není dost.
3. **basis** – počáteční šířka (např. `220px`).

Například `flex: 1 1 220px` znamená:
Začni na šířce 220 px, ale můžeš se zmenšit i zvětšit podle místa.

Tuhle kombinaci používáme na kartách dole (`.card` v `03-flex.html`).
Když okno zúžíme, karty se zalomí pod sebe – to dělá `flex-wrap: wrap`.
Je to velmi intuitivní systém a používá se dnes naprosto všude – od navigací po galerie.

---

### 5️⃣ CSS Grid – rozložení do tabulky

Flexbox je skvělý na **jednorozměrné** rozložení – buď po řádcích, nebo po sloupcích.
Ale co když potřebujeme **dvoudimenzionální** rozložení, tedy mřížku?
Na to existuje **CSS Grid**.

Grid umožňuje rozdělit stránku nebo část layoutu do **sloupců a řádků**,
a prvky pak rozmístit přesně do těchto buněk.

---

#### 🧩 Základní princip

Rodič má `display: grid`,
a pomocí `grid-template-columns` určujeme, kolik sloupců má mít.

Například:

```css
grid-template-columns: repeat(3, 1fr);
```

znamená tři sloupce, každý o stejné šířce (1fr = jeden díl volného prostoru).

Potomky můžeme rozmístit automaticky, nebo říct konkrétnímu prvku,
že má přeskočit víc sloupců – třeba `grid-column: span 2;`.

---

#### 🧱 Ukázka v praxi

Otevři si soubor `04-grid.html`.
Tam máme 3 sloupcovou mřížku s několika boxy –
ten první má třídu `.hero` a `grid-column: span 3`, takže se rozprostře přes celou šířku.

Když zmenšíme okno, media queries (`@media`) postupně mění počet sloupců:

-   nad 900 px má 3 sloupce,
-   mezi 600–900 px má 2,
-   a pod 600 px se mění na jeden sloupec.

Tohle je základ responzivního designu pomocí Gridu.

---

#### 🧠 Shrnutí rozdílů: Flex vs Grid

-   **Flexbox** je lepší pro řádky nebo sloupce, kde se prvky skládají za sebe.
-   **Grid** je lepší, když potřebujeme strukturovanou mřížku, například pro layout celé stránky.

V praxi se oba přístupy často kombinují – Grid se použije pro velké rozložení stránky a Flexbox uvnitř pro zarovnání obsahu.

---

### 6️⃣ Box model – jak CSS počítá prostor

Teď se podíváme na úplně základní princip, který ale často dělá začátečníkům problémy – **box model**.

Každý HTML prvek je vlastně „krabice“, která má:

1. **content** – samotný obsah (například text nebo obrázek),
2. **padding** – vnitřní odsazení mezi obsahem a okrajem,
3. **border** – rámeček kolem,
4. **margin** – vnější mezera mezi prvkem a ostatními prvky.

---

#### 📦 Příklad

Otevři `05-box-model.html`.
Uvidíš tam několik boxů – první má standardní padding, druhý má větší padding i border,
a díky tomu zabírá víc místa.
Všimni si, že i když nastavíme šířku 220 px,
tak ten s větším borderem a paddingem je ve skutečnosti širší –
protože se to **přičítá** k obsahu.

---

#### 🧮 `box-sizing`

Aby to vývojáři nemuseli pořád přepočítávat, používá se vlastnost `box-sizing`.

-   `content-box` (výchozí) – šířka se počítá **jen pro obsah**, padding a border se přičítají navíc.
-   `border-box` – šířka **už zahrnuje** i padding a border, takže se prvek vždy vejde přesně do daného rozměru.

Proto v moderních projektech často uvidíš:

```css
* {
    box-sizing: border-box;
}
```

Tím se zjednoduší výpočty a layout se chová předvídatelněji.

---

#### 🧩 Padding vs. Margin

Ještě drobnost:

-   `padding` zvětšuje prostor **uvnitř** prvku (odsazuje obsah od hranic),
-   `margin` dělá mezeru **venku** (od ostatních prvků).

A na ladění se hodí `outline` –
to je rámeček, který **neovlivňuje rozložení**, takže se dá použít na kontrolu, kde prvek opravdu končí.

---

### 7️⃣ Shrnutí celé lekce

Dnes jsme:

-   pochopili, co se píše do `<head>` a proč,
-   naučili se připojit externí CSS soubor,
-   pochopili rozdíl mezi `block`, `inline` a `inline-block`,
-   zjistili, jak se dá s `position` přesně řídit poloha prvků,
-   vyzkoušeli základy Flexboxu a Gridu,
-   a na závěr pochopili, jak funguje box model – tedy jak CSS počítá prostor.

Doporučuji nechat studenty po lekci udělat malý úkol –
třeba jednoduchou **„vizitku“ s několika kartami**, které se rozkládají do 3 sloupců na desktopu a do 1 sloupce na mobilu.
V každé kartě ať použijí Flexbox na zarovnání obsahu doprostřed.

---

Chceš, abych ti teď všechny tyto části (hlava, display, position, flex, grid, box model) spojil do jednoho přehledného souboru `lesson2-text.md` – tedy kompletní výkladový text k lekci?
