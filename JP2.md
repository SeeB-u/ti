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
    int i, j=0, suma=0, k=0;
    for(i=1;i<=10000;i++) {
                        suma=0;
                        for(j=1;j<i;j++)
                                         if(i%j==0)
                                         suma=suma+j;
                                         if(suma==i){
                                         k++;                      
                                         printf("\n Oto %d liczba doskonala = %d",k,suma); 
                                         }
                           }
    getchar();
    return 0;
}
```

Kod programu wypisujacego trojki pitagorejskie:

```c
#include <stdio.h>
#include <math.h>
int main () {
    int a,b,c,k=1;
    for(a=1;a<100;a++)
    {
        for(b=a;b<100;b++)
                for(c=b;c<100;c++){
                         if(a*a+b*b==c*c){
                                  printf("\nTrojkat nr %2d: %2d,%2d,%2d.",k,a,b,c);
                                       k++;
                                       if(k>20)    {
                                       getchar();
                                       return 0;
                                                   }
                                        }
                               }
     }
return 0;
}
```

Kod programu szukajacego wartosc minimalna i maksymalna:

```c
#include <stdio.h>
int main() {
    double zero=0.0;
    double max=-1/zero; /*minus nieskonczonosc*/
    double min=1/zero;  /*plus nieskonczonosc*/
    double x;
    int i,n;
    do {
    printf("Podaj ilosc liczb: ");
    scanf("%d",&n);
    if(n<1)
    printf("\nco najmniej 1\n\n ");
}
    while(n<1);
    for(i=1;i<=n;i++) {
                     printf("Podaj liczbe nr %d: ", i);
                     scanf("%lf",&x);
                     if(x<=min)
                          min=x;
                     if(x>=max)
                          max=x;
                       }
                       printf("\nLiczba najmniejsza to: %.14lf",min);
                       printf("\nLiczba najwieksza to: %.14lf", max);
    getchar();
    getchar();
    return 0;
}
```

---

Dodano program wypisujacy dni tygodnia:

```c
#include <stdio.h>
int main() {
int x;
printf("Podaj dzień: ");
scanf("%d", &x);
x=x%7;
      switch(x) {
          case 1:
          printf("Poniedzialek");
          break;
          case 2:
          printf("Wtorek");
          break;
          case 3:
          printf("Sroda");
          break;
          case 4:
          printf("Czwartek");
          break;
          case 5:
          printf("Piatek");
          break;
          case 6:
          printf("Sobota");
          break;
          case 0:
          printf("Niedziela");
          break;
          }
    getchar();
    getchar();
    return 0;
}
```
