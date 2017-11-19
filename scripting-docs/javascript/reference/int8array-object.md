---
title: "Int8array — obiekt | Dokumentacja firmy Microsoft"
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
ms.assetid: 0e3bdbc5-8d85-4c0d-b399-693b01674803
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7e3f85a505f41f2909330e938f4978433fc823f9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="int8array-object"></a>Int8Array — Obiekt
Tablica z kontrolą typów 8-bitowych wartości całkowitych. Zawartość jest inicjowana wartością 0. Jeśli żądanej liczby bajtów nie można przydzielić, zgłaszany jest wyjątek.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      int8Array = new Int8Array( length );  
intArray = new Int8Array( array );  
intArray = new Int8Array( buffer, byteOffset, length);  
```  
  
## <a name="parameters"></a>Parametry  
 `int8Array`  
 Wymagany. Nazwa zmiennej, do której `Int8Array` obiekt jest przypisany.  
  
 `length`  
 Określa liczbę elementów w tablicy.  
  
 `array`  
 Tablica (lub tablica z kontrolą typów) zawarta w tej tablicy. Zawartości są inicjowane do zawartości danej tablicy lub tablicy z kontrolą typów, przy czym każdy element jest konwertowanym na typ Int8.  
  
 `buffer`  
 ArrayBuffer, który reprezentuje obiekt Int8Array.  
  
 `byteOffset`  
 Opcjonalny. Określa przesunięcie w bajtach od początku buforu, w którym powinien się zacząć Int8Array.  
  
 `length`  
 Liczba elementów w tablicy.  
  
## <a name="constants"></a>Stałe  
 W poniższej tabeli wymieniono stałe `Int8Array`obiektu.  
  
|Stała|Opis|  
|--------------|-----------------|  
|[Bytes_per_element — stała](../../javascript/reference/bytes-per-element-constant-int8array.md)|Rozmiar w bajtach każdego elementu w tablicy.|  
  
## <a name="properties"></a>Właściwości  
 W poniższej tabeli wymieniono stałe `Int8Array`obiektu.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|[Właściwość Buffer](../../javascript/reference/buffer-property-int8array.md)|Tylko do odczytu. Pobiera ArrayBuffer, do którego odwołuje się ta tablica.|  
|[byteLength właściwość](../../javascript/reference/bytelength-property-int8array.md)|Tylko do odczytu. Ustalona podczas tworzenia długość (w bajtach) tej tablicy od początku jej ArrayBuffer.|  
|[byteOffset właściwość](../../javascript/reference/byteoffset-property-int8array.md)|Tylko do odczytu. Ustalone podczas tworzenia przesunięcie (w bajtach) tej tablicy od początku jej ArrayBuffer.|  
|[length — właściwość](../../javascript/reference/length-property-int8array.md)|Długość tablicy.|  
  
## <a name="methods"></a>Metody  
 W poniższej tabeli przedstawiono metody `Int8Array`obiektu.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Metoda Set (Int8Array)](../../javascript/reference/set-method-int8array.md)|Ustaw wartość lub tablicę wartości.|  
|[Metoda subarray (Int8Array)](../../javascript/reference/subarray-method-int8array.md)|Pobiera nowy widok Int8Array magazynu ArrayBuffer dla tej tablicy.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia, jak używać obiektu Int8Array do przetwarzania danych binarnych uzyskanych z XmlHttpRequest:  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Int8Array(buffer.byteLength);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt8(i);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]