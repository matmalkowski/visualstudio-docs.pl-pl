---
title: Uint8ClampedArray — obiekt (JavaScript) | Dokumentacja firmy Microsoft
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
ms.assetid: 0c5537f7-00b4-487a-8fba-ef032e67e7bd
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51673eadc8eb905355bf136dc82b2f240462180a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24792166"
---
# <a name="uint8clampedarray-object-javascript"></a>Uint8ClampedArray — obiekt (JavaScript)
Tablica typu 8-bitowych liczb całkowitych bez znaku z wartościami zablokowane za pomocą do zakresu od 0 do 255. Zawartość jest inicjowana wartością 0. Jeśli nie można przydzielić żądanej liczby bajtów, zwracany jest wyjątek.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      uint8ClampedArray = new Uint8ClampedArray( length );  
uint8ClampedArray = new Uint8ClampedArray( array );  
uint8ClampedArray = new Uint8ClampedArray( buffer, byteOffset, length);  
```  
  
## <a name="parameters"></a>Parametry  
 `uint8ClampedArray`  
 Wymagany. Nazwa zmiennej, do której `Uint8ClampedArray` obiekt jest przypisany.  
  
 `length`  
 Opcjonalny. Liczba elementów w tablicy.  
  
 `array`  
 Opcjonalny. Tablica (lub typizowaną tablicę) zawierający tej tablicy. Zawartość są inicjowane zawartości podanej tablicy lub przekonwertować typizowaną tablicę z każdym elementem `Uint8` typu.  
  
 `buffer`  
 Opcjonalny. [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) który `Uint8ClampedArray` reprezentuje.  
  
 `byteOffset`  
 Opcjonalny. Przesunięcie, w bajtach, od początku buforze, od której `Uint8ClampedArray` należy rozpocząć.  
  
 `length`  
 Opcjonalny. Liczba elementów w tablicy.  
  
## <a name="remarks"></a>Uwagi  
 Wartości przechowywane w `Uint8ClampedArray` obiektu należą do zakresu od 0 do 255. Jeśli ustawisz wartość ujemną dla elementu członkowskiego tablicy 0 jest ustawiona wartość. Jeśli ustawisz wartość, która jest większa niż 255 255 jest ustawiona jako wartość.  
  
 Wartości w `Uint8ClampedArray` obiektu jest zaokrąglana do najbliższej parzystej wartości, która jest wywoływana, zaokrąglenie kwot.  
  
## <a name="constants"></a>Stałe  
 W poniższej tabeli wymieniono stałe `Uint8ClampedArray` obiektu.  
  
|Stała|Opis|  
|--------------|-----------------|  
|[Bytes_per_element — stała](../../javascript/reference/bytes-per-element-constant-uint8clampedarray.md)|Rozmiar w bajtach każdego elementu w tablicy.|  
  
## <a name="properties"></a>Właściwości  
 W poniższej tabeli wymieniono stałe `Uint8ClampedArray` obiektu.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|[Właściwość Buffer](../../javascript/reference/buffer-property-uint8clampedarray.md)|Tylko do odczytu. Pobiera [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) , do którego odwołuje tej tablicy.|  
|[byteLength właściwość](../../javascript/reference/bytelength-property-uint8clampedarray.md)|Tylko do odczytu. Długość tej tablicy, od początku jego [ArrayBuffer](../../javascript/reference/arraybuffer-object.md), w bajtach, jak określono w czasie tworzenia.|  
|[byteOffset właściwość](../../javascript/reference/byteoffset-property-uint8clampedarray.md)|Tylko do odczytu. Przesunięcie tej tablicy, od początku jego [ArrayBuffer](../../javascript/reference/arraybuffer-object.md), w bajtach, jak określono w czasie tworzenia.|  
|[length — właściwość](../../javascript/reference/length-property-uint8clampedarray.md)|Długość tablicy.|  
  
## <a name="methods"></a>Metody  
 W poniższej tabeli przedstawiono metody `Uint8ClampedArray` obiektu.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[set — metoda](../../javascript/reference/set-method-uint8clampedarray.md)|Ustaw wartość lub tablicę wartości.|  
|[Metoda subarray](../../javascript/reference/subarray-method-uint8clampedarray.md)|Pobiera nową `Uint8ClampedArray` widoku [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) magazynu dla tej tablicy, określając imię i nazwisko elementy subarray.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `Uint8ClampedArray` obiektu do przetwarzania danych binarnych z `XmlHttpRequest`:  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Uint8ClampedArray(buffer.byteLength);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getUint8(i);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak wartości są ograniczone w `Uint8ClampedArray`.  
  
```JavaScript  
var ints = new Uint8ClampedArray(2);  
ints[0] = -1;  // 0 will be assigned.  
ints[1] = 256; // 255 will be assigned.  
  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak wartości są zaokrąglane w `Uint8ClampedArray`.  
  
```  
var ints = new Uint8ClampedArray(4);  
ints[0] = 11.3; // 11 will be assigned (same as Int8Array).  
ints[1] = 11.8; // 12 will be assigned (same as Int8Array).  
ints[2] = 10.5; // 10 will be assigned (rounded to the nearest   
                // even value).  
ints[3] = 11.5; // 12 will be assigned (rounded to the nearest   
                // even value).  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Uint8array — obiekt](../../javascript/reference/uint8array-object.md)   
 [Arraybuffer — obiekt](../../javascript/reference/arraybuffer-object.md)
