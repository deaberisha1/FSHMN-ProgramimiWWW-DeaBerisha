# PERGJIGJE – Prova 1 · Gr.4

## P1.7 – `box-sizing: border-box`

Si default (`content-box`), `width` e elementit vlen veq per permbajtjen. Padding dhe border shtohen **mbi** ate width.

Shembull nga kodi im, `.panel`:

```css
.panel {
  width: 100%;
  padding: 1rem 1.25rem;   /* 20px majtas + 20px djathtas */
  border: 2px solid #0b4f9c; /* 2px + 2px */
}
```

- Me `content-box`: gjeresia reale = 100% + 40px + 4px → paneli del 44px jashte prindit dhe krijon scroll horizontal ne 360 px.
- Me `border-box` (qe e kam vendos per krejt elementet me `*, *::before, *::after`): 100% e perfshin edhe padding-un edhe border-in. Paneli eshte fiks sa prindi, e permbajtja ngushtohet ne brendesi.

Pra `border-box` e bon matjen me te lehte: "width" = sa zen elementi realisht ne ekran.

## P1.8 – Lidhje (`a`) per lundrim kundrejt `button` per veprim

- **`<a href="...">`** perdoret kur perdoruesi **shkon diku**: ne nje faqe tjeter ose ne nje pjese te faqes. Ne kodin tim, menuja dhe "Më shumë" jane `a href="#ndihma"` sepse e qojne perdoruesin te seksioni Ndihma. Lidhja e ndryshon URL-ne, punon me Enter, mund te hapet ne tab te ri dhe ruhet ne historik (butoni Back).
- **`<button>`** perdoret kur **ndodh nje veprim** ne te njejten faqe pa u leviz diku: me dergu formen, me hap/mbyll nje menu, me shtu ne liste. Butoni punon me Enter **dhe** Space dhe screen reader-i e lajmeron si "button".

Pse ka rendesi: perdoruesi i tastieres dhe i screen reader-it pret sjellje te ndryshme. Nese perdor `button` per lundrim ose `a` pa `href` per veprim, humb fokusi, Back-u ose Space-i nuk punojne si duhet. Ne kete prove nuk ka asnje veprim (nuk ka JavaScript), prandaj jane perdor vetem lidhje.
