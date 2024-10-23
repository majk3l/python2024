# Laboratorium nr 2: Pętle. Definiowanie funkcji. Słowniki. 

Na tym laboratorium zapoznasz się z pętlami `for` i `while` oraz przećwiczysz definiowanie własnych funkcji. Przyjrzymy się także słownikom, które są wygodnym sposobem przechowywania danych w postaci par klucz - wartość.

## Pętle `for`

Pętla `for` w Pythonie służy do iteracji po elementach sekwencji (np. listy, krotki, łańcucha znaków) lub innego obiektu iterowalnego.

### Składnia

```python
for element in sekwencja:
    # kod do wykonania w każdej iteracji
```
Przykład:
```python
fruits = ['jabłko', 'banan', 'wiśnia', 'kiwi']
for fruit in fruits:
    print(fruit)
```

${\color{green}{\textsf{{Ćwiczenie:}}}}$ Zmodyfikuj powyższą pętlę tak, aby wypisywała najpierw indeks elementu, a później dany element. Użyj poznanej na wykładzie funkcji ```enumerate()```.

${\color{green}{\textsf{{Ćwiczenie:}}}}$ Wypisz posortowane elementy powyższej listy. Użyj funkcji [```sorted()```](https://docs.python.org/3/library/functions.html#sorted). Zwróć uwagę na jej działanie (np. czy modyfikuje oryginalne dane).

${\color{green}{\textsf{{Ćwiczenie(*):}}}}$  Wypisz posortowane elementy, ale z oryginalnymi indeksami.


### ```range()```

Funkcja ```range()``` generuje sekwencję liczb, którą można iterować.

```python
for i in range(5):
    print(i)
```

${\color{green}{\textsf{{Ćwiczenie:}}}}$ Zmodyfikuj powyższą pętlę tak, aby wypisać wszystkie dwucyfrowe liczby nieparzyste. Jeśli nie pamiętasz pozostałych parametrów funkcji ```range()``` do definiowania przedziału, zajrzyj do slajdów z wykładu lub dokumentacji.

### ```for``` wewnątrz ```for```

Pętle możemy zagnieżdżać:

```python
for i in range(1, 4):
    for j in range(1, 4):
        print(f'i={i}, j={j}')
```
Zwróć uwagę na wywołanie funkcji ```print()```. Używa ona tzw. *formatted string literals*, które pozwalają na wypisywanie tekstu łączonego z wartościami wyrażeń. Uruchom powyższy przykład oraz przeczytaj więcej o tym zapisie w [dokumentacji](https://docs.python.org/3/tutorial/inputoutput.html#formatted-string-literals).

## Pętle ```while```

Pętla ```while``` działa tak jak w innych językach, czyli powtarza blok kodu tak długo, jak długo warunek jest spełniony.

Składnia:

```python
while warunek:
    # kod do wykonania, gdy warunek jest prawdziwy
```

Przykład prostej pętli while:

```python
i = 0

while i < 5:
    print(i)
    i += 1  # inkrementacja zmiennej sterującej
```
Należy pamiętać (tak jak i w przypadku pętli ```for``` i instrukcji ```if```) o definiowaniu bloku kodu poprzez wcięcia oraz o kończeniu nagłówka instrukcji znakiem ```:```.

## Definiowanie Funkcji

Funkcje pozwalają na tworzenie modułowego i wielokrotnego użytku kodu. Możesz zdefiniować własne funkcje używając słowa kluczowego ```def```.
Składnia:

```python
def nazwa_funkcji(argumenty):
    # blok kodu funkcji
    return wartość  # opcjonalne
```

Przykłady:

- Funkcja bez argumentów i wartości zwracanej:
```python
def greet():
    print("Witaj, świecie!")
```

- Funkcja z argumentami:

```python
def greet(name):
    print(f"Witaj, {name}!")
```

- Funkcja z wartością zwracaną:

```python
def add(a, b):
    return a + b

result = add(5, 3)
print(result)
```

## Słowniki

Słowniki to wbudowane struktury danych w Pythonie, które przechowują pary klucz-wartość. Pozwalają one na szybki dostęp do wartości na podstawie unikalnych kluczy. Słowniki są mutowalne, co oznacza, że można zmieniać ich zawartość po utworzeniu.

### Tworzenie słownika

Słownik można utworzyć na kilka sposobów:

- tworząc pusty słownik

```python
empty_dict = {}
```

- używając nawiasów klamrowych `{}`:

```python
my_dict = {
    'imie': 'Jan',
    'wiek': 25,
    'miasto': 'Rzeszów'
}
```
- używając funkcji ```dict()```:

${\color{green}{\textsf{{Ćwiczenie:}}}}$ Utwórz powyższy słownik za pomocą funkcji ```dict()```. Jeśli nie pamiętasz jak jej użyć, zobacz przykład na wykładzie.


### Usuwanie Elementów

- Użycie słowa kluczowego ```del```:

```python
del my_dict['miasto']
print(my_dict)
```

- Użycie metody ```pop()```:

```python
wiek = my_dict.pop('wiek')
print(wiek)
print(my_dict)
```

### Iterowanie po elementach słownika

${\color{green}{\textsf{{Ćwiczenie:}}}}$ Za pomocą pętli ```for``` wypisz pary klucz-wartość ze słownika ```my_dict``` (Jeśli nie pamiętasz jak to zrobić zajrzyj do wykładu bądź dokumentacji).

${\color{green}{\textsf{{Ćwiczenie:}}}}$ Napisz funkcję, która jako parametr przyjmuje napis tekstowy i zwraca histogram znaków
występujących w tym napisie (czyli pary znak-liczba wystąpień). Wynikiem powinien być
słownik. Przykład:

```python
>>> histogram("Ala ma kota")
{'t': 1, 'a': 3, 'l': 1, 'A': 1, 'k': 1, 'm': 1, 'o': 1}
```

## ${\color{green}{\textsf{\textbf{ZADANIA do samodzielnego wykonania:}}}}$

Napisz następujące funkcje niezbędne do implementacji gry w pokera pięciokartowego dobieranego:

**1.** ```deck()``` - zwraca listę reprezentującą talię kart w kolejności od najmłodszej do najstarszej. Każda karta posiada 2 atrybuty, będące łańcuchem tekstowym:
- rangę - możliwe wartości: ```'2', '3', '4', '5', '6', '7', '8', '9', '10', 'J', 'D', 'K', 'A'``` (karty od 2 do 10 oraz walet, dama, król, as)
- kolor - możliwe wartości: 
  - ```'c'``` - &clubs; trefl (**c**lubs)
  - ```'d'``` - &diams; karo (**d**iamonds)
  - ```'h'``` - &hearts; kier (**h**earts)
  - ```'s'``` - &spades; pik (**s**pades)


Każdym elementem listy powinna być krotka, będąca parą (ranga, kolor). Przykładowo *as pik*:
 
 # &#127137;

 reprezentowany będzie jako ```('A', 's')```. Lista powinna zawierać 52 elementy (13 rang * 4 kolory).
 

**2.** ```deal(deck, n)``` - przyjmuje talię kart (```deck```) oraz liczbę graczy (```n```), zwraca n-elementową listę 5-elementowych list z kartami rozdanymi graczom. Każda 5-elementowa lista kart gracza zawiera 5 krotek reprezentujących kartę.  


**3.** 
Zaimplementuj funkcję ```hand_rank(hand)```, która będzie przyjmować jako parametr 5-elementową listę krotek reprezentujących karty i zwracać liczbę całkowitą w zakresie od 10 do 1 reprezentującą rangę układu tych 5 kart w pokerze pięciokartowym 
dobieranym (http://pl.wikipedia.org/wiki/Poker), gdzie 10 - to poker królewski, 9 - poker, 8 - kareta, 7 - full itd. Do implementacji wykorzystaj 
szablon funkcji umieszczony poniżej. Umieść go w tym samym pliku co swoje definicje funkcji ```histogram```, ```deck``` oraz ```deal```.

Zwróć uwagę, że o starszeństwie decydują różne reguły, które opierają się na 3 atrybutach:

- czy wszystkie karty są jednego koloru,
- czy karty są "po kolei",
- czy w układzie występują powtórzenia, tzn. zawiera 4, 3, 2 karty o tej samej randze.

Do sprawdzenia ile rang kart powtarza się, najłatwiej będzie użyć zaimplementowanej już funkcji ```histogram``` - 
funkcja ta przyjmowała łańcuch tekstowy, ale jeżeli została zaimplementowana z użyciem pętli ```for``` nic nie stoi na przeszkodzie wywołać
ją z listą jako parametr. Gdy wywołamy ją na liście rang karty, możemy sprawdzić czy występują powtórzenia kart, natomiast gdy wywołamy ją
na liście kolorów kart możemy sprawdzić czy wszystkie karty są jednego koloru. Przykładowo mamy listę:

```[('A','c'), ('A','s'), ('A','h'), ('9','c'), ('8','s')]```

która reprezentuje następujący układ kart:

 # &#127153; &#127185; &#127137; &#127193; &#127144;

możemy stworzyć listę samych rang z układu, która będzie wyglądać następująco:

```['A', 'A', 'A', '9', '8']```

po wywołaniu funkcji ```histogram``` na powyższej liście otrzymamy słownik:

```{'8': 1, '9': 1, 'A': 3}```

po sprawdzeniu wartości słownika wiemy, czy karta o jakiejś randze pojawiła się więcej niż raz (w tym wypadku as).


```python

def hand_rank(hand):
    hand_rank_list = []  # TODO: pobierz liste rang kart gracza. Uzyj listy skladanej.
    hand_color_list = [] # TODO: pobierz liste kolorow kart gracza. Uzyj listy skladanej.

    # histogramy rang kart graczy  okresla ile razy wystapila karta o tej samej randze,
    # potrzebne do ustalenia ukladu kart
    # TODO: uzyj funkcji 'histogram' z poprzedniego laboratorium!
    hand_rank_histogram = histogram(hand_rank_list)
    # histogramy kolorow kart graczy, jesli 5 in hand_color_histogram.values() == True
    # to wszystkie karty sa jednego koloru
    hand_color_histogram = histogram(hand_color_list)
    # czy karty sa "po kolei" (konieczne w: poker krolewski, pokerze, strit)
    # TODO: zaimplementuj funkcje is_rank_sequence(hand) ktora zwraca True jesli karty sa po kolei
    #       w przeciwnym razie zwraca false. Pobiera liste kart jako parametr
    is_hand_rank_sequence = is_rank_sequence(hand) 

    hand_strength = 0 # zwracana zmienna, ja trzeba ustawic
    # ------ sprawdzamy uklad gracza 1:
    # --- sprawdzamy poker krolewski: 5 kart w tym samym kolorze, po kolei, najwyzsza to as
    if( (5 in hand_color_histogram.values()) and ( 'A' in hand_rank_list ) and is_hand_rank_sequence):
        hand_strength = 10
    # --- sprawdzamy poker: 5 kart w tym samym kolorze, po kolei
    elif( ( 5 in hand_color_histogram.values()) and is_hand_rank_sequence):
        hand_strength =  9
    # TODO: za pomoca instrukcji elif oraz else sprawdz ponizsze warunki i ustaw
    #       wartosc zmiennej hand_strength:
    #        - sprawdzamy karete: 4 karty tej samej rangi
    #        - sprawdzamy full house: 3 karty tej samej rangi i 2 karty tej samej rangi
    #        - sprawdzamy kolor
    #        - sprawdzamy strit
    #        - sprawdzamy trojke 
    #        - sprawdzamy wysoka karte
    #        - sprawdzamy dwie pary
    #        - sprawdzamy jedna pare

    return(hand_strength)

```

---

*autor: Michał Kępski (mkepski[at]ur.edu.pl)*

