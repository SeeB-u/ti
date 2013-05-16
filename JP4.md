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
#define rozmiar 5               //Rozmiar tablicy

double emax (double dane[]);    //Deklaracja funkcji szukającaej element największy w tablicy

int
main ()
{
  double dane[rozmiar], x, max;
  int i;
  for (i = 0; i < rozmiar; i++) //Wczytywanie wartości do tablicy
    {
      printf ("Wprowadz liczbe nr %d: ", i + 1);
      scanf ("%lf", &x);
      dane[i] = x;
    }

  max = emax (dane);            //Użycie funkcji

  for (i = 0; i < rozmiar; i++) //Wypisanie tablicy
    printf ("\nElemnt %d tablicy ma wartosc: %lf", i, dane[i]);
  printf ("\n\nElemnt najwiekszy z tablicy to: %lf.", max);     //Wypisanie max

  getchar ();
  getchar ();
  return 0;
}

double
emax (double dane[])            //Definicja funkcji szukającej element największy w tablicy
{
  int i;
  double max = dane[0];        //Pierwsza wartość w tablicy
  for (i = 0; i < rozmiar; i++)
    {
      if (dane[i] >= max)
        max = dane[i];
    }
  return max;
}
```

### Zadanie 5

Napisz funkcję obliczającą średnią arytmetyczną z liczb zawartych w tablicy liczb zmiennoprzecinkowych.

```c
#include <stdio.h>
#define rozmiar 5

double esrednia (double dane[], int n);        //Funkcja licząca średnią elementów tablicy


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

  srednia = esrednia (dane, rozmiar);

  for (i = 0; i < rozmiar; i++)
    printf ("\nElemnt %d tablicy ma wartosc: %lf", i, dane[i]);
  printf ("\n\nSrednia to: %lf.", srednia);

  getchar ();
  getchar ();
  return 0;
}


