Kod programu liczacego miejsca zerowe trojmianu kwadratowego:

```c
#include <stdio.h>
#include <math.h>
int main() {
    double a,b,c,delta,x1,x2;
    printf("Podaj parametr a: ");
    scanf("%lf", &a);
    if(a==0)     {
    printf("\n!To nie jest trojmian kwadratowy!");
    getchar();
    getchar();
    return 1;
                  }
                  else {
    printf("\nPodaj parametr b: ");
    scanf("%lf", &b);
    printf("\nPodaj parametr c: ");
    scanf("%lf", &c);
    delta=(b*b)-(4*a*c);
    if(delta<0) {
                printf("\nBrak rozwiazania w zbiorze R");
                }
                else {
                     if(delta==0) {
                                  x1=-b/(2*a);
                                  printf("\nMiejsce zerowe to %lf", x1);
                                  }
                                  else {
                                       x1=(-b-sqrt(delta))/(2*a);
                                       x2=(-b+sqrt(delta))/(2*a);
                                       printf("\nMiejsca zerowe to: x1=%lf,\t x2=%lf", x1,x2);
                                       }
                     }
                     }
                     getchar();
                     getchar();
                     return 0;
                }                          
```

---

Kod programu wypisujacego liczby doskonale:

```c
#include <stdio.h>
int main() {
    int i, j=0, suma=0;
    for(i=1;i<=10000;i++) {
                        suma=0;
                        for(j=1;j<i;j++)
                                         if(i%j==0)
                                         suma=suma+j;
                                         if(suma==i)                      
                                         printf("\n%d",suma); 
                           }
    getchar();
    return 0;
}
```
