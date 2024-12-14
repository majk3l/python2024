
# programowanie w języku Python
### Wykład #5: Wirtualne środowiska. NumPy, SciPy.
*dr inż. Michał Kępski* 

---

# Wirtualne środowiska

Wirtualne środowiska w Pythonie to odizolowane środowiska instalacyjne, które umożliwiają niezależne zarządzanie bibliotekami i zależnościami dla różnych projektów

---

# Wirtualne środowiska - motywacja

W przypadkach gdy:

- potrzebujemy używać różnych wersji tych samych pakietów, lub gdy pakiety mają różne zależności,
- *legacy code*
- ułatwienie reprodukcji środowiska dla innych programistów.

---

# Co mamy do wyboru?

### conda

### venv (wbudowane w Pythona od wersji 3.3)

### virtualenv

---

# Tworzenie i używanie wirtualnego środowiska

```bash
python -m venv nazwasrodowiska
```
- ```-m venv```: moduł do tworzenia środowisk.
- ```nazwasrodowiska```: nazwa katalogu, w którym znajdzie się środowisko.

### Aktywacja środowiska:

- Windows: ```nazwasrodowiska\Scripts\activate```
- Mac/Linux: ```source nazwasrodowiska/bin/activate```

### Dezaktywacja środowiska:

 - ```deactivate```

---

# pip

pip to menedżer pakietów dla Pythona, umożliwiający instalowanie i zarządzanie bibliotekami dostępnymi w *Python Package Index* (PyPI).

---

# pip

```bash
pip install nazwapakietu

pip install nazwapakietu==1.2.3

pip uninstall nazwapakietu
```
---

# pip - *requirements files*

```bash
# eksportowanie zależności do pliku
pip freeze > requirements.txt
# instalowanie listy bibliotek z pliku
pip install -r requirements.txt
# lista zainstalowanych bibliotek
pip list
```

---

# conda

To menedżer pakietów i środowisk, który pozwala instalować i zarządzać bibliotekami oraz zależnościami w różnych językach, w tym Pythonie

### Czym conda jest a czym nie?

- nie jest dystrybucją pythona
- nie jest tylko i wyłącznie managerem pakietów (jak pip)
- zawiera własny menadżer środowisk wirtualnych 

---

# conda - instalacja

```bash
# silent mode installation
wget https://repo.continuum.io/miniconda/Miniconda3-3.7.0-Linux-x86_64.sh -O ~/miniconda.sh
bash ~/miniconda.sh -b -p $HOME/miniconda
export PATH="$HOME/miniconda/bin:$PATH"
```

---

# conda - podstawowe polecenia

```bash
# tworzenie środowiska z interpreterem w wersji 3.10
conda create --name nazwasrodowiska python=3.10
# usuwanie istniejacego srodowiska
conda remove --name nazwasrodowiska --all
# wypisanie listy istniejących środowisk
conda env list
```

---

# conda - podstawowe polecenia

```bash
# aktywacja wybranego środowiska
conda activate nazwasrodowiska
# wypisanie zainstalowanych pakietów
conda list
# instalacja pakietu (-c wskazuje kanał)
conda install -c conda-forge nazwapakietu
# instalacja konkretnej wersji pakietu
conda install nazwapakietu=1.2.3
# usuniecie pakietu
conda remove nazwapakietu
# deaktywacja środowiska
conda deactivate
```

---

# wirtualne środowiska - dobre praktyki

Dobre praktyki:

- Zawsze używaj wirtualnych środowisk dla każdego projektu.
- Aktualizuj i sprawdzaj requirements.txt w miarę zmian w projekcie.
- W przypadku pracy zespołowej, zapewnij spójność środowiska poprzez dokumentację.

---

# NumPy

NumPy to pakiet do obliczeń naukowych w Pythonie. Zawiera między innymi:

- obiekt tablicy N-wymiarowej wyposażony w zaawansowane funkcje (w tym broadcasting),
- narzędzia do integracji kodu w C/C++ i Fortranie,
- przydatne funkcje algebry liniowej, transformacji Fouriera i generowania liczb losowych.

Licencja: BSD

---

# Podstawy: typ danych ```ndarray```

Rdzeniem pakietu NumPy jest obiekt ```ndarray```. Reprezentuje on n-wymiarowe tablice jednorodnych typów danych, przy czym wiele operacji wykonywanych jest w skomplikowanym kodzie dla zapewnienia wydajności.

---

# ```ndarray``` a sekwencje *Pythona* (różnice)

Tablice NumPy mają stały rozmiar w momencie tworzenia, w przeciwieństwie do list Pythona, które mogą dynamicznie się rozrastać. Zmiana rozmiaru obiektu ```ndarray``` spowoduje utworzenie nowej tablicy i usunięcie oryginalnej.

