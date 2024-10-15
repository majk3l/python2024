
# programowanie w języku Python
### Wykład #1: Wstęp do języka Python.
*dr inż. Michał Kępski* 

<!-- footer: | e-mail: mkepski@ur.edu.pl | 
-->

---
<!-- footer: | programowanie w języku Python | Wykład #1: Wprowadzenie. Typy, operatory, instrukcje. | dr inż. Michał Kępski |
     page_number: true -->

# programowanie w języku Python

- Wykład
  - liczba godzin: 15 (tylko semestr 3.) 
  - zaliczenie: test (&#x2265; 50%)
- Laboratorium
  - liczba godzin: 15 (semestr 3.) + 30 (semestr 4.)
  - kolokwium (semestr 3.) + ocena projektu (semestr 4.)

Na koniec przedmiotu: egzamin pisemny z dwóch semestrów.

---

# Literatura

1. *Python 3 : kompletne wprowadzenie do programowania*, Mark Summerfield, Wyd. 2., Helion, 2010.

2. *Dokumentacja języka Python:* https://docs.python.org/3/

3. *Python. Wprowadzenie. Wydanie V*, Mark Lutz, Helion, 2020.

4. Slajdy z wykładu: https://github.com/majk3l/python2024 *(katalog lectures)*

---

# Zagadnienia

1.  **Wstęp do języka Python. Interpreter języka Python. Składnia języka. Typy i operatory. Instrukcje sterujące.**.
2. Definiowanie funkcji. Zmienna, obiekt, referencja. Przestrzenie nazw.
3.	Moduły i pakiety. Obsługa wyjątków, asercje. Logowanie.
4.	Klasy, obiekty, programowanie obiektowe.
5.	Środowisko programisty. Zarządzanie pakietami i ścieżka wyszukiwania modułów. Wirtualne środowiska. Narzędzia do zarządzania instalacjami: conda, pip.
6.	Narzędzia wbudowane – biblioteka standardowa języka Python. Typowe zadania: manipulacja plikami, katalogami, wczytywanie danych. Prosta komunikacja sieciowa. Działania w internecie. Biblioteka Numpy. Biblioteka Scipy.
7.  Zagadnienia zaawansowane. Dekoratory, zarządzanie atrybutami, generatory. Wyrażenia regularne.

---

#  Python

### Jest językiem:

- skryptowym
- obiektowym
- interpretowanym
- typowanym dynamicznie

---
# PVM (maszyna wirtualna)

&nbsp;
    


```text
       plik                   kod                 
     źródłowy               bajtowy               wykonanie 
    __________            ___________            ___________
   |          |          |           |          |           |
-> |   m.py   |    ->    |   m.pyc   |    ->    |    PVM    |
   |__________|          |___________|          |___________|
```

---

# Alternatywne implementacje

- CPython - standardowa implementacja, napisana w języku C.

- Jython - implementacja dla języka Java, kod źródłowy tłumaczony jest do kodu bajtowego JVM.

- IronPython - implementacja dla platformy .NET.

- PyPy - alternatywna implementacja Python, która kładzie nacisk na wydajność. Używa techniki Just-In-Time (JIT), co sprawia, że wiele programów działa szybciej niż w CPython. 

---

# Co mogę zrobić za pomocą Pythona?

## *Przegląd potencjalnych zastosowań i bibliotek*

---

# Programowanie systemowe

Tworzenie przenośnych i łatwych w utrzymaniu narzędzi służących do administrowania systemami i automatyzacji zadań. Przykłady:

- Przeszukiwanie plików i drzew katalogów za pomocą biblioteki `os` oraz `shutil`.
- Uruchamianie innych programów i zarządzanie procesami z wykorzystaniem `subprocess`.
- Równoległe przetwarzanie danych i wielowątkowość za pomocą `multiprocessing` i `threading`.
  
---

# Programowanie systemowe

## *Po co używać Pythona skoro jest Bash?*

---

# Bash vs Python 
### Porównanie pod kątem programowania narzędzi powłoki

**Bash**
&nbsp;

\+ wszechobecny  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; \+ łatwe łączenie komend, np: 

```bash
ls -l|tail -n +2|sed 's/\s\s*/ /g'|cut -d ' ' -f 3|sort|uniq
```

\- nieintuicyjna składnia, duże skrypty często nieczytelne &nbsp;&nbsp;&nbsp;
\- brak natywnego wsparcia dla zaaw. funkcji (np. parsowanie XML)

**Python**
&nbsp;

\+ łatwe tworzenie i utrzymanie kodu &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  \+ OOP
\- wymaga instalacji, czasami dodatkowych pakietów, etc.

---


# Skrypty internetowe

Biblioteka standardowa Pythona zawiera moduły pozwalające na wykonywanie różnych zadań sieciowych zarówno w trybie klienta, jak i serwera.

- Komunikacja za pomocą gniazd (moduł `socket`)
- Pobieranie stron internetowych za pomocą URL (`urllib`, `requests`)
- Parsowanie i generowanie XML, HTML (`xml.etree.ElementTree`, `html.parser`, `BeautifulSoup`)
- Obsługa protokołu FTP (`ftplib`)

---

# Obsługa baz danych

- Python obsługuje interfejsy do najpopularniejszych relacyjnych baz danych (`MySQLdb`, `psycopg2`, `sqlite3`)
- Moduł do serializacji i deserializacji obiektów (`pickle`)
- Wbudowany silnik bazy danych SQL (SQLite) jest standardową częścią języka (od wersji 2.5).
- `SQLAlchemy` - narzędzie ORM do zarządzania bazami danych i wykonywania złożonych zapytań SQL.

---

# Obliczenia numeryczne i programowanie naukowe

- `numpy` - szybkie obliczenia na macierzach
- `scipy` - obliczenia numeryczne i naukowe
- `pandas` - analityka i przetwarzanie danych
- `scikit-learn` - uczenie maszynowe
- `OpenCV` - biblioteka do przetwarzania obrazu i video
- `matplotlib` - tworzenie wykresów i wizualizacja danych

---
# Gry komputerowe & grafika 

- Programowanie gier oraz multimediów dzięki systemowi ```pygame```.
- Komunikacja przez port szeregowy w systemach Windows, Linux i innych dzięki rozszerzeniu ```PySerial```.
- Przetwarzanie grafiki wykonywane za pomocą ```PyOpenGL```.
-  Blender (program do modelowania) jest częściowo napisany w Pythonie, umożliwia rozszerzenia za pomocą skrytpów.

---

# GUI

- `TkInter` - wbudowany w Pythona, łatwy w użyciu
- `PySide` oraz `PyQt` - frameworki do budowy zaawansowanych GUI
- `Kivy` - framework do tworzenia aplikacji mobilnych i wieloplatformowych
- `wxPython` - framework do GUI kompatybilny z wieloma platformami

---

# Backend serwisów internetowych

- `Django` - wolny i otwarty framework do tworzenia aplikacji webowych, realizujący wzorzec architektoniczny model-template-view.
  - Wykorzystany przez Pinterest, Instagram, Fundację Mozilla, Public Broadcasting Service i The Washington Times.
- `Flask` - lekki framework do tworzenia aplikacji webowych, popularny do prototypowania i mniejszych projektów.
- `FastAPI` - nowoczesny, szybki framework przeznaczony do budowy API i mikroserwisów.
  
<sub><sup>źródło: https://pl.wikipedia.org/wiki/Django_(framework)</sup></sub>

---

# Czy python przyda się podczas zajęć na UR?

- Aplikacje internetowe 
- Analiza i przetwarzanie obrazów
- Percepcja i uczenie maszynowe

i wiele innych.

---

# Wykonywanie programów

## - Interaktywny wiersz poleceń
## - Systemowy wiersz poleceń
## - IDE (np. *IDLE* czy *PyCharm*)

---

# Interaktywny wiersz poleceń
  
```shell
$ % python
Python 3.8.5 (default, Sep  4 2020, 02:22:02) 
[Clang 10.0.0 ] :: Anaconda, Inc. on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>>
```
---

# Systemowy wiersz poleceń

Skrypt o nazwie hello.py:
```python
print("Hello world!")
```
uruchamiamy w konsoli systemowej:

```shell
$ python hello.py
Hello world!
```

---

# ```import```

Kod źródłowy Pythona pogrupowany jest w moduły i pakiety (więcej o modułach na kolejnych wykładach). Słowo kluczowe ```import``` pozwoli na załadowanie elementów z modułu:

```python
import module_name
from module_name import element_name
from module_name import *
```
```python
from decimal import Decimal
from fractions import Fraction
```
---

# Typy danych

         
- Liczby
``` python
10, 3.1415, 1+3j, Decimal, Fraction 
```   
- Łańcuchy znaków 
 ```python 
 'Hello world' 
 ``` 
- Listy 
``` python
[1, [2, 'trzy'], 4]
```
- Słowniki 
``` python
{'imie': 'Jan', 'nazwisko': 'Kowalski'}
```

---

# Typy danych

- Krotki
 ```python
 (1,'A', 2, 'B')
 ```
- Pliki 
 ```python
 myfile = open('dane.csv', 'r')
 ```
- Zbiory  
 ```python
 {'a', 'b', 'c'}
 ```
- Inne typy podstawowe (Boolean, None)

---

# Liczby

- całkowite 
- zmiennoprzecinkowe
- *zespolone*
- *Decimal* (ułamki dziesiętne)
- *Fraction* (ułamki zwykłe)

---


# Operatory arytmetyczne

operator| znaczenie
---|---
x + y |suma x oraz y
x - y |różnica x oraz y
x * y |iloczyn x oraz y
x / y |iloraz x oraz y
x // y |(zaokrąglony w dół) iloraz x oraz y
x % y |reszta z dzielenia x / y
-x |-x
+x |x
abs(x) | wartość bezwzględna x

---

# Operatory arytmetyczne

operator| znaczenie
---|---
int(x)  |x zamienione na typ całkowity
float(x)|x zamienione na typ zmiennoprzecinkowy
complex(re,im)| liczba zespolona z częścią rzeczywistą re, urojoną im.
divmod(x, y) | para (x // y, x % y)
pow(x, y) | x do potęgi y
x ** y |x do potęgi y

---

# Łańcuchy tekstowe

W Pythonie napisy zamykane są poprzez pojedynczy, podwójny lub potrójny cudzysłów:

```python
A = """Witaj świecie!"""
B = "Witaj ponownie"
C = 'Witaj ponownie'
# D = 'Witaj' 
```

Do wypisywania służy polecenie ```print```

```python
print("Witaj świecie!")
```
---

# Operator indeksowania

```python
A = "Witaj w świecie Pythona!"
i = 0
j = 5
print(A[0]) #1
print(A[i:j]) #2
```

Wyjście:

 ```W```
 
 ```Witaj```

Uwagi:
- Indeksowanie rozpoczynamy od 0
- ```A[i:j]``` oznacza: zwróć wszystko z ```A``` od przesunięcia ```i``` aż do przesunięcia ```j```, ale bez elementu ```A[j]```. 

---
# Operator indeksowania

Dopuszczalnymi indeksami są też ujemne liczby całkowite:
```python
print (A[-1])  # pierwszy element od konca
print (A[-2])  # drugi element od końca
print (a[-5:]) # pięć ostatnich elementów
```
&nbsp;
Zapis  postaci ```A[-1]``` jest równoważny ```A[len(A)-1]```, gdzie ```len(A)``` jest funkcją zwracającą liczbę elementów w ```A```. 

---
# Łańcuchy tekstowe

```python
>>> S = "To jest napis"
>>> S[0]
'T'
>>> S[0] = 't'

# jaki będzie efekt działania ostatniej instrukcji?

```
---
# Łańcuchy tekstowe

```python
>>> S = "To jest napis"
>>> S[0]
'T'
>>> S[0] = 't'
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'str' object does not support item assignment
```
---
# Łańcuchy tekstowe

```python
>>> S = "To jest napis"
>>> S[0] = 't'
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'str' object does not support item assignment
```

**UWAGA**: Łańcuchy tekstowe są niemodyfikowalne (ang. *immutable*). Można jednak używać istniejących łańcuchów do tworzenia nowych:

```python
>>> S = "To jest napis"
>>> S = 't' + S[1:] # + jest operatorem łączenia
>>> print(S)
to jest napis
```
---

# Listy



- Kontenery ogólnego przeznaczenia, uporządkowane pod względem pozycji.
- Przechowują dowolny typ obiektów, także inne listy.
- Obiekty w zakresie jednej listy mogą być różnego typu.
- Są modyfikowalne (ang. *mutable*).


---
# Listy

Definicja listy:

```python
A = [1, 2, 'trzy', 4, 3.1415] # używamy nawiasów kwadratowych
```

Lista jest indeksowana podobnie jak łańcuch tekstowy:

```python
A[0]  # początkowy element, o indeksie 0
A[-1] # element ostatni
```
Podobnie jak w przypadku łańcuchów tekstowych, możemy użyć ```:``` w operatorze indeksowania. 


---
# Listy

Zagnieżdżanie - dowolna kombinacja i głębokość:

```python
A = [1, 2, ['jeden', 'dwa'], [['x', 'y'], 'z'], 3.1415] 
```
Funkcja ```len()``` zwraca długość listy:
```python
>>> len(A)
5
```

--- 

# Krotki (ang. *tuple*)

Od list różnią się tym, że są niemodyfikowalne (podobnie jak łańcuchy tekstowe).

Definicja krotki:
```python
T = (1, 2, 'x', 4)
```

Podobnie jak w przypadku łańcuchów tekstowych i list mamy do dyspozycji operator konkatenacji:

```python
>>> T2 = T + (5, 6)
>>> print(T2)
(1, 2, 'x', 4, 5, 6)
```
---

# Instrukcja warunkowa ```if```


Test wyrażenia logicznego ```if```, następnie opcjonalne sekcje ```elif``` (*else if*) oraz opcjonalna sekcja ```else```:

```python
if testA: # test logiczny
    instrukcjaA1             # B  K	  
    ...                      # L  O
    ...                      # O  D
    instrukcjaAn             # K  U
elif testB: # test opcjonalny
    instrukcjaB1             # B  K  
    ...                      # L  O
    ...                      # O  D
    instrukcjaBn             # K  U
else: # opcjonalny blok else
    instrukcjaC
```
Bloki kodu w Javie czy C++ definiowane w nawiasach klamrowych w Pythonie określane są wcięciami!

---

# Instrukcja warunkowa ```if```

**Java:**

```C 
if (x > y) {
    x = 1;
    y = 2;
}
```

**Python**:

```Python
if x > y:
    x = 1
    y = 2
```
- wiersz nagłówka zakończony dwukropkiem,
- koniec wiersza jest końcem instrukcji (```;``` jest niepotrzebny),
- koniec wcięcia to koniec bloku.

---

# Instrukcja warunkowa ```if```

```Python
x = -10
y = 5
if x > y:
    x = 1
    y = 2
```
x = ? 
y = ?

---

# Instrukcja warunkowa ```if```

```Python
x = -10
y = 5
if x > y:
    x = 1
    y = 2
```
x = -10
y = 5

---

# Instrukcja warunkowa ```if```

```Python
x = -10
y = 5
if x > y:
    x = 1
y = 2
```
x = ? 
y = ?

---

# Instrukcja warunkowa ```if```

```Python
x = -10
y = 5
if x > y:
    x = 1
y = 2 # ta instrukcja nie należy już do bloku if!
```
x = -10 
**y = 2**

---

# Instrukcja pętli ```while```

Instrukcja ```while``` powtarza wykonanie bloku (uwzględniającego odpowiednie wcięcia) dopóki wynik testu logicznego jest prawdziwy:

```python
while test: # test logiczny
    instrukcje  # ciało pętli
else: # opcjonalny blok else wykonywany
    instrukcje # gdy pętla zakończyła się bez wywołania break
```

- ```break```- przerywa wykonanie pętli i powoduje ominięcie instrukcji w bloku else (jeśli taki istnieje),
- ```continue``` - przejście do następnej iteracji najściślej otaczającej ją pętli.

---

# Instrukcja pętli ```while```

Co jest wyjściem poniższego skryptu?

```Python
num = 10
while num > 3:
    num = num - 1
print(num)
```
---

# Instrukcja pętli ```while```

Co jest wyjściem poniższego skryptu?

```Python
num = 10
while num > 3:
    num = num - 1
print(num)
```
Rezultat:
```
> python loop.py
3
```
---

# Instrukcja pętli ```for```

Uniwersalny iterator po sekwencjach:

```python
for item in sequence: # 
    instrukcje  # tu zazwyczaj używany jest item
else: # opcjonalny blok else
    instrukcje 
``` 

---
<!-- footer: | Język skryptowy | Wykład #2: Funkcje, zakresy nazw. | dr inż. Michał Kępski | https://github.com/majk3l/JS2017/
     page_number: true -->

# Więcej o typach danych

## Metody listy:

- ``` s.append(x) ``` - dodaje nowy element ```x``` na końcu ```s```
- ``` s.extend(t) ``` - dodaje nową listę ```t``` na końcu ```s```
- ``` s.count(x) ``` - zlicza wystąpienie ```x``` w ```s```
- ``` s.index(x) ``` - zwraca najmniejszy indeks ```i```, gdzie ```s[i] == x```
- ``` s.pop([i]) ``` - zwraca ```i```-ty element i usuwa go z listy. Jeżeli nie podamy parametru to usunięty zostanie ostatni element
- ``` s.remove(x) ``` - odnajduje ```x``` i usuwa go z listy ```s```
- ``` s.reverse() ``` - odwraca w miejscu kolejność elementów ```s```
- ```s.sort([f]) ``` - sortuje elementy, ```f``` to funkcja porównawcza

---

# Konwersja niektórych typów danych

- Pyton dostarcza gotowe mechanizmy konwersji typów sekwencyjnych.

- Obiekt musi być iterowalny, tzn. posiadać metody ```__iter__()``` lub ```__getitem__()```.

- Konwersja:

```python
>>> t = (1,2,3)        # krotka 
>>> list(t)
[1, 2, 3]              # lista na podstawie krotki
>>> set(t)
{1, 2, 3}              # zbior na podstawie krotki
>>> tuple([1, 2, 3])   
(1, 2, 3)	       # krotka na podstawie listy

```

---

#  ```range```


Klasa ```range``` reprezentuje niemodyfikowalną sekwencję liczb w pewnym zakresie. Zazwyczaj używana w instrukcji pętli ```for```.


*class* **range**(*stop*)
*class* **range**(*start, stop*[, *step*])


Elementy sekwencji ``` r ``` typu **range** określone są następująco:

&nbsp; ``` r[i] = start + step * i ```

Parametr ``` step``` może być dodatni lub ujemny:			
 
- jeśli ```step > 0``` to: ```i >= 0 oraz r[i] < stop```

- jeśli ```step < 0``` to: ```i >= 0 oraz r[i] > stop```

---

# *List Comprehensions*

### to:

- zwięzłe mechanizmy definiowania listy,
- przydatne gdy nowa lista jest wynikiem pewnych operacji na elementach listy istniejącej.



---

# *List Comprehensions*


```python
squares = []
for x in range(10):	   # tworzymy listę wykorzystując
    squares.append(x**2)   # pętlę for
```
po wykonaniu kodu otrzymamy listę:

```python
>>> squares
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```
powyższą listę można zdefiniować w sposób bardziej zwięzły:

```python
squares = [x**2 for x in range(10)] # list comprehension
```

---

# *List Comprehensions*

Składnia dopuszcza opcjonalną instrukcję warunkową:

```python
>>> squares = [x**2 for x in range(10) if x % 2 == 0]
>>> squares
[0, 4, 16, 36, 64]
```

oraz możliwość zagnieżdżania:

```python
>>> matrix = [
...     [1, 2, 3],
...     [4, 5, 6],
...     [7, 8, 9]
... ]
>>> matrix_T = [[row[i] for row in matrix] for i in range(3)]
>>> matrix_T
[[1, 4, 7], [2, 5, 8], [3, 6, 9]]
```
---

# Słowniki

```python 
d = {'name':'Jack', 'age': 26}
```

Dostęp do elementów poprzez operator indeksowania ``` [] ```, w którym podajemy wartość klucza:

``` python 
>>> d['name']
'Jack'

>>> d['city'] = 'London'
>>> d
{'city': 'London', 'name':'Jack', 'age': 26}

```
---

# Słowniki

Usuwanie elementów ze słownika:
```
>>> del d['city']
>>> d
{'name':'Jack', 'age': 26}
```
### Słowniki mogą być zagnieżdżane:

```python
rec = {'dane osobowe': {'imię': 'Ireneusz', 'nazwisko': 
'Zielony'}, 'zawód': ['konstruktor', 'inżynier'],
'wiek': 28}
```

Dostęp do zagnieżdżonych elementów:
```python
>>> rec['dane osobowe']['nazwisko']
'Zielony'
```
---

# Słowniki
```python
rec['zawód'].append('mechanik') # Rozszerzenie listy
>>> rec
{'wiek': 28, 'zawód': ['konstruktor', 'inżynier', 
'mechanik'], 'dane osobowe': {'nazwisko': 'Zielony', 
'imię': 'Ireneusz'}}
```

lista kluczy:

```python 
>>> rec.keys()
dict_keys(['dane osobowe', 'wiek', 'zawód'])
```
---
