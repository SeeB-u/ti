### Treść zadania 1
Napisz funkcję obliczającą pole kuli o podanym promieniu.

```c
#include <stdio.h>
#include <math.h>

double pole(double r);

int main() {
    double r, p;
    printf("Podaj promien kuli: ");
    scanf("%lf",&r);
    p=pole(r);
    printf("\n\n Pole kola o promieniu %lf ma wartosc %lf", r, p);
    getchar();
    getchar();
    return 0;
        }   

double pole(double r) {
    double p;
    p=4*M_PI*r*r;                                                          
    return p;    
}
```
### Treść zadania 2
Napisz funkcję warBezwzgledna zwracajaca wartość bezwzględną z liczby całkowitej.

```c
#include <stdio.h>

double wartBezwzgledna(double x);

int main() {
    double x,y;
    puts("Podaj liczbe: ");
    scanf("%lf",&x);
    y=wartBezwzgledna(x);
    printf("\n\n Wartosc bezwzgledna z %lf wynosi %lf", x, y);
    getchar();
    getchar();
    return 0;
        }   

double wartBezwzgledna(double x) {
    if(x<0)
    x=-x;
    return x;    
}
```
