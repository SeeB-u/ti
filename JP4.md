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
