```c
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

#define MAX_STUDENTOW 15

void lista(struct student Studenci[], int iloscStudentow);
void zapisz(struct student Studenci[], const char * const  nazwaPliku, int iloscStudentow);
int dodaj(struct student Studenci[], int iloscStudentow);
int odczytaj(struct student Studenci[], const char * const  nazwaPliku, int iloscStudentow);

enum oceny { ndst=2, dst, db, bdb };

struct student {
       char imie[12];
       char nazwisko[16];
       enum oceny ocena;
};

int main(){
    int k, iloscStudentow=0;
    struct student Kowalski={"Jan", "Kowlaski", db};
    struct student Studenci[MAX_STUDENTOW];
    FILE *plik;
    const char * const nazwaPliku="studenci.dat";
    /* staly wskaznik do stalego napisu */
    

   // printf("Podaj co chcesz zrobic: \n1 - Wyswietl wszystkich studentow,\n2 - zapis danych do pliku,\n3 - dodaj element do tablicy, \n4 - odczytaj dane z pliku,\n5 - srednia studentow.");
   // scanf("%d",k);

    
    Studenci[0]=Kowalski; /*przypisanie całej struktury */
    iloscStudentow++;
      
    iloscStudentow = dodaj(Studenci,iloscStudentow); 
    
    /*Studenci[1].ocena=444; */
    /* W ANSI C nie jest sprawdzana poprawnosc przypisana ! */
    /*Dopiero C++ nie pozwala na przypisanie 'int' do 'enum' ! */
    
    zapisz(Studenci, nazwaPliku, iloscStudentow);
      
lista(Studenci, iloscStudentow);
iloscStudentow  = odczytaj(Studenci, nazwaPliku, iloscStudentow);
      getchar();
      getchar();
      return 0;
      }                         

void lista(struct student Studenci[],int iloscStudentow){
    int k;   
    for(k=0; k<iloscStudentow; k++)
      printf("%s %s %d\n", Studenci[k].imie, Studenci[k].nazwisko, Studenci[k].ocena);

      }

void zapisz (struct student Studenci[], const char * const  nazwaPliku, int iloscStudentow){
  FILE *plik;
  int k;
    if((plik=fopen(nazwaPliku, "w"))==NULL) {
      fprintf(stderr, "Nie moge otworzyc pliku %s\n", nazwaPliku);
      exit(2); }
      
    for(k=0; k<iloscStudentow; k++)
      fprintf(plik, "%s %s %d\n", Studenci[k].imie, Studenci[k].nazwisko, Studenci[k].ocena);
     
    if(fclose(plik)!=0) {
      fprintf(stderr, "Nie moge zamknac pliku %s\n", nazwaPliku);
      exit(3); } 
     }

int dodaj(struct student Studenci[], int iloscStudentow){
    char imie[12], nazwisko[16];
    int ocena;
    enum oceny ocena1;
    printf("Podaj imie: ");
    scanf("%s",imie);
    strncpy(Studenci[iloscStudentow].imie, imie, 12);
    Studenci[iloscStudentow].imie[11]='\0'; /*poprawne zakonczenie napisu ! */
    
    printf("Podaj nazwisko: ");
    scanf("%s",nazwisko);
    strncpy(Studenci[iloscStudentow].nazwisko, nazwisko, 16);
    Studenci[iloscStudentow].nazwisko[15]='\0';
    
    printf("Podaj ocene: ");
    scanf("%d",&ocena);
    switch (ocena)
    {
    case 2:
      ocena1=ndst;
      break;
    case 3:
      ocena1=dst;
      break;
    case 4:
      ocena1=db;
      break;
    case 5:
      ocena1=bdb;
      break;
    default:
      printf ("Zle podana ocena");
      break;
    }
    Studenci[iloscStudentow].ocena=ocena1;
    iloscStudentow++;
    return iloscStudentow;
    }
    
int odczytaj(struct student Studenci[], const char * const  nazwaPliku, int iloscStudentow){
    int k;
    FILE *plik; int o;
    enum oceny ocena1;
    for(k=0; k<iloscStudentow; k++)
      {
             fscanf(plik, "%s %s %d\n", Studenci[k].imie, Studenci[k].nazwisko, &o);
      switch (o)
    {
    case 2:
      ocena1=ndst;
      break;
    case 3:
      ocena1=dst;
      break;
    case 4:
      ocena1=db;
      break;
    case 5:
      ocena1=bdb;
      break;
    default:
      printf ("Zle podana ocena");
      break;
    }
    }
    for(k=0; k<iloscStudentow; k++)
      printf("%s %s %d\n", Studenci[k].imie, Studenci[k].nazwisko, Studenci[k].ocena);
      return iloscStudentow;
     }
```

