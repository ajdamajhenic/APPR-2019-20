# Analiza podatkov s programom R, 2019/20

Repozitorij z gradivi pri predmetu APPR v študijskem letu 2019/20

* [![Shiny](http://mybinder.org/badge.svg)](http://mybinder.org/v2/gh/jaanos/APPR-2019-20/master?urlpath=shiny/APPR-2019-20/projekt.Rmd) Shiny
* [![RStudio](http://mybinder.org/badge.svg)](http://mybinder.org/v2/gh/jaanos/APPR-2019-20/master?urlpath=rstudio) RStudio

## Tematika

V okviru svojega projekta bom analizirala podatke o porokah in razvezah v Sloveniji. V glavnem se bom posvetila obdobju med letoma 2008 in 2018. Moje osrednje teme analize bodo: 

* povprečna starost neveste in ženina pri vstopu v prvo zakonsko zvezo,
* število sklenjenih zakonskih zvez med Slovenci letno,
* število razdrtih zakonskih zvez med Slovenci letno,
* število porok in razvez po regijah,
* število partnerskih zvez med istosplonimi partnerji,
* število zakonskih razvez z otroki in brez,
* povprečno trajanje zakonske zveze,
* število vdovelih ljudi v Sloveniji.

Cilj je pokazati, da se ljudje vedno manj poročajo, poročajo se čedalje starejši in se več ločujejo. 

### Tabele
* TABELA 1: Osnovni podatki o sklenitvah zakonskih zvez – LETO, MERITVE (sklenitve zakonskih zvez, prve sklenitve zakonskih zvez, povprečna starost ženina ob sklenitvi zakonske zveze, povprečna starost ženina ob sklenitvi prve zakonske zveze, povprečna starost neveste ob sklenitvi zakonske zveze, povprečna starost neveste ob sklenitvi prve zakonske zveze, zakonski stan ženina – vdovec, zakonski stan neveste - vdova)
* TABELA 2: Regionalni podatki o sklenitvah zakonskih zvez – STATISTIČNA REGIJA, MERITVE, LETO
* TABELA 3: Razveze zakonskih zvez – STATISTIČNA REGIJA, LETO , TRAJANJE ZAKONSKE ZVEZE
* TABELA 4: Razveze po številu vzdrževanih otrok –  STATISTIČNA REGIJA, LETO , ŠTEVILO VZDRŽEVANIH OTROK
 * TABELA 5: Sklenitve partnerskih zvez – MERITVE (med moškima, med ženskama), LETO
 
### Viri
Podatke bom pridobila na Statističnem uradu Republike Slovenije:

* https://pxweb.stat.si/SiStatDb/pxweb/sl/10_Dem_soc/10_Dem_soc__05_prebivalstvo__34_Poroke__05_05M10_poroke-SL/?tablelist=true
* https://pxweb.stat.si/SiStatDb/pxweb/sl/10_Dem_soc/10_Dem_soc__05_prebivalstvo__34_Poroke__10_05M20_poroke-RE-OBC/?tablelist=true
* https://pxweb.stat.si/SiStatDb/pxweb/sl/10_Dem_soc/10_Dem_soc__05_prebivalstvo__36_Razveze__05_05M30_razveze-SL/?tablelist=true
* https://pxweb.stat.si/SiStatDb/pxweb/sl/10_Dem_soc/10_Dem_soc__05_prebivalstvo__36_Razveze__10_05M40_razveze-RE-OBC/?tablelist=true
* https://pxweb.stat.si/SiStatDb/pxweb/sl/10_Dem_soc/10_Dem_soc__05_prebivalstvo__35_05M50_istospolne_skupnosti/?tablelist=true



## Program

Glavni program in poročilo se nahajata v datoteki `projekt.Rmd`.
Ko ga prevedemo, se izvedejo programi, ki ustrezajo drugi, tretji in četrti fazi projekta:

* obdelava, uvoz in čiščenje podatkov: `uvoz/uvoz.r`
* analiza in vizualizacija podatkov: `vizualizacija/vizualizacija.r`
* napredna analiza podatkov: `analiza/analiza.r`

Vnaprej pripravljene funkcije se nahajajo v datotekah v mapi `lib/`.
Podatkovni viri so v mapi `podatki/`.
Zemljevidi v obliki SHP, ki jih program pobere,
se shranijo v mapo `../zemljevidi/` (torej izven mape projekta).

## Potrebni paketi za R

Za zagon tega vzorca je potrebno namestiti sledeče pakete za R:

* `knitr` - za izdelovanje poročila
* `rmarkdown` - za prevajanje poročila v obliki RMarkdown
* `shiny` - za prikaz spletnega vmesnika
* `DT` - za prikaz interaktivne tabele
* `rgdal` - za uvoz zemljevidov
* `rgeos` - za podporo zemljevidom
* `digest` - za zgoščevalne funkcije (uporabljajo se za shranjevanje zemljevidov)
* `readr` - za branje podatkov
* `rvest` - za pobiranje spletnih strani
* `tidyr` - za preoblikovanje podatkov v obliko *tidy data*
* `dplyr` - za delo s podatki
* `gsubfn` - za delo z nizi (čiščenje podatkov)
* `ggplot2` - za izrisovanje grafov
* `mosaic` - za pretvorbo zemljevidov v obliko za risanje z `ggplot2`
* `maptools` - za delo z zemljevidi
* `extrafont` - za pravilen prikaz šumnikov (neobvezno)

## Binder

Zgornje [povezave](#analiza-podatkov-s-programom-r-201819)
omogočajo poganjanje projekta na spletu z orodjem [Binder](https://mybinder.org/).
V ta namen je bila pripravljena slika za [Docker](https://www.docker.com/),
ki vsebuje večino paketov, ki jih boste potrebovali za svoj projekt.

Če se izkaže, da katerega od paketov, ki ji potrebujete, ni v sliki,
lahko za sprotno namestitev poskrbite tako,
da jih v datoteki [`install.R`](install.R) namestite z ukazom `install.packages`.
Te datoteke (ali ukaza `install.packages`) **ne vključujte** v svoj program -
gre samo za navodilo za Binder, katere pakete naj namesti pred poganjanjem vašega projekta.

Tako nameščanje paketov se bo izvedlo pred vsakim poganjanjem v Binderju.
Če se izkaže, da je to preveč zamudno,
lahko pripravite [lastno sliko](https://github.com/jaanos/APPR-docker) z želenimi paketi.

Če želite v Binderju delati z git,
v datoteki `gitconfig` nastavite svoje ime in priimek ter e-poštni naslov
(odkomentirajte vzorec in zamenjajte s svojimi podatki) -
ob naslednjem zagonu bo mogoče delati commite.
Te podatke lahko nastavite tudi z `git config --global` v konzoli
(vendar bodo veljale le v trenutni seji).
