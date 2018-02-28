---
title: "JSON.Parse — funkcja (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- JSON.parse
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- parse JSON method
- JSON.parse method
ms.assetid: 20f00d31-5ab5-4c3c-ab49-2534fc39a9b4
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 519fc733fd42a194fbd7335127ddf9bcf0bdc220
ms.sourcegitcommit: 11740fed01cc602252ef698aaa11c07987b00570
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2018
---
# <a name="jsonparse-function-javascript"></a>JSON.parse — Funkcja (JavaScript)
Konwertuje ciąg JSON na obiekt.  
  
## <a name="syntax"></a>Składnia  
  
```  
JSON.parse(text [, reviver])  
```  
  
## <a name="parameters"></a>Parametry  
 `text`  
 Wymagany. Prawidłowy ciąg JSON.  
  
 `reviver`  
 Opcjonalny. Funkcja, która przekształca wyniki. Ta funkcja jest wywoływana dla każdego elementu członkowskiego obiektu. Jeśli element członkowski zawiera obiekty zagnieżdżone, są one transformowane przed obiektem nadrzędnym. Dla każdego elementu członkowskiego, mają miejsce następujące zdarzenia:  
  
-   Jeśli `reviver` zwraca prawidłową wartość elementu członkowskiego jest zastępowany Przekształconą wartość.  
  
-   Jeśli `reviver` zwraca tę samą wartość otrzymał, wartość elementu członkowskiego nie jest modyfikowany.  
  
-   Jeśli `reviver` zwraca `null` lub `undefined`, członek zostanie usunięty.  
  
## <a name="return-value"></a>Wartość zwracana  
 Obiekt lub tablica.  
  
## <a name="exceptions"></a>Wyjątki  
 Jeśli ta funkcja powoduje, że [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Błąd analizatora (takich jak "SCRIPT1014: nieprawidłowy znak"), tekst wejściowy nie jest zgodne z składni JSON. Aby poprawić ten błąd, wykonaj jedną z następujących czynności:  
  
-   Modyfikowanie `text` argumentu w celu zapewnienia przestrzegania składni JSON. Aby uzyskać więcej informacji, zobacz [Notacja składni BNF](http://go.microsoft.com/fwlink/?LinkId=125203) obiektów JSON.  
  
     Na przykład, jeśli odpowiedź jest w formacie JSONP zamiast czystego JSON, wypróbuj następujący kod na obiekcie odpowiedzi:  
  
    ```JavaScript  
    var fixedResponse = response.responseText.replace(/\\'/g, "'");  
    var jsonObj = JSON.parse(fixedResponse);  
    ```  
  
-   Upewnij się, że `text` argument był serializowany przez zgodne JSON implementacji takich jak `JSON.stringify`.  
  
-   Uruchom `text` argumentu w moduł weryfikacji JSON, takich jak [JSLint](http://www.jslint.com/) lub [JSON do pliku CSV](https://json-csv.com) zidentyfikować błędy składniowe.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `JSON.parse` do przekonwertowania ciągu JSON do obiektu.  
  
```JavaScript  
var jsontext = '{"firstname":"Jesper","surname":"Aaberg","phone":["555-0100","555-0120"]}';  
var contact = JSON.parse(jsontext);  
document.write(contact.surname + ", " + contact.firstname);  
document.write(contact.phone[1]);  
// Output:  
// Aaberg, Jesper  
// 555-0100  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład konwertuje tablicę do ciągu JSON przy użyciu `JSON.stringify`, a następnie konwertuje ciąg na powrót do tablicy przy użyciu `JSON.parse`.  
  
```JavaScript  
var arr = ["a", "b", "c"];  
var str = JSON.stringify(arr);  
document.write(str);  
document.write ("<br/>");  
  
var newArr = JSON.parse(str);  
  
while (newArr.length > 0) {  
    document.write(newArr.pop() + "<br/>");  
}  
  
// Output:  
// ["a","b","c"]  
// c  
// b  
// a  
```  
  
## <a name="example"></a>Przykład  
 `reviver` Funkcja jest często używany do przekształcania reprezentacja JSON Międzynarodowej Organizacji Normalizacyjnej (ISO) ciągów daty w formacie uniwersalnego czasu koordynowanego (UTC) `Date` obiektów. W tym przykładzie użyto `JSON.parse` do deserializacji ciągu na datę w formacie ISO. `dateReviver` Funkcja zwraca `Date` obiektów dla elementów członkowskich, które są sformatowane, takich jak ISO ciągi daty.  
  
```JavaScript  
var jsontext = '{ "hiredate": "2008-01-01T12:00:00Z", "birthdate": "2008-12-25T12:00:00Z" }';  
var dates = JSON.parse(jsontext, dateReviver);  
document.write(dates.birthdate.toUTCString());  
  
function dateReviver(key, value) {  
    var a;  
    if (typeof value === 'string') {  
        a = /^(\d{4})-(\d{2})-(\d{2})T(\d{2}):(\d{2}):(\d{2}(?:\.\d*)?)Z$/.exec(value);  
        if (a) {  
            return new Date(Date.UTC(+a[1], +a[2] - 1, +a[3], +a[4],  
                            +a[5], +a[6]));  
        }  
    }  
    return value;  
};  
  
// Output:  
// Thu, 25 Dec 2008 12:00:00 UTC  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcja JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md)   
 [toJSON — metoda (Data)](../../javascript/reference/tojson-method-date-javascript.md)   
 [Koncentrator szablonu przykładowej aplikacji (w Sklepie Windows)](http://code.msdn.microsoft.com/Hub-template-sample-with-4b70002d)