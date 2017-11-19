---
title: "Uint8array — obiekt | Dokumentacja firmy Microsoft"
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
ms.assetid: ae78b3ee-b660-4625-ac7b-d414a0842c87
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 72002af4ca92d1104a3c3c3bb2339e63856a80a6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="uint8array-object"></a>Uint8Array — Obiekt
Tablica wartości 8-bitowych liczb całkowitych bez znaku. Zawartość jest inicjowana wartością 0. Jeśli żądanej liczby bajtów nie można przydzielić, zgłaszany jest wyjątek.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      uint8Array = new Uint8Array( length );  
uint8Array = new Uint8Array( array );  
uint8Array = new Uint8Array( buffer, byteOffset, length);  
```  
  
## <a name="parameters"></a>Parametry  
 `uint8Array`  
 Wymagany. Nazwa zmiennej, do której **Uint8Array** obiekt jest przypisany.  
  
 `length`  
 Określa liczbę elementów w tablicy.  
  
 `array`  
 Tablica (lub tablica z kontrolą typów) zawarta w tej tablicy. Zawartości są inicjowane do zawartości danej tablicy lub tablicy z kontrolą typów, przy czym każdy element jest konwertowanym na typ Uint8.  
  
 `buffer`  
 ArrayBuffer, który reprezentuje obiekt Uint8Array.  
  
 `byteOffset`  
 Opcjonalny. Określa przesunięcie w bajtach od początku buforu wskazujące miejsce, w którym ma się zacząć Uint8Array.  
  
 `length`  
 Liczba elementów w tablicy.  
  
## <a name="constants"></a>Stałe  
 W poniższej tabeli wymieniono stałe `Uint8Array`obiektu.  
  
|Stała|Opis|  
|--------------|-----------------|  
|[Bytes_per_element — stała](../../javascript/reference/bytes-per-element-constant-uint8array.md)|Rozmiar w bajtach każdego elementu w tablicy.|  
  
## <a name="properties"></a>Właściwości  
 W poniższej tabeli wymieniono stałe `Uint8Array`obiektu.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|[Właściwość Buffer](../../javascript/reference/buffer-property-uint8array.md)|Tylko do odczytu. Pobiera ArrayBuffer, do którego odwołuje się ta tablica.|  
|[byteLength właściwość](../../javascript/reference/bytelength-property-uint8array.md)|Tylko do odczytu. Ustalona podczas tworzenia długość (w bajtach) tej tablicy od początku jej ArrayBuffer.|  
|[byteOffset właściwość](../../javascript/reference/byteoffset-property-uint8array.md)|Tylko do odczytu. Ustalone podczas tworzenia przesunięcie (w bajtach) tej tablicy od początku jej ArrayBuffer.|  
|[length — właściwość](../../javascript/reference/length-property-uint8array.md)|Długość tablicy.|  
|||  
  
## <a name="methods"></a>Metody  
 W poniższej tabeli przedstawiono metody `Uint8Array`obiektu.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Metoda Set (Uint8Array)](../../javascript/reference/set-method-uint8array.md)|Ustaw wartość lub tablicę wartości.|  
|[Metoda subarray (Uint8Array)](../../javascript/reference/subarray-method-uint8array.md)|Pobiera nowy widok Uint8Array magazynu ArrayBuffer dla tej tablicy.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia, jak używać obiektu Uint8Array do przetwarzania danych binarnych uzyskanych z XmlHttpRequest:  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Uint8Array(buffer.byteLength);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getUint8(i);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]