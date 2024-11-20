# Laboratorium nr 4: Klasy

## ${\color{lightgreen}{\textsf{\textbf{ZADANIA do samodzielnego wykonania:}}}}$

Celem laboratorium jest wprowadzenie klas do projektu aplikacji pokera pięciokartowego dobieranego. Zadanie polega na uzupełnieniu implementacji klas na podstawie przygotowanego szablonu tak, aby poprawnie udało się przeprowadzić rozgrywkę, zaimplementowaną na laboratorium poprzednim. Wprowadzimy następujące klasy:

- ```Card``` - reprezentuje kartę. Powinna mieć dwa pola do przechowywania koloru i rangi, metodę zwracającą jej reprezentację w postaci krotki i metodę ```__str__``` która będzie potrzeba do wypisywania karty funkcją ```print```.

- ```Deck``` - reprezentuje talię. Powinna mieć jedno pole (listę) do przechowywania kart oraz metody do tasowania, rozdawania i ```__str__```.

- ```Player``` - reprezentuje gracza. Większość jej funkcjonalności jest już dostarczona.

Szablon:

```python

import random

class Card:
    # słownik symboli unicode
    unicode_dict = {'s': '\u2660', 'h': '\u2665', 'd': '\u2666', 'c': '\u2663'}
       
    def __init__(self, rank, suit):
    # TODO: definicja konstruktora, ma ustawiać pola rangi i koloru.

        pass
    def get_value(self):
    # TODO: definicja metody (ma zwracać kartę w takiej reprezentacji, jak dotychczas, tzn. krotka)
        pass
    def __str__(self):
    # TODO: definicja metody, przydatne do wypisywania karty    
        pass

class Deck():
    
    def __init__(self, *args):
    # TODO: definicja metody, ma tworzyć niepotasowaną talię (jak na poprzednich lab)
        pass
    def __str__(self):
    # TODO: definicja metody, przydatne do wypisywania karty
        pass
    def shuffle(self):
    # TODO: definicja metody, tasowanie
        pass
    def deal(self, players):
    # TODO: definicja metody, otrzymuje listę graczy i rozdaje im karty wywołując na nich metodę take_card z Player
        pass

class Player():

    def __init__(self, money, name=""):
        self.__stack_ = money
        self.__name_ = name
        self.__hand_ = []

    def take_card(self, card):
        self.__hand_.append(card)

    def get_stack_amount(self):
        return self.__stack_

    def change_card(self, card, idx):
        # TODO: przyjmuje nową kartę, wstawia ją za kartę o indeksie idx, zwraca kartę wymienioną

    def get_player_hand(self):
        return tuple(self.__hand_)

    def cards_to_str(self):
    # TODO: definicja metody, zwraca stringa z kartami gracza
        pass


```

Wprowadź i uzupełnij klasy, pamiętaj o strukturze programu (moduły, pakiety). Dopasuj logikę rozgrywki w skrypcie głównym tak, aby korzystać z nowych klas. W razie potrzeby dopasuj implementację (ale nie logikę, nie zmieniaj zasad gry!) rozgrywki.