Elementy w tablicy NumPy muszą mieć ten sam typ danych, co oznacza, że zajmują jednakową ilość pamięci.

Tablice NumPy umożliwiają zaawansowane operacje matematyczne (i inne) na dużych zbiorach danych. Operacje te są wykonywane bardziej efektywnie i przy użyciu mniejszej ilości kodu niż w przypadku korzystania z wbudowanych sekwencji Pythona.

---

# ```ndarray``` - przykład

```python
>>> import numpy			
>>> a = numpy.zeros((3,5)) # macierz 3 wiersze, 5 kolumn
>>> a                    
array([[0., 0., 0., 0., 0.],
       [0., 0., 0., 0., 0.],
       [0., 0., 0., 0., 0.]])						
```

Często spotykane jest importowanie w taki skrótowy sposób:

```python
import numpy as np
```

---

# typy danych w ramach ```ndarray```

### Podstawowe typy danych:

**Typy liczb całkowitych**: ```int8```, ```int16```, ```int32```, ```int64```: Liczby całkowite o różnym zakresie (8, 16, 32, 64 bity).

```python
np.array([1, 2, 3], dtype=np.int32)
```

**Typy zmiennoprzecinkowe**: ```float16```, ```float32```, ```float64``` - liczby zmiennoprzecinkowe (32 lub 64 bity to najczęściej używane).

```python    
np.array([1.5, 2.3], dtype=np.float64)
```
#### domyślnym typem jest float64

---

# typy danych w ramach ```ndarray```

**Typy logiczne:**

- ```bool```: Wartości logiczne (True, False).
 
```python
np.array([True, False], dtype=np.bool_)
```

**Typy znakowe:**

- ```str_:``` Łańcuchy znaków o stałej długości w formacie Unicode.

- ```bytes_:``` Łańcuchy bajtów zakończone ```'\0'```.

*W starszych wersjach NumPy był typ ```unicode_``` dla tekstu kodowanego w tym formacie.*

---

# typy danych w ramach ```ndarray```

**Typy zespolone:**

```complex64```, ```complex128```: Liczby zespolone (z częściami rzeczywistą i urojoną).

**Typy danych bez znaku:**

```uint8```, ```uint16```, ```uint32```, ```uint64```: Liczby całkowite bez znaku.

### Wykrywanie i zmiana typów danych

Sprawdzenie typu danych: ```array.dtype```

Zmiana typu danych: ```array.astype(np.float32)```

---

# typy danych w ramach ```ndarray```

### Przykład (z dokumentacji):

```python
>>> np.array(["hello", "world!"])
array(['hello', 'world!'], dtype='<U6')
```

Typ danych jest wykrywany jako ciąg Unicode o maksymalnej długości 6, co wystarcza do zapisania obu wpisów bez obcinania. 
Przy krótszym lub dłuższym typie dane są obcinane lub wypełniane zerami, aby dopasować się do szerokości:

```python
>>> np.array(["hello", "world!"], dtype="U5")
array(['hello', 'world'], dtype='<U5')
```

---


# ```ndarray``` - dostęp do elementów 

```python
a[row][column]  # indeksy od 0
a[row, column]  # tak też jest możliwe
```

```python
>>> a[0][2] = 5
>>> a
array([[0., 0., 5., 0., 0.],
       [0., 0., 0., 0., 0.],
       [0., 0., 0., 0., 0.]])
```

Możliwe indeksowanie podtablic (*slice*): ```x[start:stop:step]```

```python
>>> a[0:2, 2:4]
array([[5., 0.],
       [0., 0.]])
```

---

# Podtablice jako widoki, a nie kopie

 Ważną rzeczą, którą warto wiedzieć o wycinkach tablic (*slices*), jest to, że zwracają one widoki (*views*), a nie kopie danych tablicy. Jeśli zmodyfikujemy wycinek:

```python
a_sub = a[0:2, 2:4]
a_sub[0, 1] = 2.5
```
to zarówno wycinek jak i oryginalna tablica mają zmienione wartości:

```python
>>> a_sub
array([[5. , 2.5],
       [0. , 0. ]])
>>> a
array([[0. , 0. , 5. , 2.5, 0. ],
       [0. , 0. , 0. , 0. , 0. ],
       [0. , 0. , 0. , 0. , 0. ]])
```

---

# ```ndarray``` - tworzenie na podstawie innych obiektów

```python
# tworzenie na podstawie listy:
b1D = np.array([ 2., 4., 6. ])                       # jednowymiarowa
b2D = np.array([[1, 2], [3, 4]])                     # dwuwymiarowa
b3D = np.array([[[1, 2], [3, 4]], [[5, 6], [7, 8]]]) # trójwymiarowa
# na podstawie obiektu range:
c = np.array(range(100))          
# na podstawie krotki
d = np.array(( 10., 20., 30. ))  
```

---

# atrybuty określające rozmiar i ```reshape()```

Każda tablica posiada atrybuty: ```ndim``` (liczba wymiarów), ```shape``` (rozmiar każdego wymiaru),```size``` (całkowity rozmiar tablicy):

```python
print(b3D.ndim)      # wypisze: 3
print(b3D.shape)     # wypisze: (2, 2, 2)
print(b3D.size)      # wypisze: 8
```
Możemy użyć funkcji ```reshape``` aby zmienić rozmiar każdego wymiaru, np. umieścić liczby od 1 do 9 w siatce 3x3:

```python
np.arange(1, 10).reshape((3, 3))
```

Operacje *reshape* działają szybko, bo zmieniają tylko indeksy, a nie bufor danych.

---

# zmienne, obiekty, referencje


```python
a = numpy.zeros((3, 3))
b = a                    # b ma referencję do tego samego obiektu co a
c = a.copy()             # c to nowa tablica (nowy obiekt), kopia a
```

```python
>>> b is a
True
>>> c is a 
False
```

---

# Przykład użycia: *element-wise multiplication*

---

# *"pure" Python*

```python
# a i b to pewne listy o takiej samej długości, zawierające liczby
c = []
for i in range(len(a)):
    c.append(a[i] * b[i])
```

---

# C

```c
// a i b to pewne tablice o takiej samej długości, zawierające liczby,
// musimy też zadeklarować c
for (i = 0; i < rows; i++) {
  c[i] = a[i] * b[i];
}
```

---

# MATLAB

```matlab
C = A .* B
```	

# NumPy

```python
c = a * b
```

---

# Dlaczego NumPy jest szybki? Wektoryzacja

Wektoryzacja oznacza brak jawnych pętli, indeksowania itp. w kodzie.

- wektoryzowany kod jest bardziej zwięzły i łatwiejszy do odczytania,
- mniej linii kodu zazwyczaj oznacza mniej błędów,
- kod bardziej przypomina standardową notację matematyczną.

---

# Wektoryzacja


**Pętle, indeksowanie itp. – te operacje odbywają się „za kulisami” w zoptymalizowanym, skompilowanym kodzie C.**

---

# Arytmetyka macierzy w numpy
### (z wartością skalarną)


```
a + 5
a – 3
a * 5
a / 3.14 
a.sum()
a > 15
```

---

# Arytmetyka macierzy w numpy
### Dwie macierze, operacje na odpowiadających sobie elementach (*elementwise*):

```python
x = np.array([[1,2],[3,4]], dtype=np.float64)
y = np.array([[5,6],[7,8]], dtype=np.float64)

# suma elementów; rezultatem obu operacji będzie macierz:
# [[ 6.0  8.0]
#  [10.0 12.0]]
print(x + y)
print(np.add(x, y))

# różnica elementów; rezultatem obu operacji będzie macierz:
# [[-4.0 -4.0]
#  [-4.0 -4.0]]
print(x - y)
print(np.subtract(x, y))

```

---

# Arytmetyka macierzy w numpy
### Dwie macierze, operacje na odpowiadających sobie elementach (*elementwise*):

```python

# Iloczyn elementów; rezultatem obu operacji będzie macierz:
# [[ 5.0 12.0]
#  [21.0 32.0]]
print(x * y)
print(np.multiply(x, y))

# Iloraz elementów; rezultatem obu operacji będzie macierz:
# [[ 0.2         0.33333333]
#  [ 0.42857143  0.5       ]]
print(x / y)
print(np.divide(x, y))

```

---

# Arytmetyka macierzy w numpy
### (wektor - wektor, wektor - macierz)

```python
import numpy as np

x = np.array([[1,2],[3,4]])
y = np.array([[5,6],[7,8]])

v = np.array([9,10])
w = np.array([11, 12])

# Iloczyn skalarny wektorów; rezultatem obu operacji jest 219
print(v.dot(w))
print(np.dot(v, w))

# Iloczyn macierzy i wektora; generuje macierz: [29 67]
print(x.dot(v))
print(np.dot(x, v))
```

---

# Arytmetyka macierzy w numpy
### (macierz - macierz)

```python
# Mnożenie dwóch macierzy,
# rezultatem jest:
# [[19 22]
#  [43 50]]

print(x.dot(y))
print(np.dot(x, y))
```
---

# Inne przydatne operacje

