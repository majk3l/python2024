# Laboratorium nr 3: Definiowanie funkcji. Moduły i pakiety. Wyjątki

## ${\color{lightgreen}{\textsf{\textbf{ZADANIA do samodzielnego wykonania:}}}}$


**1.** Przenieś dotychczas napisane funkcje implementujące elementy pokera 5-kartowego dobieranego do pliku ```poker.py```.


**2.** Dodaj do modułu ```poker``` funkcję ```cards_to_string(cards)``` która przyjmuje listę kart w postaci krotek, a zwraca łańcuch reprezentujący karty wizualnie z użyciem symboli unicode, przykładowo:

```
D♥ 9♦ K♦ J♥ 8♠  
```

skorzystaj z symboli unicode: '\u2660', '\u2665', '\u2666', '\u2663'

**3.** Dodaj plik main.py. W nim przetestuj działanie zaimplementowanej ostatnio funkcji ```hand_rank```, korzystając z następujących danych testowych:

```python

hands = [[('10', 'h'), ('J', 'h'), ('D', 'h'), ('K', 'h'), ('A', 'h')], # Przykład: poker królewski        : 10
         [('A', 'c'), ('A', 's'), ('A', 'h'), ('A', 'd'), ('8', 's')],  # Przykład: kareta                 : 8
         [('5', 'c'), ('6', 'd'), ('7', 'h'), ('8', 's'), ('9', 'd')],  # Przykład: strit                  : 5
         [('A', 's'), ('2', 'h'), ('3', 'd'), ('4', 'c'), ('5', 's')],  # Przykład: też strit, (As jako 1) : 5
         [('2', 'c'), ('2', 'd'), ('5', 'h'), ('9', 's'), ('K', 'd')]   # Przykład: jedna para             : 2
         ]

 ```

 **4.** Napisz funkcję ``exchange_cards(hand, indices, deck)`` która pozwala na wymianę wybranych kart w ręce gracza. Funkcja przyjmuję listę kart na ręce gracza, listę indeksów oraz talię. Wymienione karty powinny trafić "na spód" talii. Funkcja zwraca nową rękę z wymienionymi kartami.

