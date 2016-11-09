---
layout: page
title: Requests
permalink: /Requests/
---

<br>

Zadanie 1
------------

<br>

* Przerób wyszukiwanie w FeedViewController aby odbywało sie po każdej wpisanej literce.
 <br> 

*  Wyszukiwanie ma rozpocząć sie nie wcześniej niż 300ms po wpisaniu znaku. 
 <br>
 
*  Ignorujemy wpisanie i skasowanie tej samej frazy
 <br>
 
* Wyszukiwanie ma rozpocząć sie dopiero od 3-ciego wpisanego znaku
 <br>
 
*  Użyj do tego RxSwifta oraz property rx_text z search bara



<br>

Zadanie 2
-----------

<br>

* Utwórz PlayerCellViewModel z nastepujacymi polami typu Variable: <br>

	* nazwa
	* wykonawca
	* album obecnie odtwarzanej piosenki
	* track 



* Stwórz konstruktor i ustaw wartości dla poszczególnych variable na podstawie przekazanego obieku Track. 
<br>

* W PlayerTableViewCell utwórz property typu PlayerCellViewModel. 
<br>

* Utwórz disposeBag. 
<br>

* Napisz metodę ktora tworzy nowy disposeBag oraz binduje informacje z viewModelu z poszczególnymi labelkami. W momencie ustawiania viewModelu wywołaj ta metodę. 
<br>

* Nadpisz metodę prepareForReuse i ustaw disposeBag na nil