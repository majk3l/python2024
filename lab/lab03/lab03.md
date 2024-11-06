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

 **5.** W pliku głównym utwórz logikę bardzo podstawowej (niepełnej) rozgrywki. W rozgrywce N graczy będzie uczestniczył użytkownik i N-1 "botów", którzy na razie będą podejmować uproszczone decyzje:

 - aplikacja pyta ilu graczy powinno brać udział w rozgrywce: możliwy wybór 2 - 6
    - należy obsłużyć wejście z klawiatury i pytać o liczbę dopóki użytkownik poda prawidłową wartość z zakresu od 2 do 6. Użyj klauzuli ```try-except```, możesz zmodyfikować przykład z [https://docs.python.org/3/tutorial/errors.html#handling-exceptions](https://docs.python.org/3/tutorial/errors.html#handling-exceptions)


- wszyscy gracze otrzymują początkową liczbę żetonów: 1000, ustalana jest stawka minimalnego zakładu na: 50. Pula żetonów wynosi 0.

- pobierany jest minimalny zakład od każdego gracza i dodawany do puli. 

- rozdawane są karty wszystkim graczom (użytkownik widzi tylko swoje karty), następnie gracz otrzymuje 4 opcje, według których może:

    - Czekać (check): możliwe tylko wtedy, gdy nie ma aktywnego zakładu  (nikt nie podbił stawki).
    - Sprawdzić (call): wyrównać aktualny zakład.
    - Podbić (raise): zwiększyć aktualny zakład.
    - Spasować (fold): zrezygnować z udziału w rozdaniu.

    *Gracze boty mogą jedynie czekać, albo, jeśli gracz podbił, pasować lub sprawdzać (losowo). Uwaga: upewnij się, że gracz nie może czekać, jeśli jest aktywny zakład do wyrównania.*

    *Gracze podejmują decyzje w ustalonej kolejności (zgodnie ze swoimi numerami).*

- Po rundzie zakładów ustalane jest starszeństwo układów na rękach graczy i wyłaniany jest zwycięzca (który otrzymuje żetony z puli).

- Koniec rozgrywki