double
esrednia (double dane[], int n)
{
  int i;
  double x, suma = 0.0;
  for (i = 0; i < n; i++)
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

### Zadanie 7

Napisz funkcję void odKonca(char napis[]) która odwraca podany napis (taka funkcja jest potrzebna np. do zamiany liczb na system dwójkowy).

```c
#include <stdio.h>
#include<string.h>
#define rozmiar 32

void odKonca (char napis[]);

int
main ()
{
  char napis[rozmiar], c;
  int i;

  for (i = 0; i < rozmiar; i++) //Null-owanie tablicy
    napis[i] = '\0';

  i = 0;

  printf ("Wprowadz napis:");   //Wczytywanie napisu
  while ((c = getchar ()) != '\n')
    {
      napis[i] = c;
      i++;
    }
  napis[i]='\0';                  //Napis musi się kończyć symbolem \0 (null)

  printf("%s\n\n", napis);       //Wyświetlanie napisu

  odKonca (napis);              //Użycie funkcji

  puts(napis);                  //Wyświetlanie odwróconego napisu
  getchar ();
  return 0;
}

void
odKonca (char napis[])          //Funcka do wyświetlania napisu "od tyłu"
{
  int i, j = strlen(napis) - 1;
  char rewers[strlen(napis)];
  
  for (i = 0; i < strlen(napis); i++, j--)
    rewers[i] = napis[j];

  for (i = 0; i < strlen(napis); i++)
    napis[i] = rewers[i];
}
```

### Zadanie 8

Napisz funkcję zwracającą najmniejszy i największy element z tablicy liczb zmiennoprzecinkowych podanej jako argument funkcji. 

```c

  min = max = dane[0];
  for (i = 1; i < n; i++)
    {
      x = dane[i];#include <stdio.h>
#define rozmiar 5

struct minMax {
       double min;
       double max;
       };

struct minMax extr (double dane[], int n);    //Funkcja szukająca element największy i najmniejszy w tablicy

int
main ()
{
  double dane[rozmiar], x, min, max;
  int i;
  struct minMax mM;
  for (i = 0; i < rozmiar; i++)
    {
      printf ("Wprowadz liczbe nr %d: ", i + 1);
      scanf ("%lf", &x);
      dane[i] = x;
    }

  for (i = 0; i < rozmiar; i++)
    printf ("\nElemnt %d tablicy ma wartosc: %lf", i, dane[i]);
mM = extr (dane, rozmiar);
  printf ("\n\nElemnt najmniejszy to: %lf, a najwiekszy to: %lf.",mM.min, mM.max);
  getchar ();
  getchar ();
  return 0;
}

struct minMax extr (double dane[], int n)
{
  int i;
  double x, min, max;
  struct minMax mM;
      if (x <= min)
        min = x;
      if (x >= max)
        max = x;
    }
  mM.min = min;
  mM.max = max;
  return mM;
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
#define N 10                     //Rozmiar wektorów

double iloczyn (double dane1[], double dane2[], int n);
void wysWekt(double dane[], int n);
void wprWekt(double dane[], int n);

int
main ()
{
  double dane1[N], dane2[N], x;
  int i, n;
  printf ("Wprowadz rozmiar wektorow: ");
  scanf ("%d", &n);
     
  printf("\n\nWprowadz skladowa wektora pierwszego\n");
  wprWekt(dane1, n);
  
  puts (" ");  
  
  printf("\n\nWprowadz skladowa wektora drugiego\n");
  wprWekt(dane2, n);
    
  printf("\n\nWektor pierwszy = ");
  wysWekt(dane1, n);
  printf("\n\nWektor drugi = ");
  wysWekt(dane2, n);

  x = iloczyn (dane1, dane2, n);   //Wykorzystanie funkcji

  printf ("\n\nIloczyn skalarny tych wektorow wynosi = %lf.", x);

  getchar ();
  getchar ();
  return 0;
}

double
iloczyn (double dane1[], double dane2[], int n)        //Definicja funkcji
{
  int i;
  double x = 0.0;
  for (i = 0; i < n; i++)
    x += (dane1[i]) * (dane2[i]);
  return x;
}

void wysWekt(double dane[], int n){
       int i;
       printf ("[");
  for (i = 0; i < n; i++)
    {
      printf ("%lf", dane[i]);
      if (i < n - 1)
        printf (",");
    }
  printf ("].");
}

void wprWekt(double dane[], int n) {
  int i;
  double x;
  for (i = 0; i < n; i++)       
    {
      printf ("nr %d: ", i + 1);
      scanf ("%lf", &x);
      dane[i] = x;
    }
}
```

### Zadanie 11

Napisz funkcję która transponuje tablicę kwadratową double tab[128][128] podaną jako argument. Napisz i wykorzystaj funkcję void wyswietlMacierz(double m[128][128], int wierszy, int kolumn); 

```c
#include <stdio.h>
#define N 128                     //Rozmiar tablicy

double trans (double tab[N][N], int wierszy, int kolumn);

void wyswietlMacierz (double m[N][N], int wierszy, int kolumn);

int
main ()
{
  double tab[N][N], tabT[N][N], x;
  int i, j, wierszy, kolumn;
  
          printf ("Wprowadz ilosc wierszy: ");
          scanf ("%d", &wierszy);
          printf ("\nWprowadz ilosc kolumn: ");
          scanf ("%d", &kolumn);
          
          printf ("\n\n");          //Odstęp przy wyświetlaniu
          
  for (i = 0; i < wierszy; i++)       //Wczytanie  tablicy (wiersze)
    {
      for (j = 0; j < kolumn; j++)   //Wczytywanie kolumn
        {
          printf ("Wprowadz skladowa tablicy [%d,%d]: ", i + 1, j + 1);
          scanf ("%lf", &x);
          tab[i][j] = x;
        }
    }
  printf ("\n\n");              //Odstęp przy wyświetlaniu

  wyswietlMacierz (tab, wierszy, kolumn);  //Wyświetlanie tablicy

  printf ("\n\n");              //Odstęp po wyświetleniu tablicy

  for (i = 0; i < wierszy; i++)       //Klonowanie tablicy
  for (j = 0; j < kolumn; j++)
    tabT[i][j] = tab[i][j];
  
  trans (tabT, wierszy, kolumn);
  
  wyswietlMacierz (tabT, kolumn, wierszy);  //Wyświetlanie tablicy

  getchar ();
  getchar ();
  return 0;
}

double
trans (double tab[N][N], int wierszy, int kolumn)
{
  double tabT[N][N];
  int i, j, k;
  for (i = 0; i < wierszy; i++)       //Transponowanie tablicy tab na tablice tabT
    for (j = 0; j < kolumn; j++)
      tabT[j][i] = tab[i][j];
      
  for (i = 0; i < kolumn; i++)       //Klonowanie tablicy
  for (j = 0; j < wierszy; j++)
    tab[i][j] = tabT[i][j];
}

void
wyswietlMacierz (double m[N][N], int wierszy, int kolumn)
{
  int i, j;
  for (i = 0; i < wierszy; i++)
    for (j = 0; j < kolumn; j++)
      printf ("%lf %c", m[i][j], j == kolumn - 1 ? '\n' : ' ');
}
```
