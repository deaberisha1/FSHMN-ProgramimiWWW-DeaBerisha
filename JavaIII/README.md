# JavaIII — Klinika e CSS: shpeto afishen

Afisha e klubit te debatit ka qene e palexueshme. Detyra ishte me e kthy ne nje ftese te qarte tu perdorur CSS te jashtem, variabla, klasa te riperdorshme edhe fokus te dukshem. Po ashtu kemi diagnostiku gabimet ne gabime.css dhe i rregulluam pa !important.

## Analiza para kodimit

**Hyrjet (inputs):**
- Skeleti HTML (index.html me TODO)
- CSS baze (style.css me box-sizing)
- gabime.css me dy rregulla konfliktuale

**Daljet (outputs):**
- Afishe e plote me titull, date, vend, pershkrim, link te regjistrimit edhe tri etiketa
- CSS me variabla, responsive layout dhe focus-visible
- gabime.css e diagnostikume edhe e rregullume
- Seksione demo per focus-visible dhe box-sizing

**Rast normal:**
- Useri e hap faqen ne desktop, sheh afishen me tri etiketat, klikon butonin "Kerko informacion"

**Raste kufitare:**
- Ekran 360px: posteri pershtatet, etiketat renditen vertikalisht, nuk del jashta ekranit
- Navigim me tastiere (Tab): fokusi e shohim qarte ne butonin edhe link-s me focus-visible


## Reflektim: Cili rregull fitoi ne kaskade dhe pse?

Ne gabime.css, rregulla `#poster { color: white }` fitoi mbi `.poster { color: #17263c }` se ID selektori ka specifike me te larte (1,0,0) se class selektori (0,1,0). Ne CSS, kur dy rregulla synojne te njejtin element, fiton ajo me specifike me te larte, pavaresisht rendit ne kodin. Kjo ka ba qe teksti me kane i bardhe mbi sfond te bardhe, pra i palexueshem. Zgjidhja: heqim ID selektorin dhe perdorim vetem klasen.

## File-s
- `index.html` — Afisha edhe seksionet demo (focus-visible dhe box-model)
- `style.css` — Stili me variabla, responsive, focus-visible, box-model demo
- `gabime.css` — Kodi origjinal (ne koment), diagnostika edhe rregullimi

## Si te hapet
Hap `index.html` ne browser.

## Rastet e pranimit
- [x] CSS ngarkohet prej file-it te vecante
- [x] Paneli nuk del prej ekranit 360px
- [x] Teksti lexohet mbi sfond dhe fokusi shihet me Tab
