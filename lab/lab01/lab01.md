# Elementarne Typy Danych i Zmienne w Pythonie. Skrypty i parametry.

Na tym laboratorium dowiesz się, jak pracować z interpreterem języka Python oraz poznasz podstawowe typy danych. Nauczysz się też uruchamiać skrypty zapisane w plikach .py i przekazywać do nich parametry z linii poleceń. 

## Jak uruchomić interpreter Pythona w systemie Windows?

    Upewnij się, że Python jest zainstalowany – aby to sprawdzić, otwórz Wiersz Poleceń (Command Prompt):
        Naciśnij Win + R, wpisz cmd i naciśnij Enter.
        W wierszu poleceń wpisz: ```python --version``` lub ```python3 --version``` i naciśnij Enter.
        Upewnij się, że wyświetlona wersja to Python 3.x. Python 2.7 jest przestarzały i nie jest zalecany do nauki ani używania w nowych projektach.
        Jeśli masz zainstalowaną wersję 2.7 lub nie widzisz żadnej wersji, pobierz Python 3 z oficjalnej strony Python.
    Uruchom interpreter Pythona:
        W wierszu poleceń wpisz python lub python3 i naciśnij Enter.
        Powinieneś zobaczyć znak zachęty Pythona (```>>>```) oznaczający, że interpreter jest gotowy do pracy.


## Typy i zmienne

Python to język dynamicznie typowany, co oznacza, że nie musimy określać typu zmiennej w momencie jej deklaracji. Typ danych jest przypisywany automatycznie na podstawie wartości. Możemy sprawdzić typ danej zmiennej za pomocą funkcji ```type()```. Informacje na konsolę wypisujemy za pomocą funkcji ```print()```.

Zmienne mogą zmieniać typ w trakcie działania programu. W tej instrukcji poznasz różne typy danych i podstawowe operacje na zmiennych.

### Przykłady

Uruchom poniższe przykłady w interpreterze Pythona (w oknie konsoli), aby zobaczyć, jak działają różne typy danych.

### Typ całkowity (```int```) i zmiennoprzecinkowy (```float```)

```python
num_students = 24
print(num_students)
print(type(num_students))

body_temperature = 36.6
print(body_temperature)
print(type(body_temperature))
```

### Łańcuchy znaków

```python
name = "Marcin"
print(name)
print(type(name))

# Zmiana wartości zmiennej (ta linijka to komentarz, komentarze w pythonie zaczynają się od '#')
name = 'Adam'
print(name)

# Zmiana typu zmiennej
name = 5
print(name)
print(type(name))
```
### Typ logiczny (bool)

```python

a = True
b = False
print(a, type(a))
print(b, type(b))
```

### Ciągi wielowierszowe

```python

text = '''
Tutaj pokazano
wielowierszowy
sposób zapisania ciągu
znaków
'''
print(text)
```

### Nazewnictwo zmiennych

W Pythonie nazwa zmiennej nie może zaczynać się od cyfry. Przykłady poprawnych i niepoprawnych nazw:

```python
# Niepoprawne przypisanie (zaczyna się od cyfry)
2name = "Marcin"  # To spowoduje błąd!

# Poprawne przypisanie
name2 = "Marcin"
print(name2)
```

### ```None```


W języku Python istnieje specjalna wartość typu "pustego" – ```None```, która jest jedyną możliwą wartością dla typu NoneType. Odpowiada ona wartości null w innych językach programowania i często oznacza brak wartości lub niewystępowanie jakiegoś obiektu.

Typ NoneType jest szczególnie przydatny przy pracy z obiektami, ale ma też znaczenie w definiowaniu funkcji, gdy chcemy zaznaczyć, że funkcja nic nie zwraca lub że zmienna nie ma jeszcze przypisanej wartości.


```python
a = None
print(a)
print(type(a))
```

## Środowisko IDLE

IDLE (Integrated Development and Learning Environment) to podstawowe środowisko programistyczne dostarczane wraz z Pythonem. Jest to narzędzie przeznaczone dla początkujących, które umożliwia łatwe tworzenie, edytowanie i uruchamianie kodu w Pythonie. IDLE jest dobrym miejscem do nauki, ponieważ posiada:

    Podświetlanie składni, które ułatwia czytanie kodu,
    Autouzupełnianie kodu, co przyspiesza pisanie,
    Osobne okno dla interpretera Pythona, w którym można od razu testować kod.

