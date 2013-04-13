# Notatki do Technologii Internetowych

> Dzień bez kodowania jest dniem straconym.


Znaczniki:

* p
* ul, ol
  * li
* img
* h

Szablon pliku HTML5:
```html
<!doctype html>
<html lang=pl>
<head>
  <meta charset=utf-8>
  <title>Szablon strony HTML5</title>
</head>
<body>
  <p>ąćęłńóśźż ĄĆĘŁŃÓŚŹŻ</p>
</body>
</html>
```
Pogrubienia oraz kursywa:
* _ola_ 1 _ <br>
* __ola__ 2 _ <br>
* ___ola___ 3 _ <br>
* *ola* 1* <br>
* **ola** 2* <br>
* ***ola*** 3* <br>

---

Linki oraz zdjęcia:

* [wp] (http://www.wp.pl)

* ![Logo wp] (http://x.wpimg.pl/i/ivar/layout/201201/wp.png)

---

* Dodawanie klucza: ustawienia > ssh key > add ssh key > nazwa + klucz;
* Generowanie kluczy w linuxie: ssh-keygen > odczytywanie cat ~/.ssh/id_rsa.pub (sprawdzenie nazw plików: ls ~/.ssh/).
* Kontynuacja dodawania klucza > skopiować klucz od ssh-rsa > wkleić na stronę i potwierdzić hasłem.
* Klonowanie: git clone **adres z ssh** lub git clone i adres kogoś.

---

Podstawowe komendy:<br>
* **ls** - _wyświetla zawartość katalogu_ <br>
* **ls -l** - _wyświetla szczegółowo zawartość katalogu_<br>
* **cd** - _przemieszczanie się w strukturze katalogów_ <br>
* **nano** - _edytor tekstowy_ <br>
* **rm** - _kasowanie pliku_ <br>
* **git rm** - _kasowanie pliku w repozytorium_ <br>
* **mv** - _zmiana nazwy pliku_ <br>
* **git mv** - _zmiana nazwy pliku w repozytorium_ <br>
* **git status** - _podpowiada co się stało_ <br>
* **git checkout -- plik** - _przywraca plik_ <br>
* **git reset HEAD plik** - _przywraca plik_ <br>
* **git commit -m "..."** - _opisuje zdarzenie, później można zachować zmiany na github_ <br>
* **git push**  - _przerzuca repozytorium na githuba_ <br>
* **git pull** - _ściąga nowe rzeczy z github_

---
Edytor tekstu:
Sublime Text 2
Instalacja i uruchomianie:

* ściągnąć i rozpakować plik przy pomocy polecenia:
**tar jxvf nazwa pliku** jeżeli chcemy to można wpisać początek nazwy i wcisnąć "TAB",
* przejść do katalogu rozpakowanego (za pomocą komendy **cd**),
* zmienić atrybuty przy pomocy **chmod 755 sublime_text**,
* uruchomić program za pomocą polecenia **./sublime_text**.

***
***

    body {
     margin: 28px;  
     background: yellow;
     padding: 30px;
    }  

    html {
      background: purple;
      margin : 0; 
      padding : 0; 
    }

    p { 
      background: red;
    }

    p.warning { 
      background: green;
    }

    h3.warning { 
      background: blue;
}
  p.warning:hover {background:orange;
    }
h3 em { color: red; font-style: italic}

---

<!DOCTYPE html>
<html>
<head>
<meta charset=utf-8 />
<title>JS Bin</title>
</head>
<body>
  <p>ala ma kota</p>
  <p class="warning">basia ma psa</p>
  <h3 class="warning">Warning!
    <em>Warning!</em></h3>
</body>
</html>
