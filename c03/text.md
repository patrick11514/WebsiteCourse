# Grid + další classy

## Grid

Grid je další moderní způsob, jak uspořádat a zarovnat elementy na stránce. Umožňuje nám vytvářet složitější rozvržení pomocí řádků a sloupců.
Hlavní vlastnosti gridu jsou jeho dvě hlavní osy:

-   Řádková osa (row axis) - je osa, podél které jsou řádky uspořádány. Může být horizontální (výchozí) nebo vertikální.
-   Sloupcová osa (column axis) - je osa, která je kolmá na řádkovou osu.

### Základní nastavení gridu

-   display: grid - nastaví element jako grid kontejner
-   grid-template-rows - určuje počet a velikost řádků v gridu
    -   můžeme použít jednotky jako `px`, `%`, `fr`, `auto`
    -   příklad: `grid-template-rows: 100px 200px auto;` vytvoří tři řádky, první má výšku 100px, druhý 200px a třetí se přizpůsobí obsahu
-   grid-template-columns - určuje počet a velikost sloupců v gridu
    -   můžeme použít jednotky jako `px`, `%`, `fr`, `auto`
    -   příklad: `grid-template-columns: 1fr 2fr 1fr;` vytvoří tři sloupce, první a třetí zabírají stejný prostor, druhý zabírá dvojnásobek prostoru
-   gap - nastaví mezeru mezi řádky a sloupci v grid kontejneru
    -   můžeme nastavit samostatně `row-gap` a `column-gap`
    -   příklad: `gap: 10px 20px;` nastaví mezeru 10px mezi řádky a 20px mezi sloupci
-   grid-auto-rows - určuje výšku automaticky vytvořených řádků
    -   můžeme použít jednotky jako `px`, `%`, `fr`, `auto`
    -   příklad: `grid-auto-rows: 100px;` všechny automaticky vytvořené řádky budou mít výšku 100px
-   grid-auto-columns - určuje šířku automaticky vytvořených sloupců
    -   můžeme použít jednotky jako `px`, `%`, `fr`, `auto`
    -   příklad: `grid-auto-columns: 1fr;` všechny automaticky vytvořené sloupce budou mít šířku 1fr
-   grid-template-areas - umožňuje pojmenovat oblasti v gridu pro snadnější umístění elementů
    -   příklad:
        ```css
        grid-template-areas:
            'header header header'
            'sidebar main main'
            'footer footer footer';
        ```
        vytvoří tři řádky a tři sloupce s pojmenovanými oblastmi
-   grid-area - určuje, do které oblasti gridu má element patřit
    -   můžeme použít pojmenované oblasti z `grid-template-areas`
    -   příklad: `grid-area: header;` umístí element do oblasti `header`
-   justify-items - zarovnává elementy podél řádkové osy
    -   můžeme použít hodnoty jako `start`, `end`, `center`, `stretch`
    -   příklad: `justify-items: center;` zarovná všechny elementy na střed řádkové osy
-   align-items - zarovnává elementy podél sloupcové osy
    -   můžeme použít hodnoty jako `start`, `end`, `center`, `stretch`
    -   příklad: `align-items: center;` zarovná všechny elementy na střed sloupcové osy
-   justify-content - zarovnává celý grid kontejner podél řádkové osy
    -   můžeme použít hodnoty jako `start`, `end`, `center`, `stretch`, `space-between`, `space-around`, `space-evenly`
    -   příklad: `justify-content: center;` zarovná celý grid kontejner na střed řádkové osy
-   align-content - zarovnává celý grid kontejner podél sloupcové osy
    -   můžeme použít hodnoty jako `start`, `end`, `center`, `stretch`, `space-between`, `space-around`, `space-evenly`
    -   příklad: `align-content: center;` zarovná celý grid kontejner na střed sloupcové osy

Cool stránky:

-   https://cssgrid-generator.netlify.app/ - basic klikání a ruční generování
-   https://cssgridgenerator.io/ - více pokročilejší, vezmu box a roztáhnu ho, nemusím ručně psát
-   https://grid.layoutit.com/ - více advanced, využívá areas

## Implementace login stránky
