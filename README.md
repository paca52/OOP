# OBJEKTNO ORIJENTISANO PROGRAMIRANJE (OOP)

Postoje *proceduralno* i *objektno* programiranje.

### Razlike izmedju *PROCEDURALNOG I OBJEKTNOG PROGRAMIRANJA*

- Proceduralno programiranje - pisemo funkcije koje vrse operacije nad podatcima, dok u objektnom pisemo **objekte** koji ce u sebi sadrzati i podatke i funkcije koje ce da vrse operacije nad njima.

- U *proceduralno programiranju* probleme resavamo odozgo-nadole (top - bottom), sto znaci da krecemo od generalnog problema i razbijamo ga na manje probleme i tako resavamo problem.
- U *objektno orijentisanom programiranju* resavamo probleme odozdo-nagore (bottom - top), sto znaci da krecemo od najnize jedinice (***klase***) koju mozemo da uocimo i putem nje nastavljamo da resimo celokupan problem.

## Osobine OOP

Objektno orijentisano programiranje je zasnovano na **4** glavna principa, a to su:

- ***Enkapsulacija*** (private, protected, public)
- ***Nasledjivanje***
- ***Polimorfizam***
- ***Apstrakcija***

## Uputstvo

Kroz foldere ce se uglavnom pojavljivati fajl sa nazivom ***Makefile***.
*Makefile*, uglavnom, sluzi za kompajliranje i pokretanje C/C++ programa.
U njemu stoje pravila po kojima ce da se kompajlira program.
Da bi pokrenuli *Makefile*, neophodo je da imamo instaliran ***make***.
On se moze skinitu komandom:
- Linux
	```
	sudo apt install make
	```
 - Windows ([Chocolatey](https://chocolatey.org/))
	 ```
	 choco install make
	 ```

Makefile pokrecemo tako sto ukucamo **`make`** u konzoli dok smo u folderu gde se nalazi `Makefile`.  

>![Capture](https://user-images.githubusercontent.com/104862724/193351671-6a9f8614-4ec5-4be3-9f20-0192e94b1114.PNG)

 
NAPOMENA: 
- Makefile ne mora obavezno da se zove 'Makefile', ali to je standard.
- `make` i poznavanje *make-a* **nije neophodno**

### Zasto `make` ?

Vremenom klase postaju obine i neophodno ih je razdvojiti u vise `.hpp` *(sadrze deklaraciju funkcija, klasa i slicno)* i `.cpp` *(sadrze kod (tela) funkcija i metoda)* fajlova kako bi kod bio pregledniji i laksi da se razume.

Nije neophodno koristiti Makefile-ove, sve je ovo moguce uraditi na vise razlicitih nacina, kao naprimer u [CodeBlocks-u](https://stackoverflow.com/questions/15146788/linking-header-files-in-codeblocks):
>1.  Click the "Project" tab, it's in the top right side.
>2.  Within the "Project" tab click the "Add Files..." option.
>3.  Highlight your Header file and any other files associated with your header file, like if you put your header files definitions in a .cpp file.
>4.  Compile and Run.
    
### Neke od opcija koje su mogu pojaviti u Makefile-u

| OPCIJA | DESKRIPCIJA | OUTPUT |
| :----: | :---------- | :----- |
| -c | Kreira .o (object) file | file_name.o |
| -o `name` | Preimenuje output fajl u `name` | `name`(.exe) |
| -Wall | Izbaci dodatne warning-e pri kompajliranju koda (npr. nekoriscene promenljive i sl. ) | Izbacijue warning-e u konzolu pri kompajliranju |
| -Wextra | Jos dodatnih warning-a | Izbacijue warning-e u konzolu pri kompajliranju |
| -g | Dodaje posebne informacije koje sluze za debagovanje koda |  |
| -O0 | Opcija za optimizaciju koda (-Optimization0) | Moze se desiti da kompajler zameni neki blok kod pri kompaliranju za efikasniji blok koda/efikasniju funkciju koja postize isti efekat kap blok koda |




### Eksterni resursi vezani za `make`
- [Tutorijal koji obuhvata sve sto je potrebno za pisanje pocetnih Makefile-ova i razumevanje opcija za kompajliranje.](https://www.youtube.com/watch?v=GExnnTaBELk&list=PL0MNpg4RB5lWDqu1gHBSR8IU7NtnR0XtO&index=1&t=512s)