```c
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

#define MAX_STUDENTOW 15

void lista(struct student Studenci[], int iloscStudentow);
void zapis(struct student Studenci[], const char * const  nazwaPliku, int iloscStudentow);
int dodaj(struct student Studenci[], int iloscStudentow);
int odczytaj(struct student Studenci[], const char * const  nazwaPliku);

enum oceny { ndst=2, dst, db, bdb };

struct student {
       char imie[12];
       char nazwisko[16];
       enum oceny ocena;
};

int main(){
    int k, iloscStudentow=0;
    struct student Kowalski={"Jan", "Kowlaski", db};
    struct student Studenci[MAX_STUDENTOW];
    FILE *plik;
    const char * const nazwaPliku="studenci.dat";
    /* staly wskaznik do stalego napisu */
    

   do {
   printf("\n\nPodaj co chcesz zrobic: \n1 - Wyswietl wszystkich studentow,\n2 - zapis danych do pliku,\n3 - dodaj element do tablicy, \n4 - odczytaj dane z pliku,\n5 - srednia studentow,\ninna wartosc - zakonczenie programu.\n\n");
   scanf("%d",&k);
   if(k==1){
   printf("\n\n");
   lista(Studenci,iloscStudentow);
   }
   if(k==2)
   zapis(Studenci, nazwaPliku, iloscStudentow);
   if(k==3)
   iloscStudentow = dodaj(Studenci,iloscStudentow);
   if(k==4)
   iloscStudentow  = odczytaj(Studenci, nazwaPliku);
   }
   while (k<6 && k>0);
    
   // Studenci[0]=Kowalski; /*przypisanie całej struktury */
   // iloscStudentow++;
      
    //iloscStudentow = dodaj(Studenci,iloscStudentow); 
    
    /*Studenci[1].ocena=444; */
    /* W ANSI C nie jest sprawdzana poprawnosc przypisana ! */
    /*Dopiero C++ nie pozwala na przypisanie 'int' do 'enum' ! */
    
  //  zapis(Studenci, nazwaPliku, iloscStudentow);
      
//lista(Studenci, iloscStudentow);
//iloscStudentow  = odczytaj(Studenci, nazwaPliku);
     
      getchar();
      return 0;
      }                         

void lista(struct student Studenci[],int iloscStudentow){
    int k;   
    for(k=0; k<iloscStudentow; k++)
      printf("%s %s %d\n", Studenci[k].imie, Studenci[k].nazwisko, Studenci[k].ocena);

      }

void zapis (struct student Studenci[], const char * const  nazwaPliku, int iloscStudentow){
  FILE *plik;
  int k;
    if((plik=fopen(nazwaPliku, "w"))==NULL) {
      fprintf(stderr, "Nie moge otworzyc pliku %s\n", nazwaPliku);
      exit(2); }
      
    for(k=0; k<iloscStudentow; k++)
      fprintf(plik, "%s %s %d\n", Studenci[k].imie, Studenci[k].nazwisko, Studenci[k].ocena);
     
    if(fclose(plik)!=0) {
      fprintf(stderr, "Nie moge zamknac pliku %s\n", nazwaPliku);
      exit(3); } 
     }

int dodaj(struct student Studenci[], int iloscStudentow){
    char imie[12], nazwisko[16];
    int ocena;
    enum oceny ocena1;
    printf("Podaj imie: ");
    scanf("%s",imie);
    strncpy(Studenci[iloscStudentow].imie, imie, 12);
    Studenci[iloscStudentow].imie[11]='\0'; /*poprawne zakonczenie napisu ! */
    /*
    printf("Podaj imie: ");
    scanf("%s",Studenci[iloscStudentow].imie);
    Studenci[iloscStudentow].imie[11]='\0';
    */
    printf("Podaj nazwisko: ");
    scanf("%s",nazwisko);
    strncpy(Studenci[iloscStudentow].nazwisko, nazwisko, 16);
    Studenci[iloscStudentow].nazwisko[15]='\0';
    
    printf("Podaj ocene: ");
    scanf("%d",&ocena);
    switch (ocena)
    {
    case 2:
      ocena1=ndst;
      break;
    case 3:
      ocena1=dst;
      break;
    case 4:
      ocena1=db;
      break;
    case 5:
      ocena1=bdb;
      break;
    default:
      printf ("Zle podana ocena");
      break;
    }
    Studenci[iloscStudentow].ocena=ocena1;
    iloscStudentow++;
    return iloscStudentow;
    }
    
int odczytaj(struct student Studenci[], const char * const  nazwaPliku){
    FILE *plik; int o;
    enum oceny ocena1;
    int k, iloscStudentow;
    if((plik=fopen(nazwaPliku, "r"))==NULL) {
      fprintf(stderr, "Nie moge otworzyc pliku %s\n", nazwaPliku);
      exit(2); }
    iloscStudentow=0;
    while(fscanf(plik, "%s %s %d\n", Studenci[iloscStudentow].imie, Studenci[iloscStudentow].nazwisko, &o) == 3)
    {  
    switch (o)
           {
            case 2:
            ocena1=ndst;
            break;
            case 3:
            ocena1=dst;
            break;
            case 4:
            ocena1=db;
            break;
            case 5:
            ocena1=bdb;
            break;
            default:
            printf ("Zle podana ocena");
            break;
            }
    Studenci[iloscStudentow].ocena=ocena1;
    iloscStudentow++;
    }
    if(fclose(plik)!=0) {
      fprintf(stderr, "Nie moge zamknac pliku %s\n", nazwaPliku);
      exit(3); }
      
      return iloscStudentow;
     }
```
