# JavaIV — Festivali qe pershtatet ne cdo ekran

Nje faqe statike per programin e nje festivali shkencor qe lexohet mire edhe ne telefon edhe ne ekran te gjere. Faqja ka nje menu fleksibile me Flexbox, nje imazh fleksibel dhe gjashte karta aktivitetesh te rendituna me Grid.

## Qka kam realizu

Ne `index.html` e kom zevendesu TODO-n me nje menu (Programi, Detajet, Regjistrimi), nje banner `festivali.svg` dhe seksionin Programi me gjashte karta. Secila karte osht `article` me titull, kategori, orar (me `<time>`) dhe lidhje "Detajet" qe shkon te seksioni `#detajet`. 

Ne `style.css` menuja perdor `display: flex` me `flex-wrap: wrap`, kshtu qe ne ekran te ngusht link-at kalojne ne rresht te ri. Kartat perdorin Grid: nje kolone si default, dy kolona prej `min-width: 600px` dhe tri kolona prej `min-width: 900px`. Kolonat jane `minmax(0, 1fr)` qe nje fjale e gjate mos me e zgjeru kolonen. `overflow-wrap: anywhere` osht ne `body`, pra vlen per krejt tekstin e faqes, jo veq per kartat. Imazhi ka `max-width: 100%` dhe `height: auto`, e asnje element me tekst nuk ka lartesi fikse. Fokusi i link-ave shihet me `:focus-visible`.

## Si hapet

Hape `index.html` ne browser. Per testet e madhesive perdor DevTools (F12) dhe Device Toolbar (Ctrl + Shift + M), pastaj shkruj gjeresine 360, 768 ose 1280.

## Testet

| Hyrja | Rezultati i pritur | Rezultati i marre |
|-------|--------------------|-------------------|
| Gjeresia 360 px | 1 kolone, pa scroll horizontal | 1 kolone, scrollWidth 360 |
| Gjeresia 768 px | 2 kolona, pa scroll horizontal | 2 kolona, scrollWidth 768 |
| Gjeresia 1280 px | 3 kolona, pa scroll horizontal | 3 kolona, scrollWidth 1280 |
| Kufijte 599 / 600 / 899 / 900 px | 1 / 2 / 2 / 3 kolona | 1 / 2 / 2 / 3 kolona |
| Titull me 100 karaktere ne karten e pare | Titulli thyhet, karta mbetet e rregullt | Titulli thyhet ne disa rreshta, karta s'prishet |
| Fjale e gjate pa hapsira ne cdo tekst te faqes, ne 360 / 768 / 1280 px | Asnje tekst nuk del jashte | Asnje element me overflow, scrollWidth = gjeresia e ekranit |
| Imazhi ne 360 dhe 1280 px | Ngushtohet me ekranin, nuk deformohet | 328 x 109 px ne 360, 1200 x 400 px ne 1280 |
| Tab neper faqe | Fokusi shihet ne cdo link | Outline 3 px ne skip link, menu dhe "Detajet" |
| Enter ne "Programi" dhe "Detajet" | Faqja shkon te seksioni | URL behet `#programi` dhe `#detajet` |

## Rastet e pranimit

- [x] Ne 360/768/1280 px shfaqen perkatesisht 1/2/3 kolona.
- [x] Nuk ka scroll horizontal ne faqen e plote.
- [x] Menuja mbetet e perdorshme me tastiere.

## Reflektim individual: Kur do te zgjidhje Flexbox dhe kur Grid?

Flexbox e zgjedh kur elementet rrine ne nje drejtim, ose ne rresht ose ne kolone, dhe dua qe madhesia e permbajtjes me vendos sa vend zen secili. Shembull osht menuja ime: link-at rrine ne rresht, e kur nuk kane vend, `flex-wrap` i qon ne rreshtin tjeter. Edhe brenda kartes e kom perdor Flexbox (`flex-direction: column` me `margin-top: auto`) qe lidhja "Detajet" me qendru gjithmone poshte.

Grid e zgjedh kur kam layout ne dy dimensione, rreshta dhe kolona njekohesisht, dhe dua kolona te barabarta qe nuk varen prej permbajtjes. Kartat jane shembulli: me `grid-template-columns` vendos sakt 1, 2 ose 3 kolona dhe kartat ne te njejtin rresht kane lartesi te njejte. Me Flexbox kjo do te ishte ma e veshtire, se rreshti i fundit me ma pak karta do te zgjerohej ndryshe.

## Deklarimi i burimeve

Si burim i kom perdor kapitujt 6–7 te librit te lendes dhe MDN Web Docs per Flexbox, Grid dhe `overflow-wrap`. Imazhi `festivali.svg` esht i krijum per kete detyre ne Claude, nuk esht marre prej internetit.
