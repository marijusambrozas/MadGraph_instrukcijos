# `MadGraph5_aMC@NLO` instaliacija ir naudojimo pagrindai

## 1. Instaliacija

1. Nueiti į `MadGraph5_aMC@NLO` [internetinį puslapį](https://launchpad.net/mg5amcnlo "MG5_aMC@NLO internetinis puslapis")

2. Atsisiųsti naujausią `MadGraph5` versiją (žalia nuoroda ekrano dešinėje)

3. Įsikopijuoti atsisiųstą `tar.gz` failą į direktoriją, kurioje norite turėti `MadGraph` (išskleidus suspaustą failą nauja direktorija, talpinanti programos failus bus sukurta, tad pačiam jos sukūrimu rūpintis nebūtina)

4. Išskleisti suspaustą `tar.gz` failą: 

	```bash
	$ tar -xvzf MG5_aMC_vX.Y.Z.tar.gz
	```
	
	(Čia ir toliau simbolis `$` reiškia, kad komanda vedama į `bash` terminalą)

5. Pereiti į išskleistą direktoriją:
	
	```bash
	$ cd MG5_aMC_vX_Y_Z
	```
	
6. Paleisti `MadGraph`:
	
	```bash
	$ ./bin/mg5_aMC
	```
	1. Jeigu išmeta klaidą, patikrinkite, kokią `python` versiją naudojate:
	
		```
		$ python --version
		```
	2. Jeigu matote, kad naudojama `python3`, reikia aktyvuoti `python2`
	3. Su `Anaconda` tai galima padaryti taip:
		
		```bash
		$ conda create -n python2p7 python=2.7
		$ conda activate python2p7
		```

## 2. Naudojimo įvadas

1. Įsijungus `./bin/mg5_aMC` atsiduriame `MadGraph5` terminale. Ten galime įjungti programos kūrėjų sukurtą supažindinimą su programa (jame jums teks sumodeliuoti viršūninio kvarko ir antikvarko poros sukūrimo Didžiajame hadronų greitintuve įvykius):

  ```
  > tutorial
  ```

  (Čia ir toliau simbolis `>` reiškia, kad komanda vedama į `MadGraph5` terminalą)

2. Rekomenduojama atlikti supažindinimo su programa žingsnius (programa pati pasiūlys, ką įvesti į jos terminalą ir paaiškins, ką tai daro.

Padarius įvadą ir šiek tiek susipažinus su sintakse galima pabandyti ką nors susigeneruoti savarankiškai ir detaliau pasiaiškinti, kaip programa naudotis. Tam galima pabandyti atsakyti į žemiau pateiktus klausimus/užduotis (atsakymai į juos pateikiami dar žemiau).

### Klausimai

Klausimai ir atsakymai parengti remiantis [Marko Zaro sukurtomis mokomosiomis skaidrėmis](https://cp3.irmp.ucl.ac.be/projects/madgraph/attachment/wiki/Pavia2015/tutorial-pavia-2015.pdf "Skaidrės anglų kalba").

#### 1. Paprasti klausimai

1. Kaip sugeneruoti *tt̅*  procesą (medžio lygmens)?
2. Kokie partoniniai subprocesai įeina į sugeneruotą procesą?
3. Kiek Feinmano diagramų turi kiekvienas subprocesas?
4. Kaip atliekama sugeneruoto proceso kodo išvestis?

#### 2. Sudėtingesni klausimai (užduotys)

1. Apskaičiuokite *tt̅*  proceso reakcijos skerspjūvį, jeigu viršūninio kvarko masė būtų lygi 170 GeV, o protonų susidūrimo energija lygi 8 TeV (pvz., 2012-ųjų LHC)
2. Ar tarp sugeneruotų įvykių yra diagramų, kuriuose vyksta sąveikos su fotonu arba Z bozonu?
   1. Ar galėtųmėte jas pridėti?
   2. Kaip smarkiai tai pakeistų reakcijos skerspjūvį?
   3. Ką reiškia `WEIGHTED`?
3. Pakartokite skerspjūvio skaičiavimus, kai viršūninio kvarko masė yra lygi 172, 174, ..., 180 GeV
4. Ar galite padaryti taip, kad, norint pakartoti skaičiavimus, kiekvieną kartą iš naujo įsijungus programą nereiktų visų žingsnių įvedinėti iš naujo?

### Atsakymai

#### 1. Paprasti klausimai

1. *Kaip sugeneruoti tt̅  procesą (medžio lygmens)?*
```
> generate p p > t t~
```
2. *Kokie partoniniai subprocesai įeina į sugeneruotą procesą?*
```
> display processes
Process: g g > t t~ WEIGHTED=2
Process: u u~ > t t~ WEIGHTED=2
Process: c c~ > t t~ WEIGHTED=2
Process: d d~ > t t~ WEIGHTED=2
Process: s s~ > t t~ WEIGHTED=2
```

Taigi, sugeneruotas procesas susideda iš 5 subprocesų.

3. *Kiek Feinmano diagramų turi kiekvienas subprocesas?*
```
> display diagrams
```
Gali būti, kad šia komanda sugeneruoti `eps` failai bus sugadinti (greičiausiai yra dar kažkokių `python` versijų nesuderinamumų) ir jums jų pamatyti nepavyks. Tada galima pabandyti tokį variantą:
```
> open info.html
```
Atsidariusiame lange esančioje lentelėje pasirinkti nuorodą su užrašu „*html*“ stulpelyje „*FEYNMAN DIAGRAMS*“. Dešiniau esantis stulpelis „*SUBPROCESS*“ indikuoja subprocesus, kurių Feinmano diagramas galima peržiūrėti.

Taigi, subprocesas *gg→tt̅*  turi 3 Feinmano diagramas, o visi likę – po vieną.

4. *Kaip atliekama sugeneruoto proceso išvestis?*
```
> output norimas-direktorijos-vardas
```
### 2. Sudėtingesni klausimai (užduotys)

1. *Apskaičiuokite tt̅  proceso reakcijos skerspjūvį, jeigu viršūninio kvarko masė būtų lygi 170 GeV, o protonų susidūrimo energija lygi 8 TeV*

Jeigu po praeitų žingsnių neperkrovėme programos (priešingu atveju reikia iš naujo sugeneruoti procesą ir atilkti išvestį), užtenka įvesti tokią komandą:
```
> launch
```
Gavus pirmą pasirinkimo užklausą (joje galima pasirinkti, kokiomis programomis naudosimės) tiesiog spaudžiame „*Enter*“ (paliekame standartiškai numatytus nustatymus).

Tuo tarpu antra pasirinkimo užklausa siūlo modifikuoti konfigūracinius failus – „korteles“. Jeigu norime sumodeliuoti įvykius bei apskaičiuoti reakcijos skerspjūvį su nestandartiškais nustatymais, šias korteles teks pamodifikuoti. Standartiškai protonų susidūrimo energija yra nustatyta lygi 13 TeV (dabartinė LHC energija), o viršūninio kvarko masė – 173 GeV. Norint pakeisti šiuos parametrus galime modifikuoti pačias korteles:
- Įvedame skaičių „1“ ir spaudžiame „*enter*“. Pamatysime atidaryta failą `param_card.dat`. Jame randame eilutes, kuriose parašyta:
```
6500 = ebeam1 ! beam 1 total energy in GeV
6500 = ebeam2 ! beam 2 total energy in GeV
```
Šiose eilutėse nurodoma į priešingas puses lekiančių dalelių spindulių energija. Norint, kad modeliuotume protonų susidūrimus, esant 8 TeV energijai, turime skaičių 6500 pakeisti į 4000.
- Baigę redaguoti failą grįžtame į  tą patį pasirinkimų meniu. Tada įvedame skaičių „2“ ir spaudžiame „*Enter*“. Tada išvysime atidarytą failą `run_card.dat`. Jame randame tokias eilutes:
```
Block mass
	5 4.700000e00 # MB
	6 1.730000e02 # MT
   15 1.777000e00 # MTA
   23 9.118800e01 # MZ
   25 1.250000e02 # MH
```

Šios eilutės nustato modeliuojant naudojamas dalelių mases gigaelektronvoltais (einant iš viršaus į apačią: gelminis kvarkas, viršūninis kvarkas, taonas, Z bozonas ir Higso bozonas). Taigi, mums reikia pakeisti eilutėje, pasibaigiančioje `#MT` esančią skaitinę vertę į `1.700000e00`.

- Baigę redaguoti ir šį failą ir grįžę į tą patį meniu jau nevedame nieko ir tiesiog spaudžiame „*Enter*“. Tada programa sumodeliuos 10000 įvykių ir apskaičiuos proceso reakcijos skerspjūvį. Jį bus galima pamatyti terminalo lange atsiradusiame tekste bei automatiškai iššokančiame lange. Jeigu langas vis dėlto neiššoko, jį galima atsidaryti įvedus:
```
> open crossx.html
```
Turėtumėte gauti skerspjūvį, lygų maždaug 160±0.2 pb