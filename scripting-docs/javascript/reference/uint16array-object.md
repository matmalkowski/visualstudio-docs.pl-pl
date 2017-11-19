---
title: "Uint16array — obiekt | Dokumentacja firmy Microsoft"
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
ms.assetid: e684647d-04d0-41a9-9089-16612e18ec7d
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 447c0509a29f1696e0204d6f37ff88d3c0bdecae
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="uint16array-object"></a>Uint16Array — Obiekt
Typizowaną tablicę wartości 16-bitową liczbę całkowitą bez znaku. Zawartość jest inicjowana wartością 0. Jeśli żądanej liczby bajtów nie można przydzielić, zgłaszany jest wyjątek.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      uint16Array = new Uint16Array( length );  
uint16Array = new Uint16Array( array );  
uint16Array = new Uint16Array( buffer, byteOffset, length );  
```  
  
## <a name="parameters"></a>Parametry  
 `uint16Array`  
 Wymagany. Nazwa zmiennej, do której **Uint16Array** obiekt jest przypisany.  
  
 `length`  
 Określa liczbę elementów w tablicy.  
  
 `array`  
 Tablica (lub tablica z kontrolą typów) zawarta w tej tablicy. Zawartości są inicjowane do zawartości danej tablicy lub tablicy z kontrolą typów, przy czym każdy element jest konwertowanym na typ Uint16.  
  
 `buffer`  
 ArrayBuffer, który reprezentuje obiekt Uint16Array.  
  
 `byteOffset`  
 Opcjonalny. Określa przesunięcie w bajtach od początku buforu wskazujące miejsce, w którym ma się zacząć Uint16Array.  
  
 `length`  
 Liczba elementów w tablicy.  
  
## <a name="constants"></a>Stałe  
 W poniższej tabeli wymieniono stałe `Uint16Array`obiektu.  
  
|Stała|Opis|  
|--------------|-----------------|  
|[Bytes_per_element — stała](../../javascript/reference/bytes-per-element-constant-uint16array.md)|Rozmiar w bajtach każdego elementu w tablicy.|  
  
## <a name="properties"></a>Właściwości  
 W poniższej tabeli wymieniono stałe `Uint16Array`obiektu.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|[Właściwość Buffer](../../javascript/reference/buffer-property-uint16array.md)|Tylko do odczytu. Pobiera ArrayBuffer, do którego odwołuje się ta tablica.|  
|[byteLength właściwość](../../javascript/reference/bytelength-property-uint16array.md)|Tylko do odczytu. Ustalona podczas tworzenia długość (w bajtach) tej tablicy od początku jej ArrayBuffer.|  
|[byteOffset właściwość](../../javascript/reference/byteoffset-property-uint16array.md)|Tylko do odczytu. Ustalone podczas tworzenia przesunięcie (w bajtach) tej tablicy od początku jej ArrayBuffer.|  
|[length — właściwość](../../javascript/reference/length-property-uint16array.md)|Długość tablicy.|  
|||  
  
## <a name="methods"></a>Metody  
 W poniższej tabeli przedstawiono metody `Uint16Array`obiektu.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Metoda Set (Uint16Array)](../../javascript/reference/set-method-uint16array.md)|Ustaw wartość lub tablicę wartości.|  
|[Metoda subarray (Uint16Array)](../../javascript/reference/subarray-method-uint16array.md)|Pobiera nowy widok Uint16Array magazynu ArrayBuffer dla tej tablicy.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia, jak używać obiektu Uint16Array do przetwarzania danych binarnych uzyskanych z XmlHttpRequest:  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Uint16Array(buffer.byteLength / 2);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getUint16(i * 2);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]