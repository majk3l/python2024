# programowanie w języku Python
### Wykład #4: Klasy. Dekoratory, zarządzanie atrybutami, generatory. Narzędzia wbudowane - biblioteka standardowa.
*dr inż. Michał Kępski* 



---
# Iteratory

### Działanie pętli for opiera się na iteratorach

*Behind the scenes, the **for** statement calls ```iter()``` on the container object. The function returns an iterator object that defines the method ```__next__()``` which accesses elements in the container one at a time. When there are no more elements, ```__next__()``` raises a StopIteration exception which tells the for loop to terminate.*

<!-- footer: | Język skryptowy | Wykład #4: Narzędzia wbudowane, biblioteka standardowa. | dr inż. Michał Kępski | https://github.com/majk3l/JS2017/
     page_number: true -->

---
# Iteratory

```python
>>> s = 'abc'
>>> it = iter(s)
>>> it
<iterator object at 0x00A1DB50>
>>> next(it)
'a'
>>> next(it)
'b'
>>> next(it)
'c'
>>> next(it)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
    next(it)
StopIteration

```

---
# Własny iterator

### Rozważmy iterator przechodzący sekwencję od tyłu (przykład z *docs*)

```python
class Reverse:
    """Iterator for looping over a sequence backwards."""
    def __init__(self, data):
        self.data = data
        self.index = len(data)

    def __iter__(self):
        return self

    def __next__(self):
        if self.index == 0:
            raise StopIteration
        self.index = self.index - 1
        return self.data[self.index]

```

---

# Własny iterator w działaniu

### Rozważmy iterator przechodzący sekwencję od tyłu (przykład z *docs*)

```python
>>> rev = Reverse('test')
>>> iter(rev)
<__main__.Reverse object at 0x7f926001a6a0>
>>> for char in rev:
...     print(char)
...
t
s
e
t
```
---

# Generatory

- funkcja zwracająca tzw. *generator iterator*
- uzywa instrukcji ```yield``` do zwracania wartości
- przydatne do generowania ciągu wartości, które są uzywane po kolei w pętli
- w przeciwieństwie do iteratorów nie przechowują całości danych w pamięci (czasami są określane jako *lazy iterators*)

---

# ```yield```

*Each yield temporarily suspends processing, remembering the location execution state (including local variables and pending try-statements). When the generator iterator resumes, it picks up where it left off (in contrast to functions which start fresh on every invocation).*

---
# Generatory - przykład

&nbsp;
Możemy użyć generatora do uzyskania nieskończonej sekwencji liczb całkowitych:

```python
def infinite_sequence():
    num = 0
    while True:
        yield num
        num += 1
```

```python
>>> for i in infinite_sequence():
...     print(i, end=" ")
...
0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29
30 31 32 33 34 35 36 37 38 39 40 41 42
[...]
```

---
# Generatory - przykład

&nbsp;

```python
def infinite_sequence():
    num = 0
    while True:
        yield num
        num += 1
```

```python
>>> type(inf_seq)
<class 'generator'>
>>> next(inf_seq)
0
>>> next(inf_seq)
1
>>> next(inf_seq)
2
```
---
# Dekoratory

- sposób na opakowanie funkcji w dodatkową funkcjonalność
- konstrukcja możliwa do zrealizowania, bo w Pythonie funkcje są tzw. *first-class citizens* (często też nazywane *first-class-objects*)


---
# Zawieranie się funkcji

```python

def outer_function():
    msg = 'Witaj'
    def inner_function():
        print(msg)
    return inner_function

f = outer_function()
f()

```
Funkcja wewnętrzna pamięta wartość zmiennej ```msg```, więc w definicji funkcji zewnętrznej można ją użyć jako parametr.

---

# Zawieranie się funkcji

```python

def outer_function(msg):
    def inner_function():
        print(msg)
    return inner_function

f = outer_function("Witaj")
f()

```
Funkcja wewnętrzna pamięta wartość zmiennej ```msg```, więc w definicji funkcji zewnętrznej można ją użyć jako parametr.

---
# Dekorator 

```python
def decorator_function(original_function):
    def wrapper_function():
        return original_function()
    return wrapper_function

def greeter():
    print('Witaj świecie!')

decorated_greeter = decorator_function(greeter)
decorated_greeter()

```
---

# Dekorator (zapis z ```@```)

```python

def decorator_function(original_function):
    def wrapper_function():
        return original_function()
    return wrapper_function

@decorator_function
def greeter():
    print('Witaj świecie!')

```
---
# Dekorator (który faktycznie coś robi)

```python

def decorator_function(original_function):
    def wrapper_function():
        print("Coś wypisujemy na początku")
        original_function()
        print("Coś na końcu")
    return wrapper_function

@decorator_function
def greeter():
    print('Witaj świecie!')

greeter()

```

---

# Praktyczne dekoratory

```python

def my_logger(orig_func):
    import logging
    logging.basicConfig(filename='{}.log'.format(orig_func.__name__), level=logging.INFO)

    def wrapper(*args, **kwargs):
        logging.info(
            'Ran with args: {}, and kwargs: {}'.format(args, kwargs))
        return orig_func(*args, **kwargs)

    return wrapper
```

