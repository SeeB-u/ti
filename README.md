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
* Kontynuacja dodawania klucza > skopiować klucz od ssh-rsa > paste na strone i potwierdzić hasłem.
* Klonowanie: git clone **adres z ssh** lub git clone i adres kogoś.

---

Podstawowe komendy:<br>
* ls _wyświetla pliki w katalogu_ <br>
* cd _przemieszczanie się w strukturze katalogów_ <br>
* nano _edytor tekstowy_ <br>
* rm _kasowanie pliku_ <br>
* git rm _kasowanie pliku w repozytorium_ <br>
* mv _zmiana nazwy pliku_ <br>
* git mv _zmiana nazwy pliku w repozytorium_ <br>
* git status _podpowiada co się stało_ <br>
* git checkout -- plik _przywraca plik_ <br>
* git reset HEAD plik _przywraca plik_ <br>
* git commit -m "..." _opisuje zdarzenie, później można zachować zmiany na github_ <br>
* git push  _przerzuca repozytorium na githuba_ <br>
* git pull _ściąga nowe rzyczy z github_

---