### Jak uruchomić IDLE na systemie Windows?

    IDLE jest dołączone do instalatora Pythona, więc instalacja samego Pythona wystarczy.
    Uruchom IDLE:
        Kliknij przycisk Start i wpisz "IDLE" w pole wyszukiwania.
        Powinieneś zobaczyć skrót do IDLE (Python 3.x). Kliknij na niego, aby otworzyć środowisko.

Po otwarciu IDLE, zobaczysz okno interpretera z zachętą (```>>>```), podobnie jak w wierszu poleceń. Możesz tu wpisywać polecenia, które będą wykonywane na bieżąco, lub otworzyć nowy plik i napisać dłuższy program, korzystając z menu ```File > New File.```

Od tej pory możesz korzystać z IDLE zamiast interpretera w konsoli, co może być łatwiejsze przy większych fragmentach kodu.


## Operatory Arytmetyczne

Python obsługuje standardowe operatory arytmetyczne, które można wykorzystać do wykonywania podstawowych operacji matematycznych. Przykłady możesz uruchomić w IDLE.

### Dodawanie, Odejmowanie, Mnożenie, Dzielenie

```python
2 + 2      # Dodawanie
2 - 2      # Odejmowanie
2 * 2      # Mnożenie
2 / 3      # Dzielenie (wynik zmiennoprzecinkowy)
```


### Dzielenie z zaokrągleniem w dół do liczby całkowitej

```python
2 // 3
```

### Operator reszty z dzielenia

```python
2 % 2
```

### Potęgowanie

```python
2 ** 3
```

### Operacje na zmiennych

```python
a = 5
b = 10
print(a + b)
```

```python
a += 1  # Inkrementacja (nie istnieją znane z C/C++ operatory a++, a--!)
a -= 1  # Dekrementacja
```

Nawiasy można stosować, aby kontrolować kolejność działań. W przeciwnym razie Python stosuje kolejność matematyczną:

```python
5 * 2 + 1
5 * (2 + 1)
```

### Operatory Porównania

Operatory porównania zwracają wartości logiczne (```True``` lub ```False```). Są one przydatne do porównywania wartości:

```python
2 == 2    # Równość
2 != 3    # Nierówność
2 < 3     # Mniejsze
2 <= 2    # Mniejsze lub równe
5 > 3     # Większe
a = 5
b = 10
a < b < a # Porównania łańcuchowe
```

## Operatory Logiczne i Bitowe

W języku Python operatory logiczne są zapisywane słownie: `and`, `or`, `not` zamiast `&&`, `||`, `!`. 

### Operatory logiczne

```python
True and False
True and (2 < 3)
(2 < 3) and (5 == 7)
```

### Operatory bitowe

W Pythonie & i | działają na poziomie bitów:

```python
a = 5
b = 10
a & b   # Binarne 0101 & 1010 = 0000
a | b   # Binarne 0101 | 1010 = 1111
```
Negacja bitowa ~

```python
~a          # Zanegowanie wszystkich bitów, zmiana znaku liczby
~a & 255    # Zastosowanie maski 255 (8-bitowa maska)
```

XOR (exclusive or) ^

```python
a ^ b
```

### Operatory przesunięcia bitowego

```python
a << 1    # Przesunięcie bitów w lewo: 101 -> 1010
a << 2    # Przesunięcie bitów w lewo: 101 -> 10100
a >> 1    # Przesunięcie bitów w prawo: 101 -> 10
a >> 2    # Przesunięcie bitów w prawo: 101 -> 1
```


## Instrukcja warunkowa ```if```


Instrukcja `if` w Pythonie pozwala na wykonywanie bloków kodu w zależności od spełnienia określonych warunków. Można ją stosować samodzielnie lub w połączeniu z instrukcjami `elif` i `else`, aby kontrolować przepływ programu.

## Podstawowa Składnia

Podstawowa składnia instrukcji `if` wygląda następująco:

```python
if warunek:
    # kod do wykonania, gdy warunek jest prawdziwy
```

Python stosuje wcięcia (najczęściej 4 spacje) do oznaczenia bloków kodu wewnątrz instrukcji warunkowych.
Przykład

```python
x = 10
if x > 5:
    print("x jest większe niż 5")
```

### Instrukcje ```elif``` i ```else```

