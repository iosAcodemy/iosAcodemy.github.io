---
layout: page
title: Networking
permalink: /networking/
---

Zadanie 1
----------
<br>

Plik *Api.Swift*  - w enum `Endpoint` brakuje obsługi 2 przypadków:

* Track(id: String)
* Tracks(ids:[String])

uzupełnij je następującymi wartościami:

* dla Track(id: String)
  * path: "tracks/\(id)/"


* dla Tracks(ids:[String])
  * path: "tracks/"
  * parameters: ids.encoded
  * rootKeyPath: "tracks"

<br>

Zadanie 2
----------

<br>

* W pliku *Api.Swift* uzupełnij ciało metody ```absoluteURL(endpoint: Endpoint) -> NSURL?```, która zwraca obiekt NSURL na podstawie przekazanego argumentu `endpoint` oraz `API.baseURL`.

* Zwracany obiekt `NSURL` musi zawierać wartości z `endpoint.parameters`. Wykorzystaj do tego celu `NSURLComponents` oraz `NSURLQueryItem`.

<br>

Zadanie 3
----------

<br>

W pliku *Api.Swift* uzpełnij ciało metody `request()`.

* Stwórz NSURL request z wykorzystaniem zaimplementowanej wcześniej metody `absoluteURL()`.

* Wykorzystaj istniejący obiekt `session`, do stworzenia tasku użyj metody:
```dataTaskWithRequest(request: NSURLRequest, completionHandler: (NSData?, NSURLResponse?, NSError?) -> Void) -> NSURLSessionDataTask```.

* Obsłuż response uwzględniając przypadki:
  * pełna serializacja danych zwróconych przez API
  * błędna serializacja danych zwróconych przez API


* Do parsowania błędów zwróconych przez API użyj metody ```createNSErrorFromJson(json: JSON?) -> NSError?```

<br>

Zadanie 4
----------

<br>

* Wykorzystując protokół JSONDecodable, zaimplementuj brakującą metodę `decodeJSONObject(object: AnyObject) throws` dla obiektu `Track`.

* Wykorzystaj istniejące pola struktury Track oraz opis obiektu JSON dostępnego w dokumentacji pod adresem:
<br>
*https://developer.spotify.com/web-api/get-albums-tracks/*
