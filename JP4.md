## Zadania - tablice

### Zadanie 1

Wypisz wszystkie elementy tablicy:
int dane[]={ -44 , 5 , 67 , -2 , 0 , 33 , 77 } 
w kolejności od pierwszego do ostatniego i odwrotnie.

```c
#include <stdio.h>
int
main ()
{
  int i, k, dane[] = { -44, 5, 67, -2, 0, 33, 77 };
  k = sizeof (dane) / sizeof (int);
  printf ("Rosnaco:\n\n");
  for (i = 0; i < k; i++)
    printf ("dane[%d]=%d\n", i, dane[i]);
  printf ("\n-----------------------\n\nMalejaco:\n\n");
  for (i = k - 1; i >= 0; i--)
    printf ("dane[%d]=%d\n", i, dane[i]);
  printf ("\n\nTak przy okazji - rozmiar tablicy to %d.", k);
  getchar ();


  return 0;
}
```


### Zadanie 2

Napisz program, który podany tekst wyświetli wielkimi literami.

```c
#include <stdio.h>
#include <ctype.h>
#define max 32
int
main ()
{
  char napis[max];
  int i = 0, c, k;
  printf ("Wprowadz napis:");
  while ((c = getchar ()) != EOF)
    {
      napis[i] = toupper (c);
      i++;
    }
  k = --i;
  for (i = 0; i <= k; i++)
    printf ("%c", napis[i]);
  getchar ();
  return 0;
}
```

### Zadanie 3

Napisz funkcję sprawdzającą, czy podana przez użytkownika liczba znajduje się w powyższej tablicy. (np. tablicy z zadania 1)

```c
#include <stdio.h>
int
main ()
{
  int dane[] = { -44, 5, 67, -2, 0, 33, 77 };
  int i = 0, x, k = 6, a = 0;
  printf ("Wprowadz liczbe:");
  scanf ("%d", &x);
  for (i = 0; i <= k; i++)
    {
      if (dane[i] == x)
        a = 1;
    }
  if (a == 1)
    printf ("\nLiczba %d znajduje sie w tablicy", x);
  else
    printf ("\nLiczba %d nie znajduje sie w tablicy", x);
  getchar ();
  getchar ();
  return 0;
}
```

### Zadanie 4

Znajdź maksymalną liczbę w tablicy liczb zmiennoprzecinkowych podanych przez użytkownika. 

```c
#include <stdio.h>
#define rozmiar 5

double emin (double dane[]);    //Funkcja szukająca element największy w tablicy
double emax (double dane[]);    //Funkcja szukająca element najmniejszy w tablicy


int
main ()
{
  double dane[rozmiar], x, max, min;
  int i;
  for (i = 0; i < rozmiar; i++)
    {
      printf ("Wprowadz liczbe nr %d: ", i + 1);
      scanf ("%lf", &x);
      dane[i] = x;
    }

  max = emax (dane);
  min = emin (dane);

  for (i = 0; i < rozmiar; i++)
    printf ("\nElemnt %d tablicy ma wartosc: %lf", i, dane[i]);
  printf ("\n\nElemnt najwiekszy to: %lf, a najmniejszy to: %lf.", max, min);

  getchar ();
  getchar ();
  return 0;
}



double
emin (double dane[])
{

  int i;
  double x, min = 1 / 0.0;
  for (i = 0; i < rozmiar; i++)
    {
      x = dane[i];
      if (x <= min)
        min = x;
    }
  return min;
}


double
emax (double dane[])
{
  int i;
  double x, max = -1 / 0.0;
  for (i = 0; i < rozmiar; i++)
    {
      x = dane[i];
      if (x >= max)
        max = x;
    }
  return max;
}
```

### Zadanie 5

Napisz funkcję obliczającą średnią arytmetyczną z liczb zawartych w tablicy liczb zmiennoprzecinkowych.

```c
#include <stdio.h>
#define rozmiar 5

double esrednia (double dane[]);        //Funkcja licząca średnią elementów tablicy


int
main ()
{
  double dane[rozmiar], x, srednia;
  int i;
  for (i = 0; i < rozmiar; i++)
    {
      printf ("Wprowadz liczbe nr %d: ", i + 1);
      scanf ("%lf", &x);
      dane[i] = x;
    }

  srednia = esrednia (dane);

  for (i = 0; i < rozmiar; i++)
    printf ("\nElemnt %d tablicy ma wartosc: %lf", i, dane[i]);
  printf ("\n\nSrednia to: %lf.", srednia);

  getchar ();
  getchar ();
  return 0;
}


double
esrednia (double dane[])
{
  int i;
  double x, suma = 0.0;
  for (i = 0; i < rozmiar; i++)
    suma += dane[i];
  return suma / rozmiar;
}
```

### Zadanie 6

Wypisz napis:
char tekst[]=”Tablica to podstawa programowania.”
 od końca do początku.

```c
#include <stdio.h>

int
main ()
{
  char tekst[] = "Tablica to podstawa programowania.";
  int rozmiar = sizeof (tekst) / sizeof (char), i, j = rozmiar - 1;
  char rewers[rozmiar];
  for (i = 0; i < rozmiar; i++, j--)
    rewers[i] = tekst[j];

//for(i=0;i<rozmiar;i++)
//printf("%c",tekst[i]);

  for (i = 0; i < rozmiar; i++)
    printf ("%c", rewers[i]);
  getchar ();
  return 0;
}
```

### Zadanie 7 (Niepoprawne rozwiązanie)!

Napisz funkcję void odKonca(char napis[]) która odwraca podany napis (taka funkcja jest potrzebna np. do zamiany liczb na system dwójkowy).

