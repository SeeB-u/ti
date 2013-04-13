```c
#include <stdio.h>
int main() {
    int i, dane[]={ -44, 5, 67, -2, 0, 33, 77 };
    printf("Rosnaco:\n\n");
    for(i=0; i<7; i++)
    printf("dane[%d]=%d\n",i,dane[i]);
    printf("\n-----------------------\n\nMalejaco:\n\n");
    for(i=6; i>=0; i--)
    printf("dane[%d]=%d\n",i,dane[i]);
    getchar();
return 0;
}
```
