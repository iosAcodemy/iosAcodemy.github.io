---
layout: page
title: TableView
permalink: /TableView/
---

Następnym zadaniem będzie użycie RandomUserApiManager do pobrania losowych 20-stu użytkowników oraz wyświetlenie ich imienia i nazwiska oraz powiązania listy userów z rx'owym data source tableView (`tableView.rx.items`)

<br>

Zadanie 1
------------

<br>

Przejdz do pliku `RandomUsersListViewController`. 

W metodzie `bindViewModel()` utwórz wiązanie `viewModel.users` z property `tableView.rx.items`.
Następnie w domknięciu metody `bindTo()` na tableView użyj metody `dequeueReusableCell` aby pobrać komórkę.
Utwórz `UserViewModel` na podstawie modelu `User` i przypisz go do property `viewModel` komórki.
Zwróć w domknięciu komórkę.
<br>
Rozpocznij pobieranie użytkowników. Użyj metody `getUsers(liczba rekordów)`.
Aby śledzić postęp żądania, użyj metody trackActivity z parametrem `indicator`.
Obserwuj nowe zdarzenia i sprawdź czy zapytanie zakończyło się sukcesem.
Ustaw property `errorLabel.isHidden` na `true` w przypadku sukcesu, `false` w przypadku błędu oraz ustaw `errorLabel.text` z zawartością `error.localizedDescription`.
Powiąż właściwość `indicator` z HUD.rx_isVisible` aby poinformować użytkownika o trwającym zapytaniu.

<br>

Zadanie 2
-----------

Sprawdź czy działa ;)

<br>

Zadanie 3
-----------

Otwórz plik `UserTableViewCell`. Uzupełnij metode `bindViewModel()`.
Użyj `combineLatest` aby połączyć sygnały `firstName` oraz `lastName`.
Zmapuj wartości i utwórz obiekt typu `String` oraz powiąż go z właściwościa `nameLabel.rx.text`.

Zadanie 4
-----------
Enjoy! :party_parrot: :beers:


....
