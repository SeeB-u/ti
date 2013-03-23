```c
#include <stdio.h>
#include <math.h>
int main() {
  int n=3, i=1;
  double wyraz,x,suma;
  printf("Podaj kat w radianach: ");
  scanf("%lf",&x);
  suma=wyraz=x;
  printf("\n\n Nr wyrazu | Wartosc wyrazu | Wartosc szeregu \n");
  printf("---------------------------------------------\n");
  printf(" %9d | %14lf | %lf\n", i, wyraz , suma);
  do {
     wyraz=wyraz*(-(x*x)/((n-1)*n));
     n=n+2;
     suma=suma+wyraz;
     i++;
     printf(" %9d | %14.11lf | %.11lf\n", i, wyraz , suma);
     }
     while(n<=19);
  getchar();
  printf("\n\n sin (%lf)=%.11lf", x, sin(x));
  getchar();
  return 0;
}
```
