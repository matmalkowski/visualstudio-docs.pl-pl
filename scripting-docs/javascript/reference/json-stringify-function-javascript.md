---
title: JSON.stringify — funkcja (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- stringify method
ms.assetid: 0fafaf3b-c29b-46dc-b65b-ca223064a1d0
caps.latest.revision: 40
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3539bb003ed20a3ff7586e42466bf7c47165b83f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791677"
---
# <a name="jsonstringify-function-javascript"></a>JSON.stringify — Funkcja (JavaScript)
Konwertuje [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] wartość na ciąg języka JavaScript Object Notation (JSON).  
  
## <a name="syntax"></a>Składnia  
  
```  
  
JSON.stringify(  
value [, replacer] [, space])  
```  
  
## <a name="parameters"></a>Parametry  
 `value`  
 Wymagany. A [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] wartości zwykle obiektu lub tablicy, do skonwertowania.  
  
 `replacer`  
 Opcjonalny. Funkcja lub tablica przekształcająca wyniki.  
  
 Jeśli `replacer` jest to funkcja `JSON.stringify` wywołuje funkcję, przekazując klucz i wartość dla każdego elementu członkowskiego. Zamiast oryginalnej wartości jest używana wartość zwracana. Jeśli funkcja zwraca `undefined`, element członkowski jest wyłączone. Klucz dla obiektu głównego jest pustym ciągiem znaków: "".  
  
 Jeśli `replacer` jest tablicą, tylko członkowie kluczem będzie można przekonwertować wartości w tablicy. Kolejność, w której elementy członkowskie są konwertowane, jest taka sama jak kolejność kluczy w tablicy. `replacer` Tablicy jest ignorowany podczas `value` argument jest również tablicy.  
  
 `space`  
 Opcjonalny. Do tekstu JSON będącego zwracaną wartością dodaje znaki wcięcia, białe znaki i znaki podziału wiersza w celu ułatwienia odczytu.  
  
 Jeśli `space` jest pominięty, bez żadnych dodatkowych biały znak jest generowany tekst wartość zwracaną.  
  
 Jeśli `space` jest liczbą, tworzone jest wcięcie o określoną liczbę spacji na każdym poziomie tekstu wartość zwracaną. Jeśli `space` jest większa niż 10, tekst jest wcięta 10 spacji.  
  
 Jeśli `space` jest niepusty ciąg znaków, takich jak "\t" tworzone jest wcięcie tekstu wartość zwracaną z znaków w ciągu na każdym poziomie.  
  
 Jeśli `space` jest ciągiem, który jest dłuższa niż 10 znaków 10 pierwszych znaków są używane.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ciąg zawierający tekst JSON.  
  
## <a name="exceptions"></a>Wyjątki  
  
|Wyjątek|Warunek|  
|---------------|---------------|  
|[Nieprawidłowy argument zastępczy](../../javascript/misc/invalid-replacer-argument.md)|`replacer` Argument nie jest funkcją lub tablicy.|  
|[Odwołanie cykliczne w argumencie wartości nie jest obsługiwane.](../../javascript/misc/circular-reference-in-value-argument-not-supported.md)|`value` Argument zawiera odwołanie cykliczne.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `value` ma `toJSON` metody `JSON.stringify` funkcja używa wartość zwracaną przez tę metodę. Jeśli wartość zwracana `toJSON` jest metoda `undefined`, element członkowski nie jest konwertowany. Umożliwia to obiektowi ustalenie własnej reprezentacji JSON.  
  
 Wartości, które nie mają reprezentacje JSON, takich jak `undefined`, nie zostanie przekonwertowany. W obiektach zostaną usunięte. W tablicach zostaną zastąpione wartością null.  
  
 Wartości będące ciągami zaczynają się i kończą się znakiem cudzysłowu. Wszystkie znaki Unicode mogą być ujęte w znaki cudzysłowu, z wyjątkiem znaków, które muszą być poprzedzone znakiem ukośnika odwrotnego. Następujące znaki musi być poprzedzone znakiem ukośnika odwrotnego:  
  
-   Znak cudzysłowu (")  
  
-   Ukośnik odwrotny (\\)  
  
-   Backspace (b)  
  
-   Nowa strona (f)  
  
-   Nowy wiersz (n)  
  
-   Powrót karetki (r)  
  
-   Tabulator poziomy (t)  
  
-   Cztery cyfry szesnastkowe (uhhhh)  
  
## <a name="order-of-execution"></a>Kolejność wykonywania  
 Podczas serializacji Jeśli `toJSON` istnieje metoda dla `value` argumentu, `JSON.stringify` najpierw wywołuje `toJSON` metody. Jeśli nie istnieje, używana jest oryginalna wartość. Następny, jeśli `replacer` podano argumentu, wartość (oryginalnej wartości lub `toJSON` wartość zwracaną) zostanie zastąpiony wartość zwracaną z `replacer` argumentu. Na koniec białe znaki są dodawane do wartości, w oparciu o opcjonalny `space` argument do generowania końcowego tekst JSON.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `JSON.stringify` przekonwertować `contact` obiektu na tekst w formacie JSON. `memberfilter` Tablicy jest zdefiniowana, aby tylko `surname` i `phone` elementy członkowskie są konwertowane. `firstname` Element członkowski zostanie pominięty.  
  
```JavaScript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
var memberfilter = new Array();  
memberfilter[0] = "surname";  
memberfilter[1] = "phone";  
var jsonText = JSON.stringify(contact, memberfilter, "\t");  
document.write(jsonText);  
// Output:   
// { "surname": "Aaberg", "phone": [ "555-0100", "555-0120" ] }  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `JSON.stringify` z tablicą. `replaceToUpper` Funkcja konwertuje każdy ciąg znaków w tablicy na wielkie litery.  
  
```JavaScript  
var continents = new Array();  
continents[0] = "Europe";  
continents[1] = "Asia";  
continents[2] = "Australia";  
continents[3] = "Antarctica";  
continents[4] = "North America";  
continents[5] = "South America";  
continents[6] = "Africa";  
  
var jsonText = JSON.stringify(continents, replaceToUpper);  
  
function replaceToUpper(key, value) {  
    return value.toString().toUpperCase();  
}  
  
//Output:  
// "EUROPE,ASIA,AUSTRALIA,ANTARCTICA,NORTH AMERICA,SOUTH AMERICA,AFRICA"  
  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `toJSON` metodę, aby przekonwertować wartości ciągu na wielkie litery.  
  
```JavaScript  
var contact = new Object();   
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
contact.toJSON = function(key)  
 {  
    var replacement = new Object();  
    for (var val in this)  
    {  
        if (typeof (this[val]) === 'string')  
            replacement[val] = this[val].toUpperCase();  
        else  
            replacement[val] = this[val]  
    }  
    return replacement;  
};  
  
var jsonText = JSON.stringify(contact);  
document.write(jsonText);  
  
// Output:  
{"firstname":"JESPER","surname":"AABERG","phone":["555-0100","555-0120"]}  
  
'{"firstname":"JESPER","surname":"AABERG","phone":["555-0100","555-0120"]}'  
*/  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [JSON.Parse — funkcja](../../javascript/reference/json-parse-function-javascript.md)   
 [toJSON — metoda (Data)](../../javascript/reference/tojson-method-date-javascript.md)   
 [Czytnik źródła przykładowej aplikacji (w Sklepie Windows)](http://code.msdn.microsoft.com/Feed-reader-sample-99d68cf8)