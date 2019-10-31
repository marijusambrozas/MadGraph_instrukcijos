<script src='https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML'></script>


# `MadGraph5_aMC@NLO` instaliacija ir naudojimo pagrindai

## 1. Instaliacija

1. Nueiti į `MadGraph5_aMC@NLO` [internetinį puslapį](https://launchpad.net/mg5amcnlo "MG5_aMC@NLO internetinis puslapis")
2. Atsisiųsti naujausią `MadGraph5` versiją (žalia nuoroda ekrano dešinėje)
3. Įsikopijuoti atsisiųstą `tar.gz` failą į direktoriją, kurioje norite turėti `MadGraph` (išskleidus suspaustą failą nauja direktorija, talpinanti programos failus bus sukurta, tad pačiam jos sukūrimu rūpintis nebūtina)
4. Išskleisti suspaustą `tar.gz` failą: 

	```
	$ tar -xvzf MG5_aMC_vX.Y.Z.tar.gz
	```
	
	(Čia ir toliau simbolis `$` reiškia, kad komanda vedama į `bash` terminalą)

5. Pereiti į išskleistą direktoriją:
	
	```
	$ cd MG5_aMC_vX_Y_Z
	```
6. Paleisti `MadGraph`:
	
	```
	$ ./bin/mg5_aMC
	```
	1. Jeigu išmeta klaidą, patikrinkite, kokią `python` versiją naudojate:
	
		```
		$ python --version
		```
	2. Jeigu matote, kad naudojama `python3`, reikia aktyvuoti `python2`
	3. Su `Anaconda` tai galima padaryti taip:
		
		```
		$ conda create -n python2p7 python=2.7
		$ conda activate python2p7
		```
		
7. Įsijungus `./bin/mg5_aMC` atsiduriame `MadGraph5` terminale. Ten galime įjungti programos kūrėjų sukurtą supažindinimą su programa (jame jums teks sumodeliuoti viršūninio kvarko ir antikvarko poros sukūrimo Didžiajame hadronų greitintuve įvykius):

	```
	> tutorial
	```
	
	(Čia ir toliau simbolis `>` reiškia, kad komanda vedama į `MadGraph5` terminalą)
	
8. Rekomenduojama atlikti supažindinimo su programa žingsnius ir juos atliekant stengtis atsakyti į tokius klausimus (remiantis [Marko Zaro sukurtomis mokomosiomis skaidrėmis](https://cp3.irmp.ucl.ac.be/projects/madgraph/attachment/wiki/Pavia2015/tutorial-pavia-2015.pdf "Skaidrės anglų kalba")):
	1. Kaip sugeneruoti kokį nors (šiuo atveju \\( t\bar{t} \\) procesą?
	2. Kokie partoniniai subprocesai įeina į sugeneruotą procesą?