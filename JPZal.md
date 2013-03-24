Moim zadaniem jest napisanie programu, który liczy wartość funkcji sinus dla zadanego kąta.<br>
Oczywiście nie mogę korzystać z wbudowanej funkcji sin() (przy użyciu: math.h).<br>
Z teorii - wartość funkcji sinus można przybliżyć do wartości sumy szeregu Maclaurina = x/1! – x^(3)/3! + x^(5)/5! –x^(7)/7!+…<br>


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


---

Dodano:

* użyto deklaracji stałych preprocesora (wartość delta),
* wykonywanie pętli dla zmiennej wartości (delta),
* liczenie błędu względnego,
* użyto operatora logicznego || - lub.

Efekt:

```c
#include <stdio.h>
#include <math.h>
#define delta 1e-12
int main() {
  int n=3, i=1;
	double wyraz,x,suma,blad;
	printf("Podaj kat w radianach: ");
	scanf("%lf",&x);
	suma=wyraz=x;
	printf("\n\n Nr wyrazu | Wartosc wyrazu    |    Wartosc szeregu \n");
	printf("---------------------------------------------------------\n");
	printf(" %9d | %17.14lf |   %17.14lf\n", i, wyraz , suma);
	do {
		wyraz=wyraz*(-(x*x)/((n-1)*n));
		n=n+2;
		suma=suma+wyraz;
		i++;
		printf(" %9d | %17.14lf |   %17.14lf\n", i, wyraz , suma);
	}
	while(wyraz>=delta || wyraz<=-delta);
		getchar();
		printf("\n\n Wartosc funkcji wbudowanej sin(%lf)=%17.14lf", x, sin(x));
		blad=(sin(x)-suma)/sin(x);
		printf("\n\n Blad wzgledny wynosi: %.20lf", blad);
		getchar();
		return 0;
		}
```
---
