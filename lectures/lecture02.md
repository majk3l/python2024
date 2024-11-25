
# programowanie w języku Python
### Wykład #2:  Definiowanie funkcji. Zmienna, obiekt, referencja. Przestrzenie nazw.
*dr inż. Michał Kępski* 

<!-- footer: | e-mail: mkepski@ur.edu.pl | 
-->

---
<!-- footer: | programowanie w języku Python | Wykład #1: Wprowadzenie. Typy, operatory, instrukcje. | dr inż. Michał Kępski |
     page_number: true -->

# Zmienne, obiekty i referencje

Każda przechowywana w programie dana to obiekt (ang. object). Każdy obiekt posiada:


**Tożsamość** (ang. *identity*) – unikalny identyfikator obiektu, który pozwala odróżnić go od innych w trakcie jego życia w programie,

**Typ** (ang. *type* lub *class*) – definiujący wewnętrzną reprezentację danych obiektu oraz dostępne metody,

**Wartość** (ang. *value*).

```python
a = 42
```

W wyniku powyższego przypisania powstaje obiekt typu całkowitego (ang. *integer object*) o wartości ```42```.

---


# Zmienne, obiekty i referencje

**Zmienna** (czyli nazwa) tworzona jest, kiedy kod pierwszy raz przypisuje jej wartość. Przyszłe przypisania zmieniają wartość utworzonej wcześniej zmiennej.

Zmienna nigdy nie ma dołączonych żadnych informacji o **typie**. Pojęcie to wiąże się z obiektami, a nie nazwami.

---

# Zmienne, obiekty i referencje

Kiedy zmienna pojawia się w wyrażeniu, jest zastępowana przez obiekt, do którego się odnosi.

Wszystkie zmienne muszą mieć jawnie przypisane wartości, zanim będzie można ich użyć.

---

# Zmienne, obiekty i referencje

```python
A = [1, 2, 3]
```
Efektem powyższego przypisania Pythonie jest następująca struktura w pamięci operacyjnej:

```python
      zmienna          referencja            obiekt
      (nazwa)
      _______                              ___________
     |       |             |              |           |
     |   A   | - - - - - - | - - - - - - >| [1, 2, 3] |
     |_______|             |              |___________|
     
     				# wartość licznika referencji
                                # obiektu wynosi 1  
```
---


# Zmienne, obiekty i referencje

```python
B = A
```

```python
      zmienna          referencja          obiekt
      (nazwa)
      _______                              
     |       |             |                         
     |   A   |             |             ___________
     |_______| - - - - - - | - - - - - >|           |    
      _______              |            | [1, 2, 3] |
     |       | - - - - - - | - - - - - >|___________|
     |   B   |             |
     |_______|             |          
 
     				# wartość licznika referencji
                                # obiektu wynosi 2
```
--- 

# Zmienne, obiekty i referencje


Zmienne A i B wskazują na ten sam obiekt:


```python
>>> B.append(4)
>>> B
[1, 2, 3, 4]
>>> A
[1, 2, 3, 4]
```

--- 
# Zmienne, obiekty i referencje
 
- **Zmienne** - wpisy w tabeli systemowej z miejscem na łącze do obiektów.

- **Obiekty** - fragmenty pamięci z ilością miejsca wystarczającą, by zmieścić reprezentowane wartości; ponadto posiadają:
	-   licznik referencji,
	-   pole określające ich typ.

- **Referencje** - powiązania między zmiennymi a obiektami, za którymi automatycznie podąża Python.

---


# Definiowanie funkcji


Funkcje definiuje się używając słowa ```def```:

```python
def name(arg1, arg2,... argN):
    statements
```

Przykład:

```python
def maximum(x, y):
    if x > y:
        return x
    else:
        return y
```

---

# Definiowanie funkcji - istotne informacje

- ```def``` def to kod wykonywalny - funkcja nie istnieje dopóki Python nie dotrze do jej definicji i nie wykona instrukcji ```def```,
- ```return``` przesyła wynikowy obiekt z powrotem do wywołującego,
- argumenty przekazywane są przez referencję.


---

