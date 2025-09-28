## Úvod do webových technologií

### Co je to webová stránka?

Webová stránka je dokument, který je přístupný přes internet pomocí webového prohlížeče. Obsahuje text, obrázky, videa a další multimediální prvky, které jsou strukturovány pomocí HTML (HyperText Markup Language). Webové stránky mohou být statické nebo dynamické a často využívají CSS (Cascading Style Sheets) pro stylování a JavaScript pro interaktivitu.

### Základní technologie webových stránek

1. **HTML (HyperText Markup Language)**: Základní stavební kámen webových stránek, který definuje strukturu a obsah stránky pomocí značek (tagů).
2. **CSS (Cascading Style Sheets)**: Jazyk pro popis vzhledu a formátování webových stránek. Umožňuje definovat styly pro HTML prvky, jako jsou barvy, písma a rozložení.
3. **JavaScript**: Programovací jazyk, který umožňuje vytvářet interaktivní prvky na webových stránkách, jako jsou formuláře, animace a dynamický obsah.

### Jak funguje webová stránka?

Když uživatel zadá URL adresu do webového prohlížeče, prohlížeč odešle požadavek na webový server, který obsahuje požadovanou stránku. Server zpracuje požadavek a odešle zpět HTML dokument, který prohlížeč vykreslí a zobrazí uživateli. Pokud stránka obsahuje odkazy na CSS nebo JavaScript soubory, prohlížeč je také stáhne a použije k zobrazení a interaktivitě stránky.

## Úvod do HTML

HTML je značkovací jazyk používaný k vytváření webových stránek. Skládá se z různých značek (tagů), které definují různé části obsahu, jako jsou nadpisy, odstavce, odkazy, obrázky a další. Základní struktura HTML dokumentu zahrnuje:

```html
<!DOCTYPE html>
<html>
    <head>
        <title>Název stránky</title>
    </head>
    <body>
        <h1>Hlavní nadpis</h1>
        <p>Toto je odstavec textu.</p>
    </body>
</html>
```

### Základní tagy v HTML

-   `<html>`: Kořenový element HTML dokumentu.
-   `<head>`: Obsahuje metadata o dokumentu, jako je název a odkazy na styly.
-   `<title>`: Definuje název stránky, který se zobrazuje v záložce prohlížeče.
-   `<body>`: Obsahuje hlavní obsah stránky.
-   `<h1>` až `<h6>`: Nadpise různých úrovní.
-   `<p>`: Definuje odstavec textu.
-   `<a>`: Vytváří hypertextový odkaz.
-   `<img>`: Vkládá obrázek do stránky.
-   `<div>`: Blokový kontejner pro seskupování obsahu.
-   `<span>`: Inline kontejner pro seskupování obsahu.
-   `<br>`: Vkládá zalomení řádku.
-   `<ul>`, `<ol>`, `<li>`: Vytváří nečíslované a číslované seznamy.

Tagy se dělí na **nepárové** a **párové**. Například `<img>` je nepárový tag, protože nemá koncový tag, zatímco `<p>` je párový tag, protože má otevírací a zavírací část.

Každý tag má na sobě různé atributy, atributy mají vždy jméno a hodnotu, například:

```html
<a href="https://example.com">Odkaz</a>
<img src="obrazek.jpg" alt="Popis obrázku" />
```

## Úvod do CSS

Inspirace:

-   Otevři si [inspiration.html](./inspiration.html) v prohlížeči a zkus si všimnout jak je stránka bez stylu.
-   Nyní oddělej komentář v 7. řádku a stránka se změní na nastylovanou. :)

CSS je jazyk používaný k popisu vzhledu a formátování webových stránek. Umožňuje definovat styly pro HTML prvky, jako jsou barvy, písma, rozložení a další vizuální aspekty. CSS může být zahrnuto přímo v HTML dokumentu pomocí `<style>` tagu, style atributu u každého tagu zvlášť, nebo jako externí soubor propojený pomocí `<link>` tagu.

### Základní syntaxe CSS

CSS se skládá z pravidel, která obsahují název pravidla a jeho hodnoty. Pokud tedy chci aby text v tagu `<p>` byl červený, napíšu:

```html
<p style="color: red;">Toto je červený text.</p>
```

Nebo pak ve `<style>` tagu:

```html
<style>
    p {
        color: red;
    }
</style>

<body>
    <p>Toto je červený text.</p>
    <p>Tento také :)</p>
</body>
```

Problémem u tohoto vybírání je to, že to platí na všechny tagy `<p>`, což nemusí být vždy žádoucí. Proto můžeme použít **třídy** a **id**. Třídy a id lze použít pouze v separáním CSS souboru, nebo ve `<style>` tagu, nikoliv v `style` atributu.

Formát tohoto je:

```css
SELEKTOR {
    vlastnost: HODNOTA;
    vlastnost: HODNOTA;
}
```

do `SELEKTOR` můžeme dát:

-   Tag - např. `p`, `h1`, `div`, `span` atd.
-   Třídu - např. `.blue`, `.container` atd. (třída musí začínat tečkou)
-   Id - např. `#unikátní-id`, `#header` atd. (id musí začínat mřížkou)
-   Kombinace - např. `div.blue`, `p#unikátní-id` atd.

Jednotlivé vysvětlení:

-   Třídy - jakékoliv pojmenování a je určeno pro více prvků
-   Id - musí být unikátní na stránce a je určeno pro jeden prvek

```html
<style>
    .blue {
        color: blue;
    }

    #unikátní-id {
        color: purple;
    }
</style>

<body>
    <p class="blue">Ale tento je modrý :)</p>
    <p id="unikátní-id">A tento fialový</p>
    <p id="unikátní-id">A tento fialový</p>
</body>
```

a skládání:

```html
<style>
    div.blue {
        color: blue;
    }

    div.red p {
        color: red;
    }
</style>

<body>
    <div>
        Tady nic není nastylováno
        <p>Tady taky ne</p>
    </div>
    <div class="blue">
        Ale tento je modrý :)
        <p>Tady taky ne</p>
    </div>
    <div class="red">
        Tady nic není nastylováno
        <p>Ale tento je červený :)</p>
    </div>
</body>
```
