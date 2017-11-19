---
title: "Float64array — obiekt | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 74c945dc-56ae-458c-b0aa-782f240e9b6c
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20544812d94c1234d85d714f6e469d0de4f4c5ab
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="float64array-object"></a>Float64Array — Obiekt
Typizowaną tablicę wartości 64-bitowych liczb zmiennoprzecinkowych. Zawartość jest inicjowana wartością 0. Jeśli żądanej liczby bajtów nie można przydzielić, zgłaszany jest wyjątek.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      float64Array = new Float64Array( length );  
float64Array = new Float64Array( array );  
float64Array = new Float64Array( buffer, byteOffset, length);  
```  
  
## <a name="parameters"></a>Parametry  
 `float64Array`  
 Wymagany. Nazwa zmiennej, do której **Float64Array** obiekt jest przypisany.  
  
 `length`  
 Określa liczbę elementów w tablicy.  
  
 `array`  
 Tablica (lub tablica z kontrolą typów) zawarta w tej tablicy. Zawartości są inicjowane do zawartości danej tablicy lub tablicy z kontrolą typów, a każdy element jest konwertowany na typ Float64.  
  
 `buffer`  
 ArrayBuffer, który reprezentuje obiekt Float64Array.  
  
 `byteOffset`  
 Opcjonalny. Określa przesunięcie w bajtach od początku buforu oznaczające miejsce, w którym powinna zacząć się tablica Float64Array.  
  
 `length`  
 Liczba elementów w tablicy.  
  
## <a name="constants"></a>Stałe  
 W poniższej tabeli wymieniono stałe `Float64Array`obiektu.  
  
|Stała|Opis|  
|--------------|-----------------|  
|[Bytes_per_element — stała](../../javascript/reference/bytes-per-element-constant-float64array.md)|Rozmiar w bajtach każdego elementu w tablicy.|  
  
## <a name="properties"></a>Właściwości  
 W poniższej tabeli wymieniono stałe `Float64Array`obiektu.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|[Właściwość Buffer](../../javascript/reference/bytelength-property-float64array.md)|Tylko do odczytu. Pobiera ArrayBuffer, do którego odwołuje się ta tablica.|  
|[byteLength właściwość](../../javascript/reference/bytelength-property-float64array.md)|Tylko do odczytu. Ustalona podczas tworzenia długość (w bajtach) tej tablicy od początku jej ArrayBuffer.|  
|[byteOffset właściwość](../../javascript/reference/length-property-float64array.md)|Tylko do odczytu. Ustalone podczas tworzenia przesunięcie (w bajtach) tej tablicy od początku jej ArrayBuffer.|  
|[length — właściwość](../../javascript/reference/length-property-float64array.md)|Długość tablicy.|  
  
## <a name="methods"></a>Metody  
 W poniższej tabeli przedstawiono metody `Float64Array`obiektu.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GET, metoda](../../javascript/reference/get-method-float64array.md)|Pomijalne. Pobiera element wskazywany przez określony indeks.|  
|[Metoda Set (Float64Array)](../../javascript/reference/set-method-float64array.md)|Ustaw wartość lub tablicę wartości.|  
|[Metoda subarray (Float64Array)](../../javascript/reference/subarray-method-float64array.md)|Pobiera nowy widok Float64Array magazynu ArrayBuffer dla tej tablicy.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia, jak używać obiektu Float64Array do przetwarzania danych binarnych uzyskanych z XmlHttpRequest:  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Float64Array(buffer.byteLength / 8);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getFloat64(i * 8);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]