# Definiowanie funkcji

- Zmienne w definicji funkcji, nie są połączone w żaden sposób z innymi zmiennymi o tych samych nazwach, ale użytych w innej części programu. 

- Zmienne są **lokalne** dla funkcji.

- Każda zmienna ma swój zakres, czyli blok, w którym została zadeklarowana, zaczynając od miejsca zdefiniowania jej nazwy.

---

# Zakresy nazw

### Python wyszukuje zmiennych w przestrzeni nazw (ang. *namespace*).

### Zakres (ang. *scope*) związany jest miejscem definicji i wyszukiwania zmiennej w przestrzeni nazw.

### Tworzenie zmiennych w Pythonie wiąże się z:

- przypisaniem do zmiennej wartości (konieczne przed pierwszym użyciem),
- wykorzystaniem przez Pythona miejsca przypisania do powiązania zmiennej z przestrzenią nazw.

---
# Zakresy nazw

```python
      __________________________________________________
     |                                                  |
     | ZAKRES WBUDOWANY (Python)                        |
     |  ______________________________________________  |
     | |                                              | |
     | | ZAKRES GLOBALNY                              | |   
     | |  __________________________________________  | |
     | | |                                          | | |
     | | | ZAKRESY LOKALNE FUNKCJI ZAWIERAJĄCYCH    | | |
     | | |  ______________________________________  | | |
     | | | |                                      | | | | 
     | | | | ZAKRES LOKALNY                       | | | |
     | | | |______________________________________| | | |
     | | |__________________________________________| | |
     | |______________________________________________| |
     |__________________________________________________|

```
---
# Zakresy nazw - istotne informacje

- zakres globalny rozciąga się jedynie na jeden plik,
- każde wywołanie funkcji tworzy nowy zakres lokalny,
- przprzypisane nazwy są lokalne o ile nie zostaną zadeklarowane jako globalne.

---


# ```global```


```python
globvar = 0

def set_globvar_to_one():
    global globvar    
    globvar = 1

def print_globvar():
    print(globvar)    

set_globvar_to_one()
print_globvar()     
```

---

# Przykłady

```python
X = 99 

def func(Y): 
Z = X + Y 
return Z

func(1)
```
---

# Przykłady

### Wcięcia! Kod z poprzedniegu slajdu nie wykona się poprawnie!

```python
X = 99 

def func(Y): 
    Z = X + Y 
    return Z

func(1)
```
---

# Przykłady

```python
X = 99 # przypisane w module - zatem globalne

def func(Y): 
    Z = X + Y 
    return Z

func(1) # func w module: wynik = 100
```

---

# Przykłady


```python
X = 99 # Zmienna z zakresu globalnego — nieużywana

def f1():
    X = 88 # Zmienna lokalna z zakresu zawierającego
    def f2():
        print(X) # Referencja w zagnieżdżonej instrukcji def
    f2()

f1()
```

---

# Przykłady


```python
X = 99 # Zmienna z zakresu globalnego — nieużywana

def f1():
    X = 88 # Zmienna lokalna z zakresu zawierającego
    def f2():
        print(X) # Referencja w zagnieżdżonej instrukcji def
    f2()

f1() # wypisuje 88
```

---

# Argumenty nazwane (*keyword arguments*)

Argumenty nazwane pozwalają na przekazywanie wartości do funkcji przez podanie ich nazw.
W odróżnieniu od argumentów pozycyjnych, kolejność argumentów nazwanych nie jest istotna, co zwiększa czytelność kodu.

```python

def introduce(name, age):
    print(f"Nazywam się {name} i mam {age} lat.")

# Użycie argumentów nazwanych:
introduce(age=25, name="Anna")
```
---

# Argumenty nazwane i wartości domyślne

Możemy ustawić wartości domyślne dla argumentów funkcji. Gdy argument nie zostanie przekazany, funkcja użyje wartości domyślnej.
Argumenty z wartościami domyślnymi muszą być deklarowane na końcu listy argumentów.

```python

def greet(name, message="Witaj!"):
    print(f"{message}, {name}")

greet("Anna")             # Witaj, Anna
greet("Piotr", message="Hej")  # Hej, Piotr
```

