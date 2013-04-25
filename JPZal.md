#Mój sinus<br>

Moim zadaniem jest napisanie programu, który liczy wartość funkcji sinus dla zadanego kąta.<br>
Oczywiście nie mogę korzystać z wbudowanej funkcji sin() (przy użyciu: math.h).<br>
Z teorii - wartość funkcji sinus można przybliżyć do wartości sumy szeregu Maclaurina = x/1! – x^(3)/3! + x^(5)/5! –x^(7)/7!+…<br>


```c
#include <stdio.h>
#include <math.h>
int
main ()
{
  int n = 3, i = 1;
  double wyraz, x, suma;
  printf ("Podaj kat w radianach: ");
  scanf ("%lf", &x);
  suma = wyraz = x;
  printf ("\n\n Nr wyrazu | Wartosc wyrazu | Wartosc szeregu \n");
  printf ("---------------------------------------------\n");
  printf (" %9d | %14lf | %lf\n", i, wyraz, suma);
  do
    {
      wyraz = wyraz * (-(x * x) / ((n - 1) * n));
      n = n + 2;
      suma = suma + wyraz;
      i++;
      printf (" %9d | %14.11lf | %.11lf\n", i, wyraz, suma);
    }
  while (n <= 19);
  getchar ();
  printf ("\n\n sin (%lf)=%.11lf", x, sin (x));
  getchar ();
  return 0;
}
```

W pierwszej wersji program:
* wykonuje stałą ilość kroków (ilość sumowanych wyrazów szeregu, czyli cykli pętli), co sprawia, że jest słaby jakościowo,
* dodatkowo wypisuje, co krok:
	* który to krok,
	* wartość wyrazu,
	* sumę szeregu.


---
---


###W tej wersji program:

* sumuje szereg, aż do osiągnięcia przez wyraz szeregu wartości bardzo małej (delta),
* oblicza błąd względny obliczonej sumy szeregu względem funkcji wbudowanej sin(),
* nadal wyświetla, który to krok,
* nadal pokazuje wartość wyrazu.

###Podsumowując - dodano:

* użyto deklaracji stałych preprocesora (wartość delta),
* wykonywanie pętli dla zmiennej wartości (delta),
* liczenie błędu względnego,
* użyto operatora logicznego || - lub.

Efekt:

```c
#include <stdio.h>
#include <math.h>
#define delta 1e-12
int
main ()
{
  int n = 3, i = 1;
  double wyraz, x, suma, blad;
  printf ("Podaj kat w radianach: ");
  scanf ("%lf", &x);
  suma = wyraz = x;
  printf ("\n\n Nr wyrazu | Wartosc wyrazu    |    Wartosc szeregu \n");
  printf ("---------------------------------------------------------\n");
  printf (" %9d | %17.14lf |   %17.14lf\n", i, wyraz, suma);
  do
    {
      wyraz = wyraz * (-(x * x) / ((n - 1) * n));
      n = n + 2;
      suma = suma + wyraz;
      i++;
      printf (" %9d | %17.14lf |   %17.14lf\n", i, wyraz, suma);
    }
  while (wyraz >= delta || wyraz <= -delta);
  getchar ();
  printf ("\n\n Wartosc funkcji wbudowanej sin(%lf)=%17.14lf", x, sin (x));
  blad = (sin (x) - suma) / sin (x);
  printf ("\n\n Blad wzgledny wynosi: %.20lf", blad);
  getchar ();
  return 0;
}
```

***
***

###Kolejny etap miał na celu użycie nowych elementów w moim kodzie programu:

* instrukcji warunkowej (eliminuje błąd bezwzględny ujemny),
* użycie funkcji (nazywanej czasem podprogramem lub procedurą).

Efekt:

```c
#include <stdio.h>
#include <math.h>
#define delta 1e-12

double sinus (double x);

int
main ()
{
  double x, blad;
  printf ("Podaj kat w radianach: ");
  scanf ("%lf", &x);
  blad = (sin (x) - sinus (x)) / sin (x);
  printf ("\n\n Wartosc funkcji wbudowanej sin(%lf)=%17.14lf", x, sin (x));
  printf ("\n\n Blad wzgledny wynosi: %.20lf", blad >= 0 ? blad : -blad);
  getchar ();
  getchar ();
  return 0;
}

double
sinus (double x)
{
  int n = 3, i = 1;
  double wyraz, suma;
  suma = wyraz = x;
  printf ("\n\n Nr wyrazu |    Wartosc wyrazu | Wartosc szeregu \n");
  printf ("--------------------------------------------------\n");
  do
    {
      wyraz = wyraz * (-(x * x) / ((n - 1) * n));
      n = n + 2;
      suma = suma + wyraz;
      printf (" %9d | %17.14lf | %17.14lf\n", i, wyraz, suma);
      i++;
    }
  while (wyraz >= delta || wyraz <= -delta);
  return suma;
}
```

***
***

###Kolejne poprawki:
* zmniejszenie kodu programu o jedną zmienną (i),
* poprawienie błędu - poprzednio program robił o jeden krok w pętli za dużo:

```c
#include <stdio.h>
#include <math.h>
#define delta 1e-12

double sinus (double x);

int
main ()
{
  double x, blad;
  printf ("Podaj kat w radianach: ");
  scanf ("%lf", &x);
  blad = (sin (x) - sinus (x)) / sin (x);
  printf ("\n\n Wartosc funkcji wbudowanej sin(%lf)=%17.14lf", x, sin (x));
  printf ("\n\n Blad wzgledny wynosi: %.20lf", blad >= 0 ? blad : -blad);
  getchar ();
  getchar ();
  return 0;
}

double
sinus (double x)
{
  int n = 3;
  double wyraz, suma;
  suma = wyraz = x;
  printf ("\n\n Nr wyrazu |    Wartosc wyrazu |   Wartosc szeregu \n");
  printf ("--------------------------------------------------\n");
  while (wyraz >= delta || wyraz <= -delta)
    {
      printf (" %9d | %17.14lf | %17.14lf\n", (n - 1) / 2, wyraz, suma);
      wyraz = wyraz * (-(x * x) / ((n - 1) * n));
      suma = suma + wyraz;
      n += 2;
    }
  return suma;
}
```

***
***

###Drobne poprawki:

* zmiana pętli while na pętlę for,
* użycie skróconych wyrażeń,
* zmiana nomenklatury,
* zwiększenie dokładności programu,
* skrócenie zapisu funkcji sinus(x):

```c
#include <stdio.h>
#include <math.h>
#define delta 1e-15

double sinus (double x);

int
main ()
{
  double x, blad;
  printf ("Podaj kat w radianach: ");
  scanf ("%lf", &x);
  blad = (sin (x) - sinus (x)) / sin (x);
  printf ("\n\n Wartosc funkcji wbudowanej sin(%lf)=%18.15lf", x, sin (x));
  printf ("\n\n Blad wzgledny wynosi: %.20lf", blad >= 0 ? blad : -blad);
  getchar ();
  getchar ();
  return 0;
}

double
sinus (double x)
{
  int n;
  double wyraz, suma;
  suma = wyraz = x;
  printf ("\n\n Nr wyrazu |     Wartosc wyrazu |       Suma szeregu \n");
  printf ("----------------------------------------------------\n");
  for (n = 3; wyraz >= delta || wyraz <= -delta; n += 2, suma += wyraz)
    {
      printf (" %9d | %18.15lf | %18.15lf\n", (n - 1) / 2, wyraz, suma);
      wyraz = wyraz * (-(x * x) / ((n - 1) * n));
    }
  return suma;
}
```
***
***
###Kolejne udoskonalenia:

* zamiana pętli **for** na **do – while**,
* zmniejszenie liczby wykonywanych kroków, które są niepotrzebne:

```c
#include <stdio.h>
#include <math.h>
#define delta 1e-15

double sinus (double x);

int
main ()
{
  double x, blad;
  printf ("Podaj kat w radianach: ");
  scanf ("%lf", &x);
  blad = (sin (x) - sinus (x)) / sin (x);
  printf ("\n\n Wartosc funkcji wbudowanej sin(%lf)=%18.15lf", x, sin (x));
  printf ("\n\n Blad wzgledny wynosi: %.20lf", blad >= 0 ? blad : -blad);
  getchar ();
  getchar ();
  return 0;
}

double
sinus (double x)
{
  int n = 1;
  double wyraz = x, suma = 0.0;
  printf ("\n\n Nr wyrazu |     Wartosc wyrazu |       Suma szeregu \n");
  printf ("----------------------------------------------------\n");
  do
    {
      n += 2;
      suma += wyraz;
      printf (" %9d | %18.15lf | %18.15lf\n", (n - 1) / 2, wyraz, suma);
      wyraz *= (-(x * x) / ((n - 1) * n));
    }
  while (wyraz >= delta || wyraz <= -delta);
  return suma;
}
```

### Przebudowa gruntowna kodu programu
w taki sposób, aby program wczytywał wartość początkową oraz końcową dziedziny dla funkcji sin(x), a następnie obliczał sin(x) z funkcji wbudowanej, sinus(x) z mojej funkcji oraz błąd względny z krokiem „przyrost” i wyświetlał to w formie tabeli.

```c
#include <stdio.h>
#include <math.h>
#define delta 1e-15							//delta - wartość minimalna wyrazu szereguu Maclaurina, która przerwie działanie pętli

double sinus(double x);						//deklaracja mojej funkcji liczącej wartość sinusa dla argumentu x

int main() {
    double x, y, suma, blad, przyrost=0.2;  //x - wartość początkowa
    										//y - wartość końcowa
    										//suma - suma szeregu Maclaurina
    										//blad - błąd względny mojej funkcji względem funkcji wbudowanej sin(x)
    										//przyrost - przyrost argumentu x w kolejnych krokach
    
    do {									//pętla - wczytywanie przedziału
		puts("Podaj kat w radianach (wartosc poczatkowa): ");
    	scanf("%lf",&x);    
		puts("Podaj kat w radianach (wartosc koncowa): ");
    	scanf("%lf",&y);
    	if(x>y)								//instrukcja w razie błędu
    		puts("\nWartosc koncowa nie moze byc mniejsza od wartosci poczatkowej - sprobuj ponownie\n\n");
		}
	while(y<x);
	
    puts("  \n\n  Wartosc x |       Moj sinus(x) |   Wbudowany sin(x) | Blad wzgledny"); //konstrukcja tabeli
    puts("  ----------|--------------------|--------------------|--------------");
    
	do {									//pętla - uzupełnianie tabeli ze skokiem = przyrost
		suma=sinus(x);						//odniesienie do funkcji sinus(x)
    	blad=(sin(x)-suma)/sin(x);			//obliczenie błędu względnego
    	printf(" %10.2lf |%19.15lf |%19.15lf |%11.2le\n", x, suma, sin(x),blad>=0 ? blad : -blad);
    	x+=przyrost;
		}    
	while(x<=y);

	getchar();
    getchar();
    return 0;
        }   

double sinus(double x) {					//Moja funkcja sinus(x) - definicja funkcji, pobiera argument - x
    int n;
    double wyraz, suma;						//suma szeregu Maclaurina
    suma=wyraz=x;							//w pierwszym kroku suma ciągu = pierwszy wyraz ciągu = argument funkcji - x
 	for(n=3;wyraz>=delta || wyraz<=-delta; n+=2) {  //pętla działa, dopóki kolejny wartość bezwzględna wyraz szeregu nie przekroczy wartości minimalnej 
        	wyraz*=(-(x*x)/((n-1)*n));		//obliczanie kolejnego wyrazu szeregu
        	suma+=wyraz;					//zwiększanie sumy szeregu o obliczony wyraz
    }
    return suma;    						//funkcja zwraca wartość - suma
}
```
