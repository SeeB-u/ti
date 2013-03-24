###Komputerowe wspomaganie nauczania przedmiotów ścisłych i przyrodniczych 

Pierwszy poznany program to MatLab (MATrix LABoratory)

###Początek MatLab:

* **ans** - "zmienna" w której jest przechowywany wynik działania, który nie został przypisany do jakiejkolwiek zmiennej,
* **help** - pomoc,
* **format** - sterowanie postacią wydruku,
* **format compact** - pozbędziemy się pustych linii,
* **format short** - wyświetlanie wartości zmiennych, obliczeń do 4 miejsca po przecinku,
* **format long** - wyświetlanie wartości zmiennych, obliczeń bardziej dokładnie,
* **help format** - pomoc odnośnie polecenia format,
*  ***nazwa zmiennej + enter*** - wyświetlenie wartości zmiennej,
*  ***zmienna=...*** - przypisanie wartości do zmiennej (np.: a=2),
*  **who** - wyświetlenie zmiennych,
*  **whos** - szczegółowe wyświetlenie zmiennych, 
*  **realmax** - największa liczba reprezentowana dokładnie,
*  **realmin** - najmniejsza liczba reprezentowana dokładnie,
*  **eps** - epsilon maszynowy (najmniejsza wartość, która powoduje wzrost liczby),
*  **clear('zmienna')** - usuwa zmienną,
*  **clear all** - usuwa wszystkie zmienne,
*  **clc** - czyści ekran,
*  **close all** - zamyka wszystkie okna graficzne (wykresy),
*  **w=[a1 a2 a3]** - stworzenie wektora (wierszowego) o wartościach a1, a2 oraz a3,
*  **w=[a1,a2,a3]** - jak wyżej,
*  **w=[a1;a2;a3]** - stworzenie wektora (kolumnowego) o wartościach a1, a2 oraz a3,
*  **w'** - transpozycja wektora w (z wierszowego w kolumnowy),
*  **lenght(x)** - liczba elementów wektora,
*  dodanie na końcu polecenia **;** - wstrzymuje wydruk,
*  ***ctrl+c*** - przerwanie wykonywanego procesu.


###Przydatne funkcje:

* **sqrt(...)** - pierwiastek (w ***...*** można podać wartość, zmienną, wektor, ...),
* **sin(...)** - sinus kąta podanego w radianach,
* **sind(...)** - sinus kąta podanego w stopniach,
* **cos(...)** - ...,
* **cosd(...)** - ...,
* **tan(...)** - ...,
* **tand(...)** - ...,
* **pi** - liczba pi (wartość),
* **factorial(n)** - silnia dla wartości n,
* **primes(n)** - liczby pierwsze mniejsze od n,
* **abs(x)** - wartość bezwzględna z x (liczby, zmiennej),
* **median(a)** - mediana (wartość środkowa z wektorze a),
* **std(a)** - odchylenie standardowe (w wektorze a),
* **max(a)** - wartość największa (wektora a),
* **min(a)** - wartość najmniejsza (wektora a),
* **mode(a)** - dominanta (wartość najbardziej popularna w wektorze a),
* **plot(x,y)** - rysuje wykres y od x,
* **plot(x,y,'o')** - rysuje wykres y od x za pomocą kółek,
* **plot(x,y,'o-')** - rysuje wykres y od x za pomocą kółek połączonych linią,
* **plot(x,y,'.')** - rysuje wykres y od x za pomocą kropek,
* **plot(x,y,'r-')** - rysuje wykres y od x za pomocą czerwonej linii,
* **plot(x,y,x,y1)** - rysuje wykres y od x oraz y1 od x (można dodawać kolory i kształty),
* **ylim([wartość1 wartość2])** - ograniczenia osi Y,
* **xlabel('nazwa')** - nazwa osi X,
* **hold on** - zatrzymuje wykres (kiedy stworzymy nowy wykres, poprzedni nie zniknie),
* **'\gamma'** - wypisuje symbole (greckie litery),
* **roots(w)** - pierwiastki wielomianu,
* **fzero** - pierwiastki wielomianu - metoda numeryczna (f=fzero(@(x) w [... ... ...]) -?


###Znaki specjalne:

* **.**
* **,**
* **;**
* **:**
* **()**
* **[]**
* **{}**
* **'**
* **...**
* **@**
* **\**