```c
#include <stdio.h>
#define rozmiar 32

void odKonca (char napis[]);

int
main ()
{
  char napis[rozmiar], rewers[rozmiar], c;
  int i, j;
  for (i = 0; i < rozmiar; i++)
    napis[i] = '\0';
  i = 0;
  printf ("Wprowadz napis:");
  while ((c = getchar ()) != EOF)
    {
      napis[i] = c;
      i++;
    }
  j = i + 1;
  for (i = 0; i < rozmiar; i++)
    printf ("%c", napis[i]);
//****************************************
  void odKonca (char napis[]);
//*****************************************
  getchar ();
  return 0;
}

void
odKonca (char napis[])
{
  int i, j = rozmiar - 1;
  char rewers[rozmiar];
  for (i = 0; i < rozmiar; i++, j--)
    rewers[i] = napis[j];
  for (i = 0; i < rozmiar; i++)
    printf ("%c", rewers[i]);
}
```

### Zadanie 8 (Niepoprawne rozwiązanie)!

Napisz funkcję zwracającą najmniejszy i największy element z tablicy liczb zmiennoprzecinkowych podanej jako argument funkcji. 

```c
#include <stdio.h>
#define rozmiar 5

double extr (double dane[]);    //Funkcja szukająca element największy i najmniejszy w tablicy

int
main ()
{
  double dane[rozmiar], x, min, max, b[2];
  int i;
  for (i = 0; i < rozmiar; i++)
    {
      printf ("Wprowadz liczbe nr %d: ", i + 1);
      scanf ("%lf", &x);
      dane[i] = x;
    }

  for (i = 0; i < rozmiar; i++)
    printf ("\nElemnt %d tablicy ma wartosc: %lf", i, dane[i]);
  *b = extr (dane);
  printf ("\n\nElemnt najwiekszy to: %lf, a najmniejszy to: %lf.", b[0],
          b[1]);
  getchar ();
  getchar ();
  return 0;
}


double
extr (double dane[])
{
  int i;
  double x, min = 1 / 0.0, max = -1 / 0.0, a[2];
  for (i = 0; i < rozmiar; i++)
    {
      x = dane[i];
      if (x <= min)
        min = x;
      if (x >= max)
        max = x;
    }
  a[0] = max;
  a[1] = min;
  printf ("\n\nElemnt najwiekszy to: %lf, a najmniejszy to: %lf.", a[0],
          a[1]);
  return *a;
}
```

### Zadanie 9

Napisać program, który pobiera od użytkownika n liczb i wczytuje je do tablicy. Napisać funkcję, która zwróci ostatnią liczbę tej tablicy podzielną przez 7. 

```c
#include <stdio.h>
#define rozmiar 5

int jest7 (int dane[]);

int
main ()
{
  int dane[rozmiar], i, x, a;
  for (i = 0; i < rozmiar; i++)
    {
      printf ("Wprowadz liczbe nr %d: ", i + 1);
      scanf ("%d", &x);
      dane[i] = x;
    }
  for (i = 0; i < rozmiar; i++)
    printf ("\nElemnt %d tablicy ma wartosc: %d", i, dane[i]);
  a = jest7 (dane);
  if (a == 1)
    printf ("\n\nNie wystepuje liczba podzielna przez 7");
  else
    printf ("\n\nOstatnia podana liczba podzielna przez 7 to: %d", a);
  getchar ();
  getchar ();
  return 0;
}

int
jest7 (int dane[])
{
  int i, x, a = 1;
  for (i = 0; i < rozmiar; i++)
    if (dane[i] % 7 == 0)
      a = dane[i];
  return a;
}
```

### Zadanie 10

Napisać funkcję obliczającą iloczyn skalarny dwóch wektorów n-wymiarowych. 

```c
#include <stdio.h>
#define n 3                     //Rozmiar wektorów

double iloczyn (double dane1[], double dane2[]);        //Deklaracja funkcji

int
main ()
{
  double dane1[n], dane2[n], x;
  int i;

  for (i = 0; i < n; i++)       //wczytanie skladowych wektora nr 1
    {
      printf ("Wprowadz skladowa wektora pierwszego nr %d: ", i + 1);
      scanf ("%lf", &x);
      dane1[i] = x;
    }

  puts (" ");                   //Oddzielenie składowych wektora nr 1 oraz nr 2

  for (i = 0; i < n; i++)       //wczytanie skladowych wektora nr 2
    {
      printf ("Wprowadz skladowa wektora drugiego nr %d: ", i + 1);
      scanf ("%lf", &x);
      dane2[i] = x;
    }

  printf ("\nWektor nr 1: [");  //Wypisanie wektora nr 1
  for (i = 0; i < n; i++)
    {
      printf ("%lf", dane1[i]);
      if (i < n - 1)
        printf (",");
    }
  printf ("].");

  printf ("\nWektor nr 2: [");  //Wypisanie wektora nr 2
  for (i = 0; i < n; i++)
    {
      printf ("%lf", dane2[i]);
      if (i < n - 1)
        printf (",");
    }
  printf ("].");

  x = iloczyn (dane1, dane2);   //Wykorzystanie funkcji

  printf ("\n\nIloczyn skalarny tych wektorow wynosi = %lf.", x);

  getchar ();
  getchar ();
  return 0;
}

double
iloczyn (double dane1[], double dane2[])        //Definicja funkcji
{
  int i;
  double x = 0.0;
  for (i = 0; i < n; i++)
    x += (dane1[i]) * (dane2[i]);
  return x;
}
```

### Zadanie 11

Napisz funkcję która transponuje tablicę kwadratową double tab[128][128] podaną jako argument. Napisz i wykorzystaj funkcję void wyswietlMacierz(double m[128][128], int wierszy, int kolumn); 

```c

```
