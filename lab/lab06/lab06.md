# Laboratorium nr 6: Testy jednostkowe.

Celem tego laboratorium jest zapoznanie się z podstawami testowania jednostkowego w Pythonie za pomocą modułu ```unittest```. Moduł ten jest elementem biblioteki standarodwej pythona i nie wymaga doinstalowywania żadnych pakietów. W trakcie laboratorium nauczysz się, jak tworzyć i uruchamiać testy jednostkowe dla funkcji w Pythonie, a następnie przygotujesz testy dla kodu tworzonego sukcesywnie na poprzednich zajęciach.

## Wprowadzenie do ```unittest```

Moduł ```unittest``` w Pythonie służy do tworzenia testów jednostkowych, które pozwalają na automatyczne sprawdzenie poprawności działania poszczególnych funkcji i metod w Twoim kodzie. 

Testowanie jednostkowe to forma testowania oprogramowania, w której weryfikujemy, czy izolowany kod źródłowy działa zgodnie z oczekiwaniami. Testy wykonywane są na poziomie **jednostki** (klasy lub jej metody, czy pojedynczych funkcji), w odróżnieniu od testów przeprowadzanych na poziomie integracji lub systemu.

Dzięki testom jednostkowym możesz upewnić się, że przygotowany kod jest poprawny, a jakiekolwiek zmiany w implementacji nie wprowadziły nowych błędów.

## Prosty kod, który poddamy testowaniu

Zacznijmy od stworzenia prostego pliku z funkcjami, które będziemy testować. Utwórz plik ```math_operations.py``` z następującą zawartością:


```python
def add(a, b):
    return a + b

def subtract(a, b):
    return a - b

def multiply(a, b):
    return a * b

def divide(a, b):
    if b == 0:
        raise ValueError("Cannot divide by zero")
    return a / b
```

## Pierwszy test jednostkowy

Aby rozpocząć testowanie funkcji z pliku ```math_operations.py```, musimy utworzyć odpowiedni plik testowy. W Pythonie testy jednostkowe są organizowane za pomocą klas, które dziedziczą po klasie bazowej ```unittest.TestCase```. Każda metoda testowa w tej klasie odpowiada za przetestowanie konkretnej funkcji lub fragmentu kodu.

Stwórz plik ```test_math_operations.py``` i dodaj następujący kod:

```python 

import unittest
from math_operations import add, subtract, multiply, divide

class TestMathOperations(unittest.TestCase):

    def test_add(self):
        self.assertEqual(add(2, 3), 5)  # Sprawdzamy, czy 2 + 3 = 5
        self.assertEqual(add(-1, 1), 0)  # Sprawdzamy, czy -1 + 1 = 0

    def test_subtract(self):
        self.assertEqual(subtract(5, 3), 2)  # Sprawdzamy, czy 5 - 3 = 2
        self.assertEqual(subtract(3, 5), -2)  # Sprawdzamy, czy 3 - 5 = -2

    def test_multiply(self):
        self.assertEqual(multiply(2, 3), 6)  # Sprawdzamy, czy 2 * 3 = 6
        self.assertEqual(multiply(-1, 5), -5)  # Sprawdzamy, czy -1 * 5 = -5

    def test_divide(self):
        self.assertEqual(divide(6, 3), 2)  # Sprawdzamy, czy 6 / 3 = 2
        self.assertRaises(ValueError, divide, 6, 0)  # Sprawdzamy, czy wyjątek ValueError wystąpi, gdy dzielimy przez 0

if __name__ == '__main__':
    unittest.main()

```

 Klasa ```TestMathOperations``` dziedziczy po klasie ```unittest.TestCase```, co pozwala jej na korzystanie z wbudowanych metod testujących w Pythonie. Każda metoda zaczynająca się od ```test_``` jest traktowana jako oddzielny test, który jest uruchamiany przez framework ```unittest```. W naszym przykładzie:

- ```test_add()``` testuje funkcję ```add()```,sprawdzając, czy zwraca poprawny wynik.

- ```test_subtract()``` testuje funkcję ```subtract()```.

- ```test_multiply()``` testuje funkcję ```multiply()```.
- ```test_divide()``` testuje funkcję ```divide()``` i sprawdza, czy zgłaszany jest wyjątek ```ValueError``` w przypadku dzielenia przez zero.

### Uruchamianie testów z konsoli:

Aby uruchomić testy, wystarczy wywołać plik testowy za pomocą polecenia w terminalu:

```bash
python -m unittest test_math_operations.py
```

przykładowy output:

```bash
....
----------------------------------------------------------------------
Ran 4 tests in 0.000s

OK
```

## Asercje

Asercje to podstawowe narzędzie w testowaniu jednostkowym, które pozwala na porównanie wyników uzyskanych z funkcji lub metod z wartościami oczekiwanymi. Moduł ```unittest``` w Pythonie dostarcza szereg wbudowanych metod asercji, które umożliwiają sprawdzenie, czy wyniki testów są zgodne z oczekiwaniami. Asercje pomagają w automatycznym wykrywaniu błędów w kodzie, sygnalizując, gdy coś jest niezgodne z przewidywaniami. 

Asercja to specjalna metoda, która zwykle nie zwraca żadnej wartości (tzn. zwraca ```None```), ale w przypadku niepowodzenia testu, generują wyjątek (np. ```AssertionError```), co powoduje, że test kończy się niepowodzeniem.

Przykładową asercją, którą widziałeś już w kodzie jest ```assertEqual()```. Testuje ona, czy pierwsza i druga wartość przekazane jako parametr są równe. Jeśli wartości nie będą równe, test zakończy się niepowodzeniem. 

Pełna lista asercji modułu ```unittest``` znajduje się w dokumentacji: https://docs.python.org/3/library/unittest.html#assert-methods 

Otwórz teraz listę i przyjrzyj się jej, gdyż w toku zajęć będziesz korzystać z różnych asercji.



## ${\color{lightgreen}{\textsf{\textbf{ZADANIA do samodzielnego wykonania:}}}}$

 Twoim zadaniem jest rozszerzenie funkcjonalności ```math_operations.py``` o nowe funkcje i przygotowanie testów do nich (**Zacznij od testów!**). 

 Nowe funkcje to:

 - ```mod(a, b)``` – funkcja zwracająca resztę z dzielenia ```a``` przez ```b```. Pamiętaj, że jeśli ```b``` wynosi ```0```, powinien zostać zgłoszony wyjątek ```ValueError```.
- ```power(a, b)``` – funkcja zwracająca ```a``` podniesione do potęgi ```b```.

- ```unique_numbers(*args)``` – funkcja, która przyjmuje dowolną liczbę argumentów i zwraca zbiór zawierający tylko unikalne liczby (eliminując duplikaty).

- ```range_difference(range1, range2)``` – funkcja, która przyjmuje dwa obiekty typu ```range``` i zwraca krotkę zawierającą elementy, które nie występują w obu zakresach (różnica symetryczna).


**Zadanie**: Zacznij od napisania testów. Powinieneś użyć różnych asercji, takich jak:

```assertTrue()```, ```assertFalse()```, ```assertIn()```, ```assertNotIn()```, ```assertRaises()```. 


**Zadanie**: Napisz implementację 4 wskazanych funkcji. Uruchom testy. Dokonaj poprawek w implementacji, jeśli testy nie zakończyły się sukcesem.


**Zadanie**: Do implementacji pokera z poprzedniego zadania dodaj klasę testującą, która będzie sprawdzać poprawność implementacji funkcji i klas z modułu ```poker```. Testy powinny być przygotowane dla:

#### Funkcji pomocniczych:

- Testowanie funkcji ```histogram()``` w celu zapewnienia, że poprawnie liczy wystąpienia znaków w napisie.

- Testowanie funkcji ```is_rank_sequence()``` dla różnych rąk kart.

- Testowanie funkcji ```hand_rank()``` dla różnych kombinacji kart, aby upewnić się, że prawidłowo klasyfikuje ręce.

#### Klas:

- Testowanie klasy ```Card``` (czy odpowiednio tworzy obiekt, konwertuje na string).

- Testowanie klasy ```Deck``` (czy poprawnie tworzy talię kart, czy talia jest mieszana i rozdawana).

- Testowanie klasy ```Player``` (czy poprawnie przydziela karty, zarządza stanem gracza i jego ręką).

