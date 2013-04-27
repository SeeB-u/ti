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

```

### Zadanie 5

Napisz funkcję obliczającą średnią arytmetyczną z liczb zawartych w tablicy liczb zmiennoprzecinkowych.

```c

```

### Zadanie 6

Wypisz napis:
char tekst[]=”Tablica to podstawa programowania.”
 od końca do początku.

```c

```

### Zadanie 7

Napisz funkcję void odKonca(char napis[]) która odwraca podany napis (taka funkcja jest potrzebna np. do zamiany liczb na system dwójkowy).

```c

```

### Zadanie 8

Napisz funkcję zwracającą najmniejszy i największy element z tablicy liczb zmiennoprzecinkowych podanej jako argument funkcji. 

```c

```

### Zadanie 9

Napisać program, który pobiera od użytkownika n liczb i wczytuje je do tablicy. Napisać funkcję, która zwróci ostatnią liczbę tej tablicy podzielną przez 7. 

```c

```

### Zadanie 10

Napisać funkcję obliczającą iloczyn skalarny dwóch wektorów n-wymiarowych. 

```c

```

### Zadanie 11

Napisz funkcję która transponuje tablicę kwadratową double tab[128][128] podaną jako argument. Napisz i wykorzystaj funkcję void wyswietlMacierz(double m[128][128], int wierszy, int kolumn); 

```c

```