```python
import numpy as np

x = np.array([[1,2],[3,4]])

print(np.sum(x))          # oblicza sumę wszystkich elementów
print(np.sum(x, axis=0))  # oblicza sumę dla każdej z kolumn
print(np.sum(x, axis=1))  # oblicza sumę dla każdego z wierszy
```

---

# Inne przydatne operacje

```python
x = np.array([[1,2], [3,4]])
print(x)    # Wypisze "[[1 2]
            #           [3 4]]"
print(x.T)  # Wypisze "[[1 3]
            #           [2 4]]"

v = np.array([4,5,6,7,8])
print(v)    # Prints "[4 5 6 7 8]"
print(v.T)  # Prints "[4 5 6 7 8]"
```

---

# *Broadcasting*

*Broadcasting* to potężny mechanizm, który umożliwia NumPy operowanie na tablicach o różnych kształtach podczas wykonywania operacji arytmetycznych.

Często mamy mniejszą tablicę i większą tablicę, a chcemy użyć mniejszej tablicy wielokrotnie, aby wykonać pewne operacje na większej tablicy.

---

# Przykład niezbyt wydajny

```python
# Dodamy wektor v do każdego wiersza macierzy x,
# wynik zapiszemy do macierzy y
x = np.array([[1,2,3], [4,5,6], [7,8,9], [10, 11, 12]])
v = np.array([1, 0, 1])

# tworzymy pustą macierz o takich rozmiarach jak x
y = np.empty_like(x) 

# użyjemy pętli pythona i dodamy wiersz po wierszu
for i in range(4):
    y[i, :] = x[i, :] + v

# Y wynosi:
# [[ 2  2  4]
#  [ 5  5  7]
#  [ 8  8 10]
#  [11 11 13]]

print(y)
```

---

# Przykład bardziej wydajny 
```python
# Dodamy wektor v do każdego wiersza macierzy x,
# wynik zapiszemy do macierzy y
x = np.array([[1,2,3], [4,5,6], [7,8,9], [10, 11, 12]])
v = np.array([1, 0, 1])
# złożenie 4 kopii wektora v w macierz:
vv = np.tile(v, (4, 1))   
print(vv)                 
# Wypisuje "[[1 0 1]
#            [1 0 1]
#            [1 0 1]
#            [1 0 1]]"
y = x + vv  # dodanie vv do x
print(y)    # Wypisuje "[[ 2  2  4
            #            [ 5  5  7]
            #            [ 8  8 10]
            #            [11 11 13]]"
```

---

# Przykład użycia *broadcasting*

```python
# Dodamy wektor v do każdego wiersza macierzy x,
# wynik zapiszemy do macierzy y
x = np.array([[1,2,3], [4,5,6], [7,8,9], [10, 11, 12]])
v = np.array([1, 0, 1])
y = x + v  # Dodajemy, zadziała mechanizm broadcasting
print(y)   # Wypisuje "[[ 2  2  4]
           #            [ 5  5  7]
           #            [ 8  8 10]
           #            [11 11 13]]"
```
---

# SciPy

SciPy to otwartoźródłowa biblioteka dla języka Python, zaprojektowana do zaawansowanych obliczeń naukowych i technicznych.

Kluczowe cechy:

Rozszerza możliwości NumPy o zaawansowane funkcje matematyczne.
Obsługuje takie dziedziny jak algebra liniowa, optymalizacja, przetwarzanie sygnałów (w tym proste operacje przetwarzania obrazów), statystyka, transformaty.

---

# Dlaczego SciPy?

- Bardzo szybkie obliczenia dzięki kodowi w C/C++.
- Szeroki wachlarz gotowych funkcji dla nauki i inżynierii

---

# Przykład - wyznacznik macierzy

```python
from scipy import linalg, optimize
import numpy as np
A = np.array([[1, 2], [3, 4]])
determinant = linalg.det(A)
print(determinant)
```
--- 

# SciPy - przegląd

scipy.linalg:

- Rozwiązywanie układów równań liniowych.
- Operacje na macierzach: wyznacznik, wartości własne.

scipy.optimize:

- Funkcje minimalizacyjne.
- Rozwiązywanie równań nieliniowych.

---
 # SciPy - przegląd

scipy.stats:

- Rozkłady statystyczne (np. normalny, t-Studenta).
- Testy statystyczne (np. t-test, ANOVA).

scipy.signal:

- Przetwarzanie sygnałów (np. filtrowanie, transformacje).
- Analiza sygnałów czasowych.

--- 

# Bibliografia:

1. https://numpy.org/doc/2.1/

2. https://docs.scipy.org/doc/scipy/

3. https://massimo-nocentini.github.io/UniFI-Python-Spring-2020/numpy.slides.html#/

4. https://docs.conda.io/projects/conda/en/latest/user-guide/cheatsheet.html
