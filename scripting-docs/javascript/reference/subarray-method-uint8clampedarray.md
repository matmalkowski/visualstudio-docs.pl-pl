---
title: "subarray (Uint8ClampedArray) — metoda | Dokumentacja firmy Microsoft"
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
ms.assetid: 309ed9e8-5805-47ab-b3ed-501cae1323dd
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 76cda8b123b02b4c19a7fd162f3bfbce4540d149
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="subarray-method-uint8clampedarray"></a>subarray (Uint8ClampedArray) — metoda
Pobiera nową [Uint8ClampedArray](../../javascript/reference/uint8array-object.md) widoku [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) magazynu dla tej tablicy, określając imię i nazwisko członkami subarray.  
  
## <a name="syntax"></a>Składnia  
  
```JavaScript  
var newUint8ClampedArray = uint8ClampedArray.subarray(begin, end);  
```  
  
## <a name="parameters"></a>Parametry  
 `newUint8ClampedArray`  
 Wymagany. Podtablica zwracana przez tę metodę.  
  
 `begin`  
 Opcjonalny. Indeks początku tablicy.  
  
 `end`  
 Opcjonalny. Indeks końca tablicy. Jest to wyłącznie.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli dowolny `begin` lub `end` jest ujemna, odnosi się do indeksu z końca tablicy, w przeciwieństwie do od początku. Jeśli `end` jest określony, subarray zawiera wszystkie elementy z `begin` do końca tablicy typu. Zakres określony przez `begin` i `end` wartości jest zablokowane za pomocą zakres prawidłowy indeks bieżącego tablicy. Jeśli obliczona długość nowej tablicy z kontrolą typów będzie ujemna, zostanie ona zablokowana na poziomie wartości zero. Zwracana tablica ma ten sam typ co tablica, na którym ta metoda jest wywoływana.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia, jak uzyskać podtablicę o długości dwóch elementów, poczynając od pierwszego elementu tablicy.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var intArr = new Uint8ClampedArray(buffer.byteLength);  
            var subArr = intArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Uint8array — obiekt](../../javascript/reference/uint8array-object.md)   
 [Arraybuffer — obiekt](../../javascript/reference/arraybuffer-object.md)   
 [Obiekt Uint8ClampedArray](../../javascript/reference/uint8clampedarray-object-javascript.md)