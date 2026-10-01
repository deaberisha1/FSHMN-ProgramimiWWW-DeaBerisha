# JavaII — Muzeu i sendeve te zakonshme

Nje faqe web statike qe paraqet nje muze me tre sende te zakonshme: celesi, filxhani dhe bileta. Secila sende shfaqet si karte me imazh SVG, pershkrim dhe histori te fshehur. Per historine e fshehur eshte perdorur elementi `<details>`. Per me hap e klikojm `index.html` ne browser.

## Analiza para kodimit

**Hyrjet (inputs):**
- Tre SVG files (celesi.svg, filxhani.svg, bileta.svg)
- Skeleti HTML (index.html)
- Skeleti CSS (style.css baze)

**Daljet (outputs):**
- Faqe e plote HTML me tri karta, me navigim, dhe me histori te fsheht per secilin send

**Rast normal:**
- Perdoruesi e hap faqen, i sheh tri kartat, klikon "Historia e fshehur" edhe teksti shfaqet poshte

**Raste kufitare:**
- Ekran i vogel (telefon): kartat tani renditen vertikalisht ne vend te tre kolonave
- JavaScript i caktivizuar: faqja punon njesoj sepse `<details>` eshte built-in element i HTML.
