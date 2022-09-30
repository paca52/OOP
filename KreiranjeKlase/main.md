# Intro
## Enkapsulacija i atributi klase
Klasa se definise kljucnom recju **class**:

>`class Moja_klasa {  };`    

<br/>Klase su jako slicne C strukturama samo sto sada imaju i <ins>funkcije</ins> u njima.

<ins>Primer strukture Tacka:</ins>
>```cpp
>struct sTacka {
>	float x, y;
>};
>```

<ins>Primer klase Tacka:</ins>
>```cpp
>class cTacka { //<- Naziv klase
>    float x, y; //<- atributi klase
>};
>```

<ins>**Klasinim atributima se nazivaju sve promenljive unutar klase.**</ins>

### <br/>Koja je razlika strukture i klase?
---------------------------------------------------------------------------
Pored toga sto klase mogu da imaju i funkcije u njima, one imaju i opciju **ENKAPSULACIJE**.

Enkapsulacija moze biti: *privatna(private)*, *zasticena(protected)* i *javna(public)*.
<br/><ins>*Enkapsulacija esencijalno opisuje ko moze da pristupi podatcima (atributima klase).*</ins>

<br/>Tako, recimo, kada je deo podataka enkapsuliran kao **privatan**, <ins>to znaci da samo klasa moze da pristupi svojim atributima.</ins>
<br/>Dok recimo kada je enkapsulacija** javna(public)**, <ins>onda svi mogu da pristupe tom atributu/ima koji su oznaceni kao javni.</ins>


- Primer: 
>```cpp
>class cTacka { 
>// ovde moze da stoji "private:", a i ne mora jer je private po default-u
>    float x, y; 
>};
>
>int main() {
>	cTacka moja_tacka; // definisanje objekta klase
>	moja_tacka.x = 3; // GRESKA jer je DEFAULT enkapsulacija za klasu PRIVATE
>}
>```

- Tako da kada bismo primenili enkapsulaciju na public, error bi nesato:
>```cpp
>class cTacka {
>public:
>	float x, y;
>};
>
>int main() {
>	cTacka moja_tacka;
>	moja_tacka.x = 3; Nema greske jer su x i y javni atributi
>}
>```
---------------------------------------------------------------------------

Recimo da imamo vise atributa i ne zelimo da svi budu privatni, nego zelimo da neki budu i javni.
To bismo uradili na sledeci nacin:

>```cpp
>class Tacka {
>private:
>	float x;
>public:
>	float y;
>};
>
>int main() {
>	Tacka moja_tacka;
>	moja_tacka.x = 3; // GRESKA; x je privatan member(atribut)
>	moja_tacka.y = 3; // Nema greske; y je javan atribut
>}
>```

> `output:` **`error: 'float Tacka::x' is private within this context`**

---------------------------------------------------------------------------
NOTE:
- zasticene(protected) enkapsulacije cemo se dotaci kasnije jer ona ima veze uglavnom sa NASLEDJIVANJEM

## Metode klase

Kao sto sam napomenuo, klase mogu da u sebi imaju odredjene <ins>funkcije</ins> koje se drugacije nazivaju ***metode***.

**Metode** se definisu kao i svaka druga funkcija, samo sto se funkcija zapravo nalazi u viticastim zagradama klase. 
Primer:
>```cpp
>class Tacka {
>public: // mora biti public da bismo mogli da pristupimo podatcima u main-u
>	// Atributi klase
>	float x, y; 
>	
>	// Metoda klase
>	float zbirTacaka() { 
>		return x + y;
>	}
>	// klasa moze da pristupi svojim atributima nezavisno od njihove enkapsulacije
>};
>```

### Kako koristimo metode?
---------