```elif``` (ang. else if) pozwala sprawdzić dodatkowy warunek, jeśli pierwszy warunek ```if``` jest fałszywy.
```else``` wykona się, gdy żaden z poprzednich warunków ```if``` lub ```elif``` nie był spełniony.


Przykład:

```python
x = 10

if x > 15:
    print("x jest większe niż 15")
elif x > 5:
    print("x jest większe niż 5, ale mniejsze lub równe 15")
else:
    print("x jest mniejsze lub równe 5")
```

## Listy w Pythonie

Listy to struktury danych, które pozwalają przechowywać wiele wartości w jednym miejscu. W Pythonie są one typem zmiennym i mogą zawierać elementy różnych typów danych.

### Tworzenie Listy

Listy są definiowane za pomocą nawiasów kwadratowych `[]`, a elementy są oddzielane przecinkami:

```python
my_list = [1, 2, 3, 4, 5]
mixed_list = [1, "Hello", 3.14, True]
nested_list = [1, 2, 3, [4, 5]] # Listy mogą też zawierać inne listy!
```

### Dostęp do Elementów Listy

Możemy uzyskać dostęp do elementów listy przy użyciu indeksów. Indeksowanie w Pythonie zaczyna się od zera.

```python
print(my_list[0])  # Pierwszy element
print(my_list[-1]) # Ostatni element
```

### Podstawowe Operacje na Listach

#### Dodawanie elementu na końcu listy: Użyj ```append()```

```python
my_list.append(6)
print(my_list)
```

#### Wstawianie elementu w konkretne miejsce: Użyj ```insert()```

```python
my_list.insert(1, "new")
print(my_list)
```

#### Usuwanie elementu z listy: Użyj ```remove()``` (usuwa pierwsze wystąpienie elementu)

```python
my_list.remove(10)
print(my_list)
```

#### Usuwanie elementu na podstawie indeksu: Użyj ```pop()```

```python
my_list.pop(1)  # Usuwa element o indeksie 1
print(my_list)
```

#### Znajdowanie indeksu elementu: Użyj ```index()```

```python
idx = my_list.index(4)
print("Index of 4:", idx)
```

#### Liczba wystąpień elementu: Użyj ```count()```

```python
occurrences = my_list.count(3)
print("Occurrences of 3:", occurrences)
```

#### Długość Listy

Aby sprawdzić długość listy, użyj funkcji ```len()```:

```python
length = len(my_list)
print("Length of list:", length)
```

#### Łączenie list: Użyj operatora ```+```

```python
list1 = [1, 2, 3]
list2 = [4, 5]
combined_list = list1 + list2
print(combined_list)
```

#### Powielanie listy: Użyj operatora *

```python
repeated_list = list1 * 3
print(repeated_list)
```

#### Sprawdzanie obecności elementu w liście: Użyj operatora in

```python
print(2 in list1)   # Zwraca True
print(7 in list1)   # Zwraca False
```

#### Wycinki List (Slicing)

Możemy wybrać część listy za pomocą wycinków (slice), w operatorze indeksowania używamy zakresu w postaci ```[start:stop]```. Należy pamiętać, że wybierane są elementy od ```start``` (włącznie z nim) do ```stop``` (bez niego).

```python
sub_list = my_list[1:4]  # Elementy od indeksu 1 do 3
print(sub_list)
```

# Uruchamianie Plików `.py` w Pythonie

Pliki `.py` to pliki tekstowe zawierające kod Pythona. Możesz tworzyć i uruchamiać pliki `.py` zarówno z wiersza poleceń, jak i w środowisku IDLE. Poniżej znajdują się instrukcje, jak to zrobić oraz ważne informacje o wyświetlaniu wyników na konsoli.

## Uruchamianie Plików `.py` z Wiersza Poleceń

1. **Otwórz Wiersz Poleceń (Command Prompt)**:
   - Na systemie Windows: Naciśnij **Win + R**, wpisz `cmd` i naciśnij **Enter**.

2. **Przejdź do katalogu zawierającego plik `.py`**:
   - Użyj komendy `cd`, aby zmienić katalog, np.:
     ```bash
     cd C:\path\to\your\script
     ```

3. **Uruchom plik `.py`**:
   - Wpisz `python filename.py` lub `python3 filename.py` i naciśnij **Enter**, aby uruchomić skrypt.
   - Przykład:
     ```bash
     python my_script.py
     ```

## Uruchamianie Plików `.py` w IDLE

