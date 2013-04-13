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


Zad2

```c
#include <stdio.h>
#include <ctype.h>
int main() {
    char napis[20];
    int i=0,c,k;
    printf("Wprowadz napis (malymi literami):");
    while((c=getchar())!=EOF)
    {
    napis[i]=c;
    i++;
    }
    k=i;
     for(i=0;i<k;i++) {
                  napis[i]=toupper(napis[i]);
                            i++;
 }   
    for(i=0;i<k;i++)
                printf("%c", napis[i]);
    getchar();   
    return 0;
}
```
