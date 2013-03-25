# Języki programowania (C) 

## - wstęp

```c
int main() {
  printf("witaj świecie\n");
}
```

---

Kod programu na użycie liczb double (zmiennych przecinkowych - podwójnej precyzji):

```c
# include <stdio.h>
int main () {
    double a, b;
    a=3.0;
    b=7.0;
    printf("%lf x %lf = %lf \n" ,a, b, a*b);
    printf("%lf - %lf = %lf \n" ,a, b, a-b);
    printf("%lf + %lf = %lf \n" ,a, b, a+b);
    printf("%lf / %lf = %lf \n" ,a, b, a/b);
    getchar();
    return 0;
}
```

Aby wyświetlić odpowiednią ilość miejsc po przecinku wpisujemy w następujący sposób: %. **ilość** lf

---

Kod programu do liczenia długości okręgu i pola koła:


```c
#include <stdio.h>
#include <math.h>
int main () {
    double r;
    printf("Podaj dlugosc promienia:\n");
    scanf("%lf", &r);
    printf("Dlugosc okregu o promieniu %lf wynosi: %lf \n" ,r,2*M_PI*r);
    printf("Pole kola o promieniu %lf wynosi: %lf \n" ,r,M_PI*r*r);
    getchar();
    getchar();
    return 0;
}
```
Trzeba użyć 2 razy:

```c
getchar(); 
getchar();
```

ponieważ pierwszy znak jest pobierany jako enter przechowywany w buforze po wpisaniu promienia.

```c
#include <math.h> 
```

dodaje funkcje matematyczne (np. wartość pi, którą wywołujemy jako M_PI).
Także można użyć:
```c
puts("Podaj dlugosc promienia:")
```
- działa tylko do napisów.

---
Kod programu przeliczającego temperatury (skal Celsjusza i Fahrenheita) - działający w pętli while:

```c
#include <stdio.h>
int main () {
    int fahr, celsius;
    int lower, upper, step;
    lower=0;
    upper=300;
    step=20;
    fahr=lower;
    while(fahr<=upper) {
                       celsius=5*(fahr-32)/9;
                       printf("%d \t %d \n", fahr, celsius);
                       fahr=fahr+step;
                       }
    getchar();
    return 0;
}
```
\t -znak tabulacji.

Zmienienie programu w taki sposób, aby temperatura w Celsjuszach była przeliczana i wyświetlana do 2 miejsca po przecinku:

```c
#include <stdio.h>
int main () {
    double celsius, fahr;
    int lower, upper, step;
    lower=0;
    upper=300;
    step=20;
    fahr=lower;
    while(fahr<=upper) {
                       celsius=5*(fahr-32)/9;
                       printf("%.0lf \t %.2lf \n", fahr, celsius);
                       fahr=fahr+step;
                       }
    getchar();
    return 0;
}
```

czasami trzeba pamiętać, aby liczby wpisywać w następujący sposób 9.0, a nie 9 itd.<br>
Wynik działania jest typu takiego, jakiego była najbardziej sprecyzowana liczba w działaniu.<br>
Sposób wyświetlania %5.1lf oznacza, że liczba będzie wyświetlona na 5 polach z dokładnością do 1 miejsca po przecinku<br>
<br><br><br>

Przerobienie kodu programu na pętlę for:

```c
#include <stdio.h>
#define LOWER 0
#define UPPER 300
#define STEP 20
int main() {
    int fahr;
    for(fahr=LOWER;fahr<=UPPER;fahr=fahr+STEP)
    printf("%3d %6.1lf \n", fahr, (5.0/9.0)*(fahr-32));
    getchar();
    return 0;
}
```
Przy czym:
```c
#define LOWER 0
```
stałe preprocesora - pamiętać, aby nie używać średnika!

---

Kod programu obliczający ciąg Fibonacciego (pętla do-while):

```c
#include <stdio.h>
int main()
{
      int u1, u2, u3; /*na kolejne wyrazy ciągu*/
      int n;          /*numer wyrazu*/
      int i;          /*licznik*/
      
      do {
          printf("Podaj numer wyrazu (co najmniej 3):");
          scanf("%d", &n);
          }
      while(n<3);
      u2=u1=1;        /*dwa pierwsze wyrazy*/
      i=2;
      while(i++<n)    /*uwaga, działa tylko dla n>2*/
                  {
                      u3=u1+u2;
                      u1=u2;
                      u2=u3;
                  }
                  /*inna możliwość*/
                  /*for(i=3; i<=n; i++, u1=u2, u2=u3) u3=u1+u2;*/
      printf("Wyraz o numerze %d ma wartosc %d", n, u3);
getchar();
getchar();
return 0;
}
```

---
Kod programu służącego do rysowania choinki (użycie pętli for):

```c
#include <stdio.h>
#define znak '*' /*znak wypełnienia*/
int main() {
    int lbwier; /*całkowita liczba wierszy*/
    int lw;     /*licznik wierszy*/
    int lodst;  /*liczba odstępów poprzedzających gwiazdkę*/
    int j;
    printf("ile wierszy?");
    scanf("%d",&lbwier);
    for(lw=0; lw<lbwier; lw++)
    {
              lodst=lbwier-lw-1;
              for(j=0; j<lodst; j++)
              putchar(' ');
              for(j=0; j<2*lw+1; j++)
              putchar(znak);
              putchar('\n');
    }
    getchar();
    getchar();
return 0;
}
```
Funkcja: 
```c
putchar(' ');
```
wyświetla pojedynczy znak.
<br>
*W apostrofach umieszczamy pojedynczy znak.
