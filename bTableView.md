---
layout: page
title: Bindings
permalink: /Bindings/
---


Zadanie 1
----------

<br>

* Przenieś metody protokołów```UITableViewDataSource``` oraz  ```UITableViewDelegate``` do ```Extension``` klasy ```ArtistViewController```

<br>


Zadanie 2
-----------

<br>

* Stwórz dwa obiekty typu ```SpotifyItemSection``` dla typów ```Album``` i ```Track``` z parametrami

Album

* ```title: "Albums"```
* ```limit: 4```
* ```cellHeight: 60```

Tracks

* ```title: "Tracks"```
* ```limit: 8```
* ```cellHeight: 45```

<br>

* Stwórz tablicę o nazwie ```sections``` z nowopowstałymi obiektami.


<br>


Zadanie 3
-----------

<br>

Zaktualizuj metody ```getTopTracks()``` oraz  ```getAlbums()``` tak, aby uwzględniały nowe źródła danych ```UITableView```


* Dodaj do nich parametr o odpowiednim typie obiektu ```SpotifyItemSection <>```.

* Usuń stare metody `show`

* Ustaw w sekcji property `expand = false` oraz przypisz otrzymane obiekty do `items`

* Odśwież tabelę w clousure  ```clearAllNotice(closure: () ->())```

<br>


Zadanie 4
-----------

<br>


* Stwórz metodę zwracającą komorkę typu  ```AlbumTrackTableViewCell``` przy użyciu ```tableView.dequeReusableCell(indexPath:indexPath)``` dla obiektu typu ```Track```.

* Skonfiguruj komórkę obiektem  z tabeli ```items``` odpowiedniej sekcji.

* Zaimplementuj analogiczną metodę dla obiektów typu ```Album``` - komórka typu```SearchResultTableViewCell```


<br>


Zadanie 5
-----------

<br>

* Korzystając z utworzonych w poprzednim zadaniu metod, uzupełnij implementację
<br>
 ```func tableView(tableView: UITableView, cellForRowAtIndexPath indexPath: NSIndexPath) -> UITableViewCell ```
<br>
tak, by w zależności od typu obiektu sekcji zwracała odpowiedni typ komórki.


<br>


Zadanie 6
-----------

<br>

Bazując na ustawieniach poszczególnych sekcji znajdujących się w tablicy ```sections```, zaktualizuj implementację poniższych metod:


*  ```numberOfSectionsInTableView(tableView: UITableView) -> Int```

* ``` tableView(tableView: UITableView, titleForHeaderInSection section: Int) -> String?```

*   ```tableView(tableView: UITableView, heightForRowAtIndexPath indexPath: NSIndexPath) -> CGFloat```

*   ```tableView(tableView: UITableView, numberOfRowsInSection section: Int) -> Int ```


<br>


Zadanie 7
-----------

<br>

* Wydziel logikę prezentacji kontrolerów do osobnych metod przyjmujących jako parametr obiekt typu ```Album``` dla ```AlbumViewController``` oraz ```Track``` dla ```PlayerViewController```

* W metodzie
```tableView(tableView: UITableView, didSelectRowAtIndexPath indexPath: NSIndexPath)  ```, w zależności od typu obiektu klikniętej komórki, wywołaj odpowiednią  metodę prezentującą kontroler następnego widoku.


<br>


Zadanie 8
-----------

<br>


* Stwórz metodę ```reloadSection(section: Int)``` która przeładowuje wskazaną sekcję w tabeli z efektem .Fade.

* Nadpisz metodę
 ```tableView(tableView: UITableView, viewForFooterInSection section: Int) -> UIView?```

* Jeżeli paramter sekcji ```hasMore``` ma wartość ```true``` stwórz przy pomocy metody ```tableView.dequeueReusableHeaderFooterView()``` obiekt typu  ```MoreResultsFooterView?```.


* Dla stworzonego obiektu przypisz do tapAction closure, który dla danej sekcji ustawi ```expanded = true``` oraz wywoła wcześniej utworzoną metodę ```reloadSection(section: Int)```.


* W funkcji ```tableView(tableView: UITableView, heightForFooterInSection section: Int) -> CGFloat ``` zwróć odpowiednią wartość wysokości stopki.

* Jeśli parametr sekcji ```hasMore``` posiada wartość ```true``` ustaw wysokość Footera na ```45.0```. W innym przypadku funkcja powinna zwrócić ```CGFloat.min```
