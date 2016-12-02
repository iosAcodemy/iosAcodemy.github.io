---
layout: page
title: Validations
permalink: /Validations/
---

<br>

W tym ćwiczeniu nauczysz się tworzyć prostą walidację formularzy. Uruchom apilikację i wybierz `Form Validation` - twoim zadaniem będzie implementacja walidacji dla trzech pól `UITextField` i dopiero po pozytywnej ich walidacji aktywacja przycisku `Sign Up`.
Spójrz na metodę ```setupUI()``` w klasie `FormValidationViewController` - są tam początkowo ukrywane trzy etykiety, które mają poinformować użytkownika o tym czy w poprawny sposób wpisuje dane w formularzu. Na potrzeby tego ćwiczenia ustalimy, że pole `Username` musi zawierać co najmniej 5 znaków, pole `Password` co najmniej 6 znaków, a pole `Retype password` musi być takie samo jak `Password`.

<br>

Zadanie 1
----------
<br>

W pliku `SignupViewModel` dodaj 3 pola typu trzy `Variable` dla typu `String`? :

* username
* password
* retypedPassword

W metodzie `bindViewModel()` znajdującej się w kontrolerze stwórz wiązanie w dwie strony pomiędzy:

* `usernameTextField` w kontrolerze, a `username` w ViewModelu
* `passwordTextField` w kontrolerze, a `password` w ViewModelu
* `retypedPasswordTextField` w kontrolerze, a `retypedPassword` w ViewModelu

<br>

Zadanie 2
----------
<br>

Spróbuj teraz zrobić to samo, ale przy użyciu niestandardowego infiksu (custom infix). Impelmentacja operatora `<->` znajduje się w pliku `RxUtils`.

<br>


Zadanie 3
----------
<br>

Wprowadzanie przez użytkownika danych w formularzu powinno skutkować wyświetleniem mu odpowiedniego komunikatu jeżeli nie przeszłym pomyślnie walidacji.

<br>

Zadanie 3a
----------
<br>

Pierwsza część zadania polega na stworzeniu mechanizmu walidacji dla pola `Password`. 

* W pliku `ValidationService` zaimplementuj regułę dla `validatePassword(_ password: String)`, która zwróci `ValidationResult`. 
* Przyjmij, że hasło musi się składać z co najmniej 6 znaków.
* W przypadku poprawnej walidacji zwrócona jest wartość `valid`
* Jeżeli warunek nie zostanie spełniony metoda ma zwrócić `invalid` i wiadomość "Password should have at least 6 characters."

<br>

Zadanie 3b
----------
<br>

Przejdź do `ViewModelu` i na wzór `usernameValidation` dodaj tam trzy lazy property typu `Observable` dla typu `ValidationResult`:

* passwordValidation
  * Z użyciem metody `validatePassword()`.
* passwordValidationSignal
  * Powinien filtrować wartości typu `ValidationResult` emitowane przez `passwordValidation` i sprawdzać czy są równe `valid`. Użyj do tego operatora ==, który został przeciążony w `extension` klasy `ValidationResult`.
  * Taki zabieg pozwoli uninąć sytuacji, w której dla obu pól odpowiadających za walidacje haseł zwrócona zostałaby wartość `true`, mimo że obydwa pola zwróciłyby `invalid`.
* retypedPasswordValidation
  * Zwróć `Observable`, które będzie połączeniem dwóch `Observable` - `password` i `retypedPassword` i użyj tego `Observable` w metodzie `validateSecondPassword(_ password: String?, secondPassword: String?) -> ValidationResult` (pomocna będzie metoda `combineLatest`).
  * Żeby upewnić się, że emitowane będą tylko prawidłowe elementy wykorzystaj metodę `skipUntil`, której w argumencie przekażesz wcześniej zaimplementowaną zmienną `passwordValidationSignal`.

<br>

Zadanie 3c
----------
<br>

Wróć do `FormValidationViewController` i zmodyfikuj metodę `bindValidationResultToUI(_ result: Observable<ValidationResult>, label: UILabel)`.

* Najpierw zmapuj `shared`, tak aby w przypadku gdy pole nie jest wypełnione poprawnie zwracana była boolowska wartość i powiązana została z właściwością `isHidden` etykiety.
* Następnie stwórz nowe mapowanie `shared`, aby w przypadku nieprawidłowo wypełnionego pola zwracany był opis błędu i powiąż go z właściwością `text` etykiety.

<br>

Zadanie 3d
----------
<br>

Wykorzystaj przed chwilą zmodyfikowany kod w metodzie `bindViewModel()`, aby powiązać ze sobą:

* `usernameValidation` z ViewModelu, z `usernameValidationLabel`
* `passwordValidation` z ViewModelu, z `passwordValidationLabel`
* `retypedPasswordValidation` z ViewModelu, z `retypedPasswordValidationLabel`

Gotowe! Sprawdź teraz jak w zależności od wprowadzanych danych zachowują się etykiety w formularzu.

<br>

Zadanie 4
----------
<br>

Kiedy użytkownik wprowadzi wszystkie dane poprawnie, przycisk `Sign up` powinien zostać włączony.

* W kontrolerze, w metodzie `bindViewModel()` zdefiniuj zmienną `registerEnabled` typu `Observable<Bool>`.
  * Ma połączyć w sobie trzy sekwencje z ViewModelu - `usernameValidation`, `passwordValidation` i `retypedPasswordValidation`. 
  * Jeżeli, każda z nich jest typu `valid`, to ma zwrócić true.
* Powiąż `registerEnabled` z właściwością `rx_validation` `registerButton`, zaczynając od wartości false (startWith).

Uruchom program jeszcze raz.

<br>


Zadanie 5
----------
<br>

Tak jak w poprzednim ćwiczeniu zaimplementuj zachowanie dla `Clear Form`.

* W metodzie `bindUI()` stwórz subskrypcję dla zdarzenia naciśnięcia ```clearFormButton```, która spowoduje wyczyszczenie formularza.
* Użyj metody `clearForm()` z `viewModelu`.

<br>

Przybij sobie piąteczkę - job well done ;)
