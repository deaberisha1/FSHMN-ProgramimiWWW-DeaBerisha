# JavaV — Formulari i misionit sekret

Nje faqe me formular semantik per regjistrimin ne nje mision ne kampus, me validim vendas te HTML-it dhe nje tabele me oraret e misioneve. Kur te dhenat jane valide, formulari kalon te `pranuar.html` me GET. Perdoren vetem te dhena te sajuara dhe asgje nuk ruhet ne server.

## Analiza para kodimit

Hyrjet: pseudonimi (3–20 karaktere), email-i, numri i personave ne grup (1–5), kategoria (Art ose Shkencë) dhe pranimi i rregullave.

Daljet: nese ndonje fushe s'osht valide, browseri e ndal dergimin dhe e tregon mesazhin te fusha. Nese krejt jane valide, hapet `pranuar.html` dhe vlerat shfaqen ne URL, p.sh. `file:///C:/Users/ardia/OneDrive/Desktop/FSHMN-ProgramimiWWW/JavaV/pranuar.html?pseudonimi=DeaBerisha&email=dea%40gmail.com&persona=2&kategoria=shkence&rregullat=po`.

Rast normal: pseudonimi `DeaBerisha`, email-i `dea@gmail.com`, 2 persona, kategoria Shkence dhe checkbox-i i shenuar. Formulari kalon te `pranuar.html`.

Rast kufitar 1: persona 1 dhe 5 kalojne, ndersa 0 dhe 6 nuk kalojne, se `min="1"` dhe `max="5"` i lejojne vetem vlerat brenda kufijve.

Rast kufitar 2: pseudonimi me 3 dhe me 20 karaktere kalon. Me 2 karaktere nuk kalon (`minlength="3"`), e ma shume se 20 nuk mund te shkruhen fare (`maxlength="20"`).

## Qka kam realizu

Ne `index.html` e kom zevendesu TODO-n me formularin dhe tabelen. Formulari ka `action="pranuar.html"` dhe `method="get"`. Secili kontroll ka `label` te lidhur me `for` dhe `id`, dhe secili ka `name`, se pa `name` vlera nuk dergohet ne URL. Pseudonimi perdor `required`, `minlength="3"` dhe `maxlength="20"`; email-i `type="email"` dhe `required`; persona `type="number"`, `min="1"`, `max="5"` dhe `required`. Dy radio-t (Art, Shkencë) kane te njejtin `name="kategoria"` dhe jane brenda `fieldset` me `legend` "Kategoria". Checkbox-i i rregullave ka `required`. Butoni `type="submit"` e nis validimin vendas te browserit. Formulari ka `autocomplete="off"`, qe browseri mos me plotesu te dhena reale.

Tabela ka `caption` "Oraret e misioneve", tri `th scope="col"` per kolonat (Ora, Misioni, Vendi) dhe nje `th scope="row"` per oren ne secilin rresht, me tri orare gjithsej.

`pranuar.html` osht faqe statike qe tregon qe formulari kaloi validimin, qe vlerat shihen ne URL dhe qe asnje regjistrim nuk ruhet, se s'ka server. Ka edhe lidhje kthimi te formulari.

## Si hapet

Hape `index.html` ne browser. Per me pa dergimin, plotesoje formularin me te dhena te sajuara dhe kliko "Kontrollo formularin". Ne `pranuar.html` shiko shiritin e adreses per vlerat e GET-it.

## Testet

| Hyrja | Rezultati i pritur | Rezultati i marre |
|-------|--------------------|-------------------|
| Formulari bosh | Nuk kalon | Nuk kalon, browseri e tregon mesazhin te fusha e pare bosh |
| Email `studenti` | Nuk kalon | Nuk kalon, mungon `@` |
| Email `studenti@` | Nuk kalon | Nuk kalon, mungon pjesa pas `@` |
| Persona 0 | Nuk kalon | Nuk kalon, vlera duhet me qene ≥ 1 |
| Persona 6 | Nuk kalon | Nuk kalon, vlera duhet me qene ≤ 5 |
| Persona 1 dhe 5 | Kalon | Kalon te `pranuar.html` |
| Pseudonim me 2 karaktere | Nuk kalon | Nuk kalon, duhen se paku 3 |
| Pseudonim me 3 dhe 20 karaktere | Kalon | Kalon te `pranuar.html` |
| 25 karaktere te shtypura ne pseudonim | Merren vetem 20 | Fusha ndalet ne 20 karaktere |
| Pa kategori | Nuk kalon | Nuk kalon, kerkohet nje opsion |
| Pa pranim te rregullave | Nuk kalon | Nuk kalon, kerkohet checkbox-i |
| Te dhena valide | Hapet `pranuar.html` me vlerat ne URL | `pranuar.html?pseudonimi=Shqiponja7&email=student%40example.org&persona=3&kategoria=shkence&rregullat=po` |
| Tabela | Caption dhe tituj kolonash | Caption "Oraret e misioneve", `th scope="col"` Ora, Misioni, Vendi dhe `th scope="row"` per 3 oraret |
| Plotesim vetem me tastiere (Tab, Space, Enter) | Formulari punon pa mi | Kalon te `pranuar.html`, fokusi shihet ne cdo kontroll |
| Gjeresia 360, 768, 1280 px | Pa scroll horizontal | scrollWidth 360, 768, 1280 |

## Rastet e pranimit

- [x] Formulari bosh nuk kalon.
- [x] Email pa format email-i dhe grup 0 ose 6 nuk kalojne.
- [x] Te dhenat valide qojne te faqja e demonstrimit; tabela ka tituj kolonash.

## GET dhe URL

Me `method="get"`, browseri i shton vlerat e formularit ne fund te URL-se, pas `?`, ne formen `name=vlera` te ndame me `&`. Kshtu qe krejt qka shkruan shihet ne shiritin e adreses, ruhet ne historik te browserit dhe mund te kopjohet me link. Prandaj GET s'perdoret per te dhena personale ose fjalekalime, e ne kete demonstrim perdoren vetem te dhena te sajuara. `pranuar.html` osht faqe statike: e merr URL-ne, por s'e lexon dhe s'e ruan askund, pra nuk krijohet asnje regjistrim ne server.

## Pse required ne frontend nuk provon qe te dhenat ne nje sistem real jane te sigurta?

Validimi me `required`, `type`, `min/max` dhe `minlength/maxlength` ekzekutohet ne browserin e perdoruesit, e perdoruesi e kontrollon krejt browserin e vet. Ai mund ta hjek `required` me DevTools, mund ta shtoj `novalidate` ne formular, ose mund ta dergoj kerkesen direkt pa formular, p.sh. duke e shkru URL-ne `pranuar.html?persona=99` me dore ose me curl. Pra ky validim osht per perdoruesin e sinqerte: e ndihmon me i rregullu gabimet shpejt. Nuk e mbron serverin. Pervec kesaj, `required` kontrollon veq qe fusha nuk osht bosh dhe qe formati duket ne rregull, e jo qe te dhenat jane te verteta: `student@example.org` osht email valid ne format, por i sajuar. Ne nje sistem real serveri duhet me i validu prap krejt te dhenat, me i pastru para se me i ruajt dhe me perdor POST me HTTPS per te dhena personale.

## Deklarimi i burimeve

Si burim e kam perdor README-ne e detyres, kap. 5 i librit dhe file-in `Fillimi/`. 