1. **Otwórz IDLE**:
   - Kliknij przycisk **Start** i wyszukaj **IDLE (Python 3.x)**, a następnie kliknij, aby uruchomić.

2. **Otwórz plik `.py`**:
   - W IDLE wybierz **File > Open** i wybierz swój plik `.py`.
   
3. **Uruchom plik**:
   - W oknie edytora IDLE wybierz **Run > Run Module** lub naciśnij **F5** na klawiaturze.
   - Kod zostanie uruchomiony, a wynik wyświetlony w oknie konsoli IDLE.

## Wyświetlanie Wyników na Konsoli

W trybie interaktywnym (np. w interpreterze Pythona) pojedyncze wyrażenia, takie jak `2 + 4`, automatycznie wyświetlają wynik w konsoli. Jednak w pliku `.py` takie wyrażenia **nie wyświetlają wyniku na konsoli**, ponieważ wynik nie jest domyślnie drukowany.

Aby wyświetlić wynik, należy użyć funkcji `print()`. Przykład:

```python
# Kod w trybie interaktywnym (automatyczny wynik):
2 + 4

# Kod w pliku .py (konieczne użycie print):
print(2 + 4)
```


# Przyjmowanie Parametrów w Skryptach Pythona

Python umożliwia przekazywanie argumentów do skryptu podczas jego uruchamiania z wiersza poleceń za pomocą modułu `sys`. Parametry te mogą być wykorzystywane do dostosowywania działania skryptu.

## Przekazywanie Parametrów za Pomocą `sys.argv`

Moduł `sys` zawiera listę `argv`, która przechowuje nazwę skryptu oraz wszystkie podane argumenty. Pierwszym elementem `sys.argv` jest zawsze nazwa skryptu, a kolejne elementy to argumenty podane w wierszu poleceń.

### Przykład

Zapisz poniższy kod w pliku `.py` i uruchom go z argumentami z wiersza poleceń:

```python
import sys

# Sprawdzamy liczbę argumentów
if len(sys.argv) > 1:
    # Drukujemy argumenty
    print("Argumenty:", sys.argv[1:])
else:
    print("Brak argumentów")
```

#### Uruchamianie

Z konsoli, uruchom skrypt w następujący sposób:

```bash
python my_script.py arg1 arg2 arg3
```


## ${\color{green}{\textsf{\textbf{ZADANIA do samodzielnego wykonania:}}}}$

**1.** Zmodyfikuj przykład z parametrami i plikiem ```my_script.py``` tak, aby wypisywał też typ parametrów. Użyj funkcji ```type()```.

**2.** Napisz prosty skrypt, który przyjmuje jako parametry dwie liczby oraz znak operacji (+, -, *) i wykonuje na nich proste operacje arytmetyczne. Skrypt zapisz pod nazwą arithmetics.py. Do porównywania łańcuchów tekstowych wykorzystaj operator ==. Parametry powinny być oddzielone spacjami. Przykład działania (skrypt uruchomiony z wiersza poleceń):
```bash 
arithmetics.py 2 + 4
6
```

**3.** Napisz skrypt, który policzy ile argumentów podanych przez użytkownika (oddzielonych spacjami) ma 3 lub więcej znaków. Skrypt zapisz pod nazwą arguments.py. Przykład działania:

```bash
python arguments.py o co chodzi z tym Pythonem
```

zmodyfikuj skrypt tak, aby z listy argumentów, wybierane były argumenty o liczbie znaków 3 lub więcej, a następnie łączone w odwrotnej kolejności w napis. Uzyskany w ten sposób napis należy wyświetlić. Przykład:
```bash
python arguments.py o co chodzi z tym Pythonem
3
Pythonem tym chodzi
```


**4.** Napisz program quadratic.py do obliczania miejsc zerowych równania kwadratowego. Współczynniki (a, b, c) podawane z wiersza poleceń. Wyjście programu powinno być następujące:

    pierwsza linia wyjścia: liczba miejsc zerowych
    druga linia wyjścia: miejsca zerowe oddzielone spacją, o ile istnieją.

W przypadku braku miejsc zerowych skrypt powinien wypisać linię zawierającą liczbę 0. Przykład:

```bash
python quadratic.py 1 4 3
2
-1.0 -3.0
```

---

*autor: Marcin Mrukowicz, Michał Kępski (mkepski[at]ur.edu.pl)*
