---
title: "Int32array — obiekt | Dokumentacja firmy Microsoft"
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
ms.assetid: 48696299-e41e-4590-b1b5-26fe19f68139
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 64e37564d4b4ffd336a83285818e90262f32040a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="int32array-object"></a>Int32Array — Obiekt
Typizowaną tablicę wartości 32-bitową liczbę całkowitą. Zawartość jest inicjowana wartością 0. Jeśli żądanej liczby bajtów nie można przydzielić, zgłaszany jest wyjątek.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      int32Array = new Int32Array( length );  
int32Array = new Int32Array( array );  
int32Array = new Int32Array( buffer, byteOffset, length);  
```  
  
## <a name="parameters"></a>Parametry  
 `int32Array`  
 Wymagany. Nazwa zmiennej, do której **Int32Array** obiekt jest przypisany.  
  
 `length`  
 Określa liczbę elementów w tablicy.  
  
 `array`  
 Tablica (lub tablica z kontrolą typów) zawarta w tej tablicy. Zawartość jest inicjowana do zawartości danej tablicy lub tablicy z kontrolą typów, przy czym każdy element jest konwertowanym na typ Int32.  
  
 `buffer`  
 ArrayBuffer, który reprezentuje obiekt Int32Array.  
  
 `byteOffset`  
 Opcjonalny. Określa przesunięcie w bajtach od początku buforu wskazujące miejsce, w którym ma się zacząć Int32Array.  
  
 `length`  
 Liczba elementów w tablicy.  
  
## <a name="constants"></a>Stałe  
 W poniższej tabeli wymieniono stałe `Int32Array`obiektu.  
  
|Stała|Opis|  
|--------------|-----------------|  
|[Bytes_per_element — stała](../../javascript/reference/bytes-per-element-constant-int32array.md)|Rozmiar w bajtach każdego elementu w tablicy.|  
  
## <a name="properties"></a>Właściwości  
 W poniższej tabeli wymieniono stałe `Int32Array`obiektu.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|[Właściwość Buffer](../../javascript/reference/buffer-property-int32array.md)|Tylko do odczytu. Pobiera ArrayBuffer, do którego odwołuje się ta tablica.|  
|[byteLength właściwość](../../javascript/reference/bytelength-property-int32array.md)|Tylko do odczytu. Ustalona podczas tworzenia długość (w bajtach) tej tablicy od początku jej ArrayBuffer.|  
|[byteOffset właściwość](../../javascript/reference/byteoffset-property-int32array.md)|Tylko do odczytu. Ustalone podczas tworzenia przesunięcie (w bajtach) tej tablicy od początku jej ArrayBuffer.|  
|[length — właściwość](../../javascript/reference/length-property-int32array.md)|Długość tablicy.|  
  
## <a name="methods"></a>Metody  
 W poniższej tabeli przedstawiono metody `Int32Array`obiektu.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Metoda Set (Int32Array)](../../javascript/reference/set-method-int32array.md)|Ustaw wartość lub tablicę wartości.|  
|[Metoda subarray (Int32Array)](../../javascript/reference/subarray-method-int32array.md)|Pobiera nowy widok Int32Array magazynu ArrayBuffer dla tej tablicy.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia, jak używać obiektu Int32Array do przetwarzania danych binarnych uzyskanych z XmlHttpRequest:  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Int32Array(buffer.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt32(i * 4);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]