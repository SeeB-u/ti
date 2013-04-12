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

int wartBezwzgledna(int x);

int main() {
    int x,y;
    puts("Podaj liczbe: ");
    scanf("%d",&x);
    y=wartBezwzgledna(x);
    printf("\n\n Wartosc bezwzgledna z %d wynosi %d", x, y);
    getchar();
    getchar();
    return 0;
        }   

int wartBezwzgledna(int x) {
    if(x<=0)
    x=-x;
    return x;    
}
```

### Treść zadania 3
Napisz funkcję obliczającą a do potęgi n dla n należącego do N za pomocą pętli.

```c
#include <stdio.h>
int main() {
    double a,x=1;
    int n, i;
    puts("Podaj liczbe: ");
    scanf("%lf",&a);
    puts("Podaj wykladnik (liczba naturalna): ");
    scanf("%d",&n);
    for(i=1;i<=n;i++){
    x=x*a;
}
    printf("\n\n Wartosc %lf do potegi %d wynosi %lf ", a, n, x);
    getchar();
    getchar();
    return 0;
        }
```

lub jako funkcja

```c
#include <stdio.h>
double potegaAn(double a, int n);

int main() {
    double a, x;
    int n;
    puts("Podaj liczbe: ");
    scanf("%lf",&a);
    puts("Podaj wykladnik (liczba naturalna): ");
    scanf("%d",&n);
    x=potegaAn(a,n);
    printf("\n\n Wartosc %lf do potegi %d wynosi %lf ", a, n, x);
    getchar();
    getchar();
    return 0;
        }   
double potegaAn(double a, int n) {
    int i;
    double x=1.0;
    for(i=1;i<=n;i++){
    x=x*a;
}
    return x;
}
```

### Treść zadania 4 jest zbyt skomplikowana
w skrócie - napisać funkcję, która liczy pierwiastek z liczby oraz porównuje go z pierwiastkiem z tej liczby z funkcji wbudowanej

```c
#include <stdio.h>
#include <math.h>

double pierwA(double a);

int main() {
    double a,x,y, blad;
    puts("Podaj liczbe: ");
    scanf("%lf",&a);//Będzie liczony pierwiastek z tej liczby "a"
    x=pierwA(a);    //Pierwiastek policzony moją funkcją
    y=sqrt(a);      //Pierwiastek policzony funkcją wbudowaną sqrt
    blad=(x-y)/y;   //Błąd względny
    printf("\n\n Pierwiastek z liczby %lf wynosi %lf, \n\n a z funkcji sqrt() wynosi\
 %lf, \n\n zatem blad wzgledny wynosi %.16le", a, x, y, blad>=0 ? blad : -blad);
    getchar();
    getchar();
    return 0;
        }
        
double pierwA(double a) {
    double x, epsilon=1e-15;
    x=(a/2.0)+1.0;
    while((x-(a/x))>epsilon*x || (x-(a/x))<-epsilon*x) // lub fabs(x-a/x)>epsilon*x
    x=(x+(a/x))/2.0;
    return x;
    }
```

### Treść zadania 5 (jest w formie algorytmu)
Szybkie boliczanie potęgi n-tej liczby a

```c
#include <stdio.h>
int potegaAn(int a, int n);

int main() {
    int a, p, n;
    puts("Podaj liczbe naturalna: ");
    scanf("%d",&a);
    puts("Podaj wykladnik (liczba naturalna): ");
    scanf("%d",&n);
    p=potegaAn(a,n);
    printf("\n\n Wartosc %d do potegi %d wynosi %d ", a, n, p);
    getchar();
    getchar();
    return 0;
        }   
        
int potegaAn(int a, int n) {
    int i=n, p=1, q=a;
    while(i>0){
    if(i%2!=0)
    p=p*q;
    q=q*q;
    i=i/2;
}

    return p;
}
```

### Treść zadania 6
Rozbuduj funkcję z poprzedniego zadania tak, aby funkcja działała także dla ujemnych potęg (n całkowite) i dla a będących typu double.

```c
#include <stdio.h>
double potegaAn(double a, int n);

int main() {
    int n;
    double a, p;
    puts("Podaj liczbe: ");
    scanf("%lf",&a);
    puts("Podaj wykladnik (liczba naturalna): ");
    scanf("%d",&n);
    p=potegaAn(a,n);
    printf("\n\n Wartosc %lf do potegi %d wynosi %lf ", a, n, p);
    getchar();
    getchar();
    return 0;
        }   
        
double potegaAn(double a, int n) {
    int i=n, minus=0;
    double p=1.0, q=a;
           if(i<0){
           minus=1;
            i=-i;
                 }
                 while(i>0){
                      if(i%2!=0)
                      p=p*q;
                      q=q*q;
                      i=i/2;
                            }
                     if(minus==0)             
                     return p;
                     else
                     return (1.0/p);
}
```
