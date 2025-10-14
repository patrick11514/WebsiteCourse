# Margin, padding + Pozicování elementů

## Přilinkování externího CSS souboru

```html
<head>
    <link rel="stylesheet" href="styles.css" />
</head>
```

### Cesty k souboru

-   Hlavní složka webu: `/styles.css` - nezáleží na jaké stránce jsme, vždy se odkazujeme na hlavní složku webu
-   Relativní cesta: `styles.css` - odkazujeme se na soubor, který je ve stejné složce jako HTML soubor
-   Složka: `css/styles.css` - odkazujeme se na soubor, který je ve složce `css`, která je ve stejné složce jako HTML soubor
-   Nadřazená složka: `../styles.css` - odkazujeme se na soubor, který je o úroveň výš než HTML soubor
-   Více nadřazených složek: `../../styles.css` - odkazujeme se na soubor, který je o dvě úrovně výš než HTML soubor

## Margin a padding

-   Margin (okraj) je prostor **mimo** element, odděluje ho od ostatních elementů
-   Padding (vnitřní okraj) je prostor **uvnitř** elementu, odděluje obsah elementu od jeho okrajů
-   Oba se nastavují pomocí CSS vlastností `margin` a `padding`

V základu má html, body elementy margin a padding, který většinou nechceme, proto se dá odstranit přes:

```css
html,
body {
    margin: 0;
    padding: 0;
}
```

## Display

Display určuje, jakým způsobem se bude element chovat na stránce. (tzv bude zobrazen)

Může nabývat těchto hodnot:

-   `block` - element zabere celou šířku svého rodiče, začíná na novém řádku (např. `<div>`, `<h1>`, `<p>`)
-   `inline` - element zabere pouze tolik místa, kolik potřebuje, může být vedle jiných elementů (např. `<span>`, `<a>`, `<strong>`)
-   `inline-block` - kombinuje vlastnosti `block` a `inline`, může být vedle jiných elementů, ale můžeme mu nastavit šířku a výšku
-   `none` - element není zobrazen a nezabírá místo na stránce

## Position

Position upravuje pozici elementu na stránce.

Může nabývat těchto hodnot:

-   `static` - výchozí hodnota, element je umístěn podle normálního toku dokumentu
-   `relative` - element je umístěn relativně k jeho normální pozici, můžeme ho posunout pomocí vlastností `top`, `right`, `bottom`, `left`
-   `absolute` - element je umístěn relativně k nejbližšímu předkovi, který má nastavenou hodnotu `position` na `relative`, `absolute` nebo `fixed`. Pokud takový předek neexistuje, je umístěn relativně k počátku dokumentu. Můžeme ho posunout pomocí vlastností `top`, `right`, `bottom`, `left`
-   `fixed` - element je umístěn relativně k oknu prohlížeče a zůstává na svém místě i při scrollování. Můžeme ho posunout pomocí vlastností `top`, `right`, `bottom`, `left`
-   `sticky` - element je umístěn podle normálního toku dokumentu, ale když dosáhne určité pozice při scrollování, stane se "přilepeným" a zůstane na svém místě, dokud uživatel nescrolluje

Z-index je užitečný, když máme na stránce více elementů, které se překrývají a chcem určit jejich správné pořadí. Totiž né vždy se nám povede mít elementy ve správném pořadí v HTML kódu.

-   `z-index` funguje pouze na elementy s pozicí `relative`, `absolute`, `fixed` nebo `sticky`
-   Vyšší hodnota `z-index` znamená, že element bude "nad" elementy s nižší hodnotou `z-index`
-   Pokud mají dva elementy stejný `z-index`, jejich pořadí je určeno jejich pořadím v HTML

Dejmetomu si to vezměme, že z-index je nová osa směrem od monitoru k nám, třeba skládání papíru na sebe. Čím vyšší číslo, tím více "k nám" je papír přiblížený.

## Flexbox

Flexbox je moderní způsob, jak uspořádat a zarovnat elementy na stránce. Umožňuje nám snadno vytvářet flexibilní a responzivní rozvržení.

Hlavní vlastnosti flexboxu, jsou jeho dvě hlavní osy:

-   Hlavní osa (main axis) - je osa, podél které jsou elementy uspořádány. Může být horizontální (výchozí) nebo vertikální.
-   Křížová osa (cross axis) - je osa, která je kolmá na hlavní osu.

### Základní nastavení flexboxu

-   display: flex - nastaví element jako flex kontejner
-   flex-direction - určuje směr hlavní osy
    -   row - elementy jsou uspořádany v řadě (main axis je horizontálně)
    -   row-reverse - elementy jsou uspořádany v řadě, ale v opačném pořadí
    -   column - elementy jsou uspořádany ve sloupci (main axis je vertikálně)
    -   column-reverse - elementy jsou uspořádany ve sloupci, ale v opačném pořadí
-   justify-content - zarovnává elementy podél hlavní osy
    -   flex-start - zarovná elementy na začátek hlavní osy
    -   flex-end - zarovná elementy na konec hlavní osy
    -   center - zarovná elementy na střed hlavní osy
    -   space-between - rovnoměrně rozmístí elementy podél hlavní osy, první element je na začátku a poslední na konci
    -   space-around - rovnoměrně rozmístí elementy podél hlavní osy s rovnoměrným prostorem kolem nich
    -   space-evenly - rovnoměrně rozmístí elementy podél hlavní osy s rovnoměrným prostorem mezi nimi
-   align-items - zarovnává elementy podél křížové osy
    -   flex-start - zarovná elementy na začátek křížové osy
    -   flex-end - zarovná elementy na konec křížové osy
    -   center - zarovná elementy na střed křížové osy
    -   stretch - roztáhne elementy tak, aby vyplnily celý prostor
    -   baseline - zarovná elementy podle jejich základní linie textu
-   flex-wrap - určuje, zda se elementy mají zalamovat na další řádek nebo sloupec, pokud se nevejdou do kontejneru
    -   nowrap - elementy se nezalamují (výchozí)
    -   wrap - elementy se zalamují na další řádek nebo sloupec
    -   wrap-reverse - elementy se zalamují na další řádek nebo sloupec, ale v opačném pořadí
-   gap - nastaví mezeru mezi elementy ve flex kontejneru (Pozor, při flex-wrap se mezery přidávají i na okrajích řádků/sloupců)

### Grid

příště