---

# Mieszanie argumentów pozycyjnych i nazwanych

Można mieszać argumenty pozycyjne i nazwane, ale argumenty pozycyjne muszą być zawsze podane przed nazwanymi.


```python

def order(pizza, drink="cola"):
    print(f"Zamówienie: {pizza} z {drink}")

order("margherita")          # Zamówienie: margherita z cola
order("pepperoni", drink="sok")  # Zamówienie: pepperoni z sok
```

---

# Argumenty o zmiennej liczbie nazwanych argumentów

Używając ```**kwargs```, możemy przekazać dowolną liczbę nazwanych argumentów, które zostaną zebrane jako słownik.


```python

def describe_pet(name, **attributes):
    print(f"Zwierzę: {name}")
    for key, value in attributes.items():
        print(f"{key}: {value}")

describe_pet("Largo", typ="pies", wiek=7, rasa="owczarek szetlandzki")
```

---

# Funkcje wbudowane

---

# Funkcje wbudowane: ```type()``` i ```isinstance()```


Funkcja ```type()``` zwraca typ obiektu. Używana do sprawdzenia, jakiego typu jest dany obiekt lub do dynamicznego tworzenia nowych typów (klas).

```python
x = 42
print(type(x))   # <class 'int'>
```

Funkcja ```isinstance()``` sprawdza, czy obiekt jest instancją określonego typu lub jego pochodnej. Przyjmuje dwa argumenty: obiekt i typ (lub krotkę typów), i zwraca wartość ```True``` lub ```False```.

Przykład:

```python
x = 42
print(isinstance(x, int))            # True
print(isinstance(x, (float, str)))   # False
```

---

# Funkcje wbudowane: min() i max()


Funkcja ```min()``` zwraca najmniejszy element sekwencji lub z kilku podanych wartości.
Przydaje się do szybkiego znajdowania minimalnej wartości w listach, krotkach i innych iterowalnych obiektach.

```python
numbers = [3, 7, 2, 8, 4]
print(min(numbers))    # 2
print(min(5, 12, 7))   # 5
```

Funkcja ```max()``` działa analogicznie do ```min()```,
zwracając największy element sekwencji lub z kilku podanych wartości.

```python
numbers = [3, 7, 2, 8, 4]
print(max(numbers))    # 8
print(max(5, 12, 7))   # 12
```
---

# Funkcja wbudowana: ```sum()```

Funkcja ```sum()``` oblicza sumę elementów w sekwencji, takiej jak lista czy krotka.
Można opcjonalnie podać wartość początkową, która zostanie dodana do wyniku sumy.

Przykład:

```python
numbers = [3, 7, 2, 8, 4]
print(sum(numbers))           # 24
print(sum(numbers, 10))       # 34 (suma + wartość początkowa)
```

---

# Funkcja wbudowana: ```sum()```


Uwagi:

 - ```sum()``` działa tylko na sekwencjach liczbowych lub elementach konwertowalnych do liczb.
 - W niektórych przypadkach istnieją lepsze alternatywy dla ```sum()```:
    - Do łączenia sekwencji łańcuchów znaków preferowaną i szybszą metodą jest ```''.join(sequence)```.
    - Do dodawania wartości zmiennoprzecinkowych z rozszerzoną precyzją, zobacz ```math.fsum()```.
    - Do łączenia wielu iterowalnych obiektów warto rozważyć ```itertools.chain()```.

---

# ```''.join()```

```''.join()``` to preferowany, szybki sposób na łączenie elementów sekwencji łańcuchów znaków w jeden tekst.

Przykład:

```python
words = ["Python", "is", "awesome"]
result = ' '.join(words)
print(result)  # Python is awesome
```

---

# math.fsum()

```math.fsum()``` sumuje wartości zmiennoprzecinkowe z rozszerzoną precyzją, co jest korzystne przy operacjach na liczbach zmiennoprzecinkowych.

Przykład:

