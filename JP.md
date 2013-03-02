# JP

```c
int main() {
  printf("witaj świecie\n");
}
```

---

Program na użycie liczb double (zmiennych przecinkowych)

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

żeby wyświetlić odpowiednią ilość miejsc po przecinku wpisujemy w następujący sposób: %. **ilość** lf

---

Program do liczenia długości okręgu i pola koła


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
Trzeba użyć 2 razy 

```c
getchar(); 
getchar();
```

ponieważ pierwszy znak jest pobierany jako enter po wpisaniu promienia.

```c
#include <math.h> 
```

dodaje funkcje matematyczne (np. wartość pi, którą wywołujemy jako M_PI).
Także można użyć:
```c
puts("Podaj dlugosc promienia:")
```
-działa tylko do napisów.

---
Program przeliczający temperatury (skal Celsjusza i Fahrenheita) -działający w pętli while

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
    double celsius;
    int fahr;
    int lower, upper, step;
    lower=0;
    upper=300;
    step=20;
    fahr=lower;
    while(fahr<=upper) {
                       celsius=5.0*(fahr-32.0)/9.0;
                       printf("%d \t %.2lf \n", fahr, celsius);
                       fahr=fahr+step;
                       }
    getchar();
    return 0;
}
```

trzeba pamiętać, aby liczby wpisywać w następujący sposób 9.0, a nie 9 itd.
