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