---

# Praktyczne dekoratory

```python
def my_timer(orig_func):
    import time

    def wrapper(*args, **kwargs):
        t1 = time.time()
        result = orig_func(*args, **kwargs)
        t2 = time.time() - t1
        print('{} ran in: {} sec'.format(orig_func.__name__, t2))
        return result

    return wrapper

import time
```
---
# Łączenie dekoratorów

- istnieje możliwość łączenia kilku dekoratorów dla funkcji
- ```from functools import wraps```

---

# Dekoratory używane przy tworzeniu klas 

## Metody klas:

- wiemy już, że istnieją atrybuty klas
- można też zdefiniować metodę klasy
- będą one związane z całą klasą, a nie instancją
- dekorator ```@classmethod```

---

# Metoda klasy ```@classmethod```

```python
class MyClass:
    class_variable = "Hello"

    @classmethod
    def print_class_variable(cls):
        print(cls.class_variable)

# Wywołanie metody klasy
MyClass.print_class_variable()  # Hello
```
---
# Metoda klasy ```@classmethod```

- Metody klasy mogą być wywoływane zarówno na samej klasie (np. ```C.f()```), jak i na instancji klasy (np. ```C().f()```).
- Przy wywołaniu na instancji, instancja jest ignorowana – przekazywana jest tylko jej klasa.
- Jeśli metoda klasy zostanie wywołana na klasie pochodnej, to jako pierwszy argument (```cls```) zostanie przekazana ta klasa pochodna.

---
# Metoda klasy ```@classmethod```

```python
class Base:
    @classmethod
    def identify(cls):
        print(f"Jestem klasą {cls.__name__}")

class Derived(Base):
    pass

Base.identify()        # Jestem klasą Base
Derived.identify()     # Jestem klasą Derived
```

---
# Metoda statyczna ```@staticmethod```

- Metoda statyczna to metoda, która nie ma dostępu do atrybutów ani metod instancji (```self```) ani klasy (```cls```).
- Jest przydatna, gdy metoda logicznie należy do klasy, ale nie wymaga dostępu do żadnych danych tej klasy.
- Do zdefiniowania metody statycznej używamy dekoratora ```@staticmethod```.

---

# Dekorator ```@property```

- Pozwala na traktowanie metody klasy jako atrybutu.
- Umożliwia implementację wzorca "getter" i "setter" w Pythonie.

---

```python
class Circle:
    def __init__(self, radius):
        self._radius = radius

    @property
    def radius(self):
        return self._radius

    @radius.setter
    def radius(self, value):
        if value < 0:
            raise ValueError("Radius cannot be negative")
        self._radius = value
        
    def area(self):
        from math import pi
        return pi * self._radius ** 2
```
---

# Użycie obiektu z ```@property```

```python
# Tworzenie obiektu klasy Circle
c = Circle(5)
# Odczyt promienia za pomocą getter'a
print(f"Promień: {c.radius}")       # Promień: 5
c.radius = 10
print(f"Nowy promień: {c.radius}")  # Nowy promień: 10

# Obliczanie pola
print(f"Pole: {c.area():.2f}")      # Pole: 314.16
try:
    c.radius = -3
except ValueError as e:
    print(e)                        # Promień nie może być ujemny.
```

---
# abc - Abstract Base Classes

- Abstrakcyjne klasy bazowe (ABC) definiują wspólne API dla grupy klas.
- Nie można tworzyć instancji abstrakcyjnej klasy bazowej.
- Klasy pochodne muszą implementować metody zadeklarowane jako abstrakcyjne.

---
# abc - Abstract Base Classes

```python

from abc import ABC, abstractmethod

class Animal(ABC):
    @abstractmethod
    def sound(self):
        pass
```

Klasa ```Animal``` wymaga, aby wszystkie klasy pochodne implementowały metodę ```sound()```.

---
# abc - Abstract Base Classes

```python

from abc import ABC, abstractmethod

class Animal(ABC):
    @abstractmethod
    def sound(self):
        pass


class Dog(Animal):
    def sound(self):
        return "Hau!"

dog = Dog()
print(dog.sound())  # Hau!
dog = Animal()      # Can't instantiate abstract class Animal               
                    # with abstract method sound
```
---

# Obsługa plików

Składnia:

```python
file_object = open(file_name [, access_mode][, buffering])
```

Przykład

```python
file = open('test.txt', 'w')
# wykonujemy operacje na pliku, przykładowo wypisujemy nazwę:
print(file.name)
file.close() # pamiętamy aby zamknąć plik!
```

---

# Access mode (tryby dostępu do pliku)

### Tryby dostępu do pliku (cytując z dokumentacji pythona):

- ```r```	*open for reading (default)*
- ```w```	*open for writing, truncating the file first*
- ```x```	*open for exclusive creation, failing if the file already exists*
- ```a```	*open for writing, appending to the end of the file if it exists*
- ```b```	*binary mode*
- ```t```	*text mode (default)*
- ```+``` *open for updating (reading and writing)*

*The default mode is 'r' (open for reading text, synonym of 'rt'). Modes 'w+' and 'w+b' open and truncate the file. Modes 'r+' and 'r+b' open the file with no truncation.*

---

# Używanie pliku
&nbsp;
## Pamiętamy o zamykaniu plików!
&nbsp;
Składnia:

```python
file_object.close()
```

```python
>>> file_object.close()
>>> file_object.read()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: I/O operation on closed file.
```

---
# Co się stanie jeśli pliku nie zamkniemy?

```python
files = []
for x in range(100000):
    files.append(open('test.txt', 'w'))
```

```python
OSError: [Errno 24] Too many open files: 'test.txt'
```

---

# Używanie pliku - *context managers*
&nbsp;
### Sposób na uniknięcie konieczności zamykania ręcznego:
&nbsp;


```python
with open('test.txt', 'r') as f:
    pass
# po wyjsciu z bloku plik zostanie zamkniety
print(f.closed())
>>>True
```

---
# Używanie pliku - czytanie zawartości w całości

&nbsp;

### funkcja ```read(size)```

```python
with open('workfile') as f:
    read_data = f.read()
```
&nbsp;
*When size is omitted or negative, the entire contents of the file will be read and returned; it’s your problem if the file is twice as large as your machine’s memory.* 

&uarr; cytat z dokumentacji &uarr; 

---

# Używanie pliku - czytanie pojedynczej linii

&nbsp;

```python
with open('test.txt', 'r') as f:
    line = f.readline()
    print(line)
```
&nbsp;

*```f.readline()``` reads a single line from the file; a newline character (\n) is left at the end of the string, and is only omitted on the last line of the file if the file doesn’t end in a newline*

---

# Używanie pliku - czytanie zawartości do listy 

&nbsp;

```python
with open('test.txt', 'r') as f:
    lines = f.readlines()
    print(lines)
```
---

# Używanie pliku - czytanie zawartości linia po linii

&nbsp;

```python
with open('test.txt', 'r') as f:
    for line in f:
        print(line)
```
---
# Używanie pliku

- metoda ```write()``` - zapisywanie, jako parametr obiekt, którego zawartość chcemy zapisać (binarny lub tekstowy)
- metoda ```read()``` - czytanie, opcjonalny parametr z liczbą bajtów do odczytania
- metoda ```tell()``` - zwraca aktualną pozycję w pliku
- metoda ```seek()``` - służy do poruszania się po otwartym pliku, względem początku lub aktualnej pozycji

*All streams are careful about the type of data you give to them. For example giving a ```str``` object to the ```write()``` method of a binary stream will raise a ```TypeError```. So will giving a bytes object to the ```write()``` method of a text stream.*

---

# Biblioteka standardowa - moduł ```os```

## Przykład

&nbsp;
```python
import os 

print(os.getcwd())
```
---

# Biblioteka standardowa - moduł ```os```

## Przydatne funkcje

```os.chdir(path)```  - zmiana bieżącego katalogu
```os.getcwd()``` - pobranie ścieżki bieżącego katalogu
```os.mkdir(path)``` - tworzy pojedynczy folder
```os.makedirs(name)``` - tworzy wiele zagnieżdżonych folderów na podstawie podanej ścieżki
```os.path.exists()``` - sprawdza, czy dana ścieżka istnieje

**i wiele innych**

---
# Biblioteka standardowa - moduł ```socket```

## Klient
```
# utworzenie gniazda INET
sockt = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
# połączenie z serwerem na porcie 80
sockt.connect(("www.python.org", 80))
```
---
# Biblioteka standardowa - moduł ```socket```

## Serwer
```
# utworzenie gniazda INET
servsockt = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
# dowiązanie gniazda do określonego portu
servsockt.bind((socket.gethostname(), 80))
# nasłuchiwanie przychodzących połączeń
servsockt.listen(5)
```
---

```python
         *client*                       *server*
       
                                         socket
                                           |    
                                          bind
                                           |
                                         listen
                                           |
          socket                         accept
            |                              | 
         connect - - - - - - - - - - - - ->|
            |                              |
        -->send - - - - - - - - - - - - ->recv<--
       |    |                              |     |
        --recv<- - - - - - - - - - - - -  send --
            |                              |
          close - - - - - - - - - - - - ->recv
                                           |
                                          close
```
---
# Komunikacja sieciowa

### Moduł ```socket``` zapewnia mechanizmy niskopoziomowej komunikacji.

### Inne moduły pythona do komunikacji sieciowej to np. ```http.client```

---

# ```http.client```
```python
>>> import http.client
>>> conn = http.client.HTTPSConnection("www.python.org")
>>> conn.request("GET", "/")
>>> r1 = conn.getresponse()
>>> print(r1.status, r1.reason)
200 OK
>>> data1 = r1.read()  # This will return entire content.
>>> # The following example demonstrates 
>>> # reading data in chunks.
>>> conn.request("GET", "/")
>>> r1 = conn.getresponse()
>>> while not r1.closed:
...     print(r1.read(200))  # 200 bytes
b'<!doctype html>\n<!--[if"...
```







