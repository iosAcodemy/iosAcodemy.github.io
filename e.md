---
layout: page
title: Tests
permalink: /tests/
---

<br>

Zadanie 1
----------

<br>

Oczekujemy, że użytkownik wchodząc do głównego widok aplikacji zobaczy jego tytuł ``"Feed"``

Zadania:

* Określ typ obiektu który będziemy testować używając zmiennej `sut`

* Opisz specyfikację oczekiwanego zachowania w klasie `FeedViewControllerSpec` wykorzystując funkcje `describe` oraz `it`

* Używając funkcji `beforeEach` i `afterEach` załaduj `FeedViewController` z storyboard'a i ustaw go jako obiekt który będziemy testować. Po tescie zmień wartość `sut` na `nil`  

* W funkcjach `it` napisz asercje testujące specyfikacje

--------------

<br>

Zadanie 2
--------

<br>

Oczekujemy, że użytkownik wchodząc do widoku albumu zobaczy w nagłówku jego tytuł

Zadania:

* Utwórz klasę testową `AlbumViewControllerSpec`

* Określ typ obiektu jaki będziemy testować

* Załaduj obiekt ze storyboard'a

* Napisz specyfikację oczekiwanego zachowania

* Używając dummy albumu  
```Album(id: "1Eo1pg2D4beFgf3HFTJTMc", name: "Hello", href: "https://api.spotify.com/v1/albums/1Eo1pg2D4beFgf3HFTJTMc", albumTypeRaw: "single", images: [Image(width: 300, height: 300, url: "spotify:track:0ENSn4fwAbCGeFGVUbXEU3")], artists: nil, genres: nil, popularity: nil, releaseDate: nil, tracks: nil, typeRaw: "artist", uri: "spotify:track:0ENSn4fwAbCGeFGVUbXEU3")```  
wstrzyknij go do testowanego obiektu
6. Napisz asercje testujące specyfikacje używając `expect().toEventually()` by uwzględnić zwrotkę z API

------------

<br>

Zadanie 3
---------

<br>

Oczekujemy, że kiedy użytkownik tapnie w `searchBar` i wyszuka `Adele`, tabela się odświeży i wypełni wynikami

Zadania:
* W klasie `FeedViewControllerSpec` napisz specyfikację oczekiwanego zachowania

* Usuń keyword `private` z `searchController` i `searchResultsViewController` by móc ich używać w testach

* Skonfiguruj odpowiednio `searchBar` i wywołaj metodę która wyszuka wpisane `query`

* W celu sprawdzenia czy tabela się odświeża, utwórz fake klasy UITableView który będzie posiadać zmienną `reloadDataCalled: Bool?`. Nadpisz w niej metodę `reloadData()` dodając w niej zmianę `reloadDataCalled: Bool?` na `true`

* W celu sprawdzenia czy tabela wypełniła się wynikami możesz wykorzystać parametr `tableView.numberOfRowsInSection(Int)`

* Napisz asercje testujące specyfikacje używając `expect().toEventually()` by uwzględnić zwrotkę z API.
