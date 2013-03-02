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
    printf("Dlugosc okregu o promieniu %lf wynosi: %.lf \n" ,r,2*M_PI*r);
    printf("Pole kola o promieniu %lf wynosi: %.lf \n" ,r,M_PI*r*r);
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
- działa tylko do napisów.
