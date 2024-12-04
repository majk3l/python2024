# Laboratorium nr 5: Dekoratory. 

## ${\color{lightgreen}{\textsf{\textbf{ZADANIA do samodzielnego wykonania:}}}}$

**Zadanie**: Zmodyfikuj kod z poprzedniego laboratorium: zmień klasę ```Player``` tak, aby zaimplementować wzorzec getter/setter dla atrybutu ```stack``` za pomocą dekoratora ```@property```. Metoda ```get_stack_amount(self)``` nie będzie już potrzebna. 

Zmodyfikuj też logikę gry tak, aby przy obsłudze liczby żetonów gracza (stack) wykorzystywany był getter/setter.

**Zadanie**: W klasie Player dodaj metodę klasy ```create_players(cls, number_of_players, initial_stack)```, która wygeneruje listę graczy na podstawie podanej liczby graczy oraz początkowej liczby żetonów. Dzięki tej metodzie możesz uniknąć ręcznego tworzenia instancji w pętli w ```main.py```. Użyj odpowiedniego dekoratora.

### Na tym etapie output Twojej przykładowej rozgrywki powinien wyglądać mniej więcej następująco:

```text
Podaj liczbę graczy (2-6): 2

Twoje karty: D♣ 2♦ 6♦ 5♥ 3♥

Twoje żetony: 950
Obecny zakład: 50
1. Sprawdź (call)
2. Podbij (raise)
3. Pasuj (fold)
Wybierz opcję (1-3): 2
Podaj kwotę podbicia: 50
Podbijasz do 100.
Gracz 2 pasuje.

Wszyscy gracze spasowali. Gracz 1 wygrywa i zgarnia pulę 150!
```

**Zadanie**: Upewnij się, że Twoja implementacja obsługuje poprawnie przypadki, w których gracze mają takie samo starszeństwo uładu kart (np. wysoka karta, jedna para). 

**Zadanie**: Wprowadź cykliczną rozgrywkę, jeśli gracze nie mają już żetonów żeby dokonać minimalnego zakładu, usuwaj ich z listy aż zostanie jeden gracz (zwycięzca). Możesz to zrobić przykładowym kodem:

```python
minimal_bet = 50
    pot = 0

    # Pobranie minimalnego zakładu

    # działamy na kopii, bo nie chcemy usuwać gracza z listy, którą przeglądamy, usuwamy z oryginalnej
    for player in players.copy():
        try:
            player.stack -= minimal_bet
            pot += minimal_bet
        except ValueError:
            print(f"{player} nie ma wystarczających środków na minimalny zakład i odpada z gry.")
            players.remove(player)

    if len(players) < 2:
        print("Zbyt mało graczy do rozpoczęcia gry.")
        return
```