```python
import math

values = [0.1, 0.1, 0.1, 0.1, 0.1, 0.1, 0.1, 0.1, 0.1, 0.1]
result = math.fsum(values)
print(result)  # 1.0

result = sum(values)
print(result)  # 0.9999999999999999
```
---

# Funkcja wbudowana: ```enumerate()```

```enumerate()``` dodaje indeks do każdego elementu iterowalnego obiektu (np. listy, krotki, łańcucha tekstowego).
Zwraca obiekt ```enumerate```, który można przekształcić w listę lub wykorzystać bezpośrednio w pętli.


```python
colors = ["czerwony", "zielony", "niebieski"]
for index, color in enumerate(colors):
    print(index, color)
```

```enumerate()``` przyjmuje opcjonalny argument ```start```, który określa, od jakiego indeksu rozpocząć numerowanie.

---

# Funkcje wbudowane: ```all()``` i ```any()```


### ```all()```

Funkcja ```all()``` zwraca ```True```, jeśli wszystkie elementy iterowalnego obiektu (np. lista) są prawdziwe.
Jeśli którykolwiek element jest fałszywy (```False```, ```0```, ```None```, pusty string, itp.), zwraca ```False```.


```python
numbers = [1, 2, 3, 4]
print(all(numbers))     # True

mixed = [1, 0, 3, 4]
print(all(mixed))       # False
```

---

# Funkcje wbudowane: ```all()``` i ```any()```


### ```any()```

Funkcja ```any()``` zwraca ```True```, jeśli przynajmniej jeden element iterowalnego obiektu jest prawdziwy.
Jeśli wszystkie elementy są fałszywe, zwraca ```False```.


```python
empty = [0, None, False]
print(any(empty))       # False

mixed = [0, None, 3]
print(any(mixed))       # True
```

---

# Funkcja wbudowana: ```zip()```

```zip()``` łączy elementy z dwóch lub więcej sekwencji, tworząc iterowalny obiekt, w którym każdy element jest krotką z elementami pochodzącymi z podanych sekwencji.
Zatrzymuje się, gdy najkrótsza sekwencja zostanie wyczerpana.


```python
names = ["Anna", "Piotr", "Kasia"]
ages = [28, 34, 22]
combined = zip(names, ages)

print(list(combined))
```

Funkcja ```zip()``` zwraca obiekt ```zip```, który można przekształcić w listę, krotkę lub wykorzystać bezpośrednio w pętli.

---

# Wprowadzenie do adnotacji typów (type annotations)

Adnotacje typów w Pythonie umożliwiają wskazanie oczekiwanych typów argumentów funkcji oraz wartości zwracanych.
Ułatwiają czytelność kodu i pomagają w wykrywaniu błędów przy użyciu narzędzi typu mypy.
Adnotacje są opcjonalne i nie wpływają na działanie kodu.


```python
def greet(name: str) -> str:
    return f"Witaj, {name}"
```
Powyżej wskazano, że argument name powinien być łańcuchem znaków (```str```), a funkcja zwraca wartość typu ```str```.

--- 

# Typy złożone i z ```Optional```

Python umożliwia adnotowanie bardziej złożonych typów za pomocą modułu typing.
Przykłady typów złożonych:
- ```List[int]``` – lista liczb całkowitych
- ```Dict[str, int]``` – słownik, gdzie klucze są typu ```str```, a wartości typu ```int```

Typ Optional oznacza, że argument może mieć wartość None.

---
# Typy złożone i z ```Optional```

```python
from typing import List, Optional

def process(numbers: List[int], factor: Optional[int] = None) -> List[int]:
    if factor:
        return [n * factor for n in numbers]
    return numbers
```

---

# Korzyści z adnotacji typów

- Lepsza czytelność: ułatwia zrozumienie, jakie typy wartości oczekiwane są przez funkcję i jakie zwraca.
- Narzędzia do sprawdzania typów: adnotacje typów mogą być używane przez narzędzia statyczne, np. mypy, do sprawdzania zgodności typów bez uruchamiania kodu.
- Współpraca z IDE: adnotacje typów umożliwiają podpowiedzi i wykrywanie błędów typów w edytorach takich jak PyCharm czy VS Code.
