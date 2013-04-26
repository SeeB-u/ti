## Zadania - tablice

### Zadanie 1

Wypisz wszystkie elementy tablicy:
int dane[]={ -44 , 5 , 67 , -2 , 0 , 33 , 77 } 
w kolejności od pierwszego do ostatniego i odwrotnie.

```c
#include <stdio.h>
int main() {
    int i,k, dane[]={ -44, 5, 67, -2, 0, 33, 77 };
    k=sizeof(dane)/sizeof(int);
    printf("Rosnaco:\n\n");
    for(i=0; i<k; i++)
    printf("dane[%d]=%d\n",i,dane[i]);
    printf("\n-----------------------\n\nMalejaco:\n\n");
    for(i=k-1; i>=0; i--)
    printf("dane[%d]=%d\n",i,dane[i]);
    printf("\n\nTak przy okazji - rozmiar tablicy to %d.",k);
    getchar();
    
    
return 0;
}
```


### Zadanie 2

Napisz program, który podany tekst wyświetli wielkimi literami.

```c
#include <stdio.h>
#include <ctype.h>
#define max 32
int main() {
    char napis[max];
    int i=0,c,k;
    printf("Wprowadz napis:");
    while((c=getchar())!=EOF)
    {
    napis[i]=toupper(c);
    i++;
    }
    k=--i;
    for(i=0;i<=k;i++)
    printf("%c", napis[i]);
    getchar();   
    return 0;
}
```

### Zadanie 3

Napisz funkcję sprawdzającą, czy podana przez użytkownika liczba znajduje się w powyższej tablicy. (np. tablicy z zadania 1)

```c
#include <stdio.h>
int main() {
    int dane[]={-44, 5, 67, -2, 0, 33, 77};
    int i=0,x,k=6,a=0;
    printf("Wprowadz liczbe:");
    scanf("%d",&x);
    for(i=0;i<=k;i++)    {
    	if(dane[i]==x)
    	a=1;
						}
	if(a==1)
    	printf("\nLiczba %d znajduje sie w tablicy", x);
	else
		printf("\nLiczba %d nie znajduje sie w tablicy", x);
    getchar();  
    getchar(); 
    return 0;
}
```