Metode koristimo(pozivamo) na sledeci nacin:
>```cpp
>int main() {
>	Tacka moja_tacka;
>	moja_tacka.x = moja_tacka.y = 3; // Inicijalizovanje atributa
>									 // tako da je x = y = 3
>	
>	// Promenljiva koja ce da sacuva vrednost koju vraca metoda zbirTacaka()
>	float zbirMojihKoordinata = moja_tacka.zbirTacaka();
>
>	// ispis
>	cout << "zbir kordinata x i y = " << zbirMojiKoordinata << endl;
>	
>	return 0;
>}
>```

>`output:` **`zbir kordinata x i y = 6`**
## Zasto koristiti ENKAPSULACIJU?
Zamisliti klasu <ins>*Trougao*</ins> koju ce opisati sledeci kod:
>```cpp
>class Trougao {
>public:
>	float a, b, c;
>
>	float Obim() {
>		return a + b + c;
>	}
>	int da_li_je_n_jednak_stranici(int n) {
>		if(a == n || b == n || c == n) return 1;
>		return 0;
>	}
>
>};
>```
Sta nas sprecava da stavimo neke nemoguce vrednosti za a, b i c?
<br/>Trenutno je moguce uraditi sledece:
>```cpp
>int main() {
>	Trougao moj_trougao;
>	moj_trougao.a = -1; // stranici trougla ne mogu biti negativne
>	moj_trougao.b = -2;
>	moj_trougao.c = -3;
>
>	cout << "Obim trougla: " << moj_tougao.Obim() << endl;
>
>	int n;
>	cin >> n; // unos nekog broja n
>
>	if(moj_tougao.da_li_je_n_jednak_stranici(n) == 1)
>		cout << "postoji stranice te duzine << endl;
>	else
>		cout << "ne postoji stranica te duzine << endl;
>	
>	return 0;
>}
>```

```
input: -1
```
```
output: Obim trougla: -6
	postoji stranice te duzine
```

Da bismo izbegli mogucnost da korisnik postavi neke nemoguce vrednosti, <ins>**uglavnom sve atribute stavljamo da su privatni.**</ins>

-----------
### Ako su svi atributi privatni, kako da im pristupimo?
----------------
Da bi smo pristupili <ins>**privatnim**</ins> atributima klase, moramo napisati specijalnu vrstu funkcije koja se zove **getter**. Pored *getter-a* postoji i **setter**.
- **getter** - **public** funkcija koja <ins>vraca vrednost</ins> nekog atributa klase
- **setter** - **public** funkcija koja <ins>postavlja vrednost</ins> nekog atributa klase
---------
Primer *getter-a* i *setter-a* za nasu klasu <ins>*Trougao*</ins>:
>```cpp
>class  Trougao  {  
>private: // postavljamo da su nam atributi 
>	float a, b, c;
>public: 	
>	float  Obim() {  
>		return a + b + c;  
>	}
>	int  da_li_je_n_jednak_stranici(int n) {  
>		if(a == n || b == n || c == n)  return  1;  
>		return  0;  
>	}  
>	// getteri - funkcije za vracanje vrednosti atributa klase
>	float getA() { // getter za stranicu a
>		return a;
>	}
>	float getB() { return b; } // getter za stranicu b
>	float getC() { return c: } // getter za stranicu c
>
>	// setteri - funkcije za postavljanje vrednosti atributa klase
>	float setA(float novo_a) { // setter za stranicu a
>		a = novo_a;
>	}
>	
>	float getB(float novo_b) { // setter za stranicu b
>		b = novo_b; 
>	}
>	
>	float getC(float novo_c) { // setter za stranicu c
>		c = novo_c; 
>	}
>};
>```
Sada nije moguce postaviti vrednosti iz main-a, ali smo napisali funkciju koja samo posavlja bilo koju vrednost za nase atribute(stranice u ovom slucaju).
Tako da sada moramo da dodamo uslove da ne bismo postavili stranice na neke nemoguce vrednosti.
Ovako bi izgledala funkcija **setA()**:
>```cpp
>float setA(float novo_a) { // setter za stranicu a
>	if(novo_a > 0)
>		a = novo_a;
>}
>```
Analogno ovako ce izgledati i funkcije setB() i setC()
