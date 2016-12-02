---
layout: page
title: Bindings
permalink: /Bindings/
---

<br>

W chwili obecnej zmiana danych przez użytkownika nie wpływa w żaden sposób na dane w wizytówce - wyświetlane wartości zależą od zmiennych znajdujących się w `SimpleFormViewModel`.
W tym ćwiczeniu nauczysz się wiązać ze sobą obiekty znajdujące się w `kontrolerze` i `ViewModelu`, tak aby zmiana ich wartości była odzwierciedlona na wizytówce.
Spójrz na kod w klasie `SimpleFormViewController` - metoda ```bindLabels()``` odpowiada za powiązanie zmiennych z ViewModelu, z etykietami znajdującymi się w wizytówce.

<br>

Zadanie 1
----------

<br>

Wprowadzenie danych do `firstNameTextField` oraz `lastNameTextField` powinno zmienić wartości wyświetlane w `fullNameLabel`.

* Zobacz metodę ```bindTextFields()``` w klasie ```SimpleFormViewController```, uruchom aplikację i spróbuj zmienić dane w ```UITextField```. Czy kod działa poprawnie?

* Spróbuj zmodyfikować kod tak aby wiązanie działało w obie strony (two way binding). Pamiętaj, że zmiany w ```UITextField``` powinny wpłynąć na wartości zmiennych w ```ViewModelu```.

<br>


Zadanie 2
-----------

<br>

Wybranie płci w kontrolerze segmentowym powinno zmieniać wartość `genderLabel`.
Wykorzystaj zmienne `genderIndex`, `formattedGender` oraz `gender` z `ViewModelu` do wykonania tego zadania.

* Zmodyfikuj metodę ```bindSegmentedControl()```, tak aby powiązać obustronnie kontroler segmentowy z odpowiednim Variable w viewModelu.

* W ```ViewModelu```, w metodzie ```setupObservables``` stwórz odpowiednie ```Observables```, które będą odpowiadały za zwrócenie poprawnej wartości dla wybranej płci.
    *  Najpierw zmapuj indeks dla wybranego segmentu na odpowiadający mu typ ```Gender``` i powiąż go ze zmienną ```gender```.
    * W kolejnym kroku zmapuj ```gender``` (wykorzystaj ```Extension```, który znajduje się w ```ViewModelu```) i powiąż go z ```formattedGender```. 

<br>


Zadanie 3
-----------

<br>

Zmiana daty urodzenia w `birthDatePicker` wpływa na wartość `birthLabel`, w wizytówce.
Wykorzystaj zmienną `birthDate` z `ViewModelu` do wykonania tego zadania.

* W kontrolerze zmodyfikuj metodę ```bindDatePicker()``` tak aby zmiana daty przez użytkownika wpłynęła na wartość wyświetlaną przez ```birthLabel```.
Skorzystaj przy mapowaniu z SimpleFormViewModel.dateFormatter.string

<br>


Zadanie 4
-----------

<br>

Wybranie przycisku `Clear Form` ma przywrócić pierwotny stan formularza.

* Zaimplementuj metodę ```bindUI()```, w której stworzysz subskrybcję dla zdarzenia naciśnięcia ```clearFormButton``` w przypadku której: 
    * do ```viewModel``` przypiszesz nowo stworzoną instancję ```SimpleFormViewModel```,
    * ponownie wywołasz wiązanie ```ViewModelu```.

<br>
