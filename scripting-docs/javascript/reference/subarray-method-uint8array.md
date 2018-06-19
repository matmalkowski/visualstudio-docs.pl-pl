---
title: Metoda subarray (Uint8Array) | Dokumentacja firmy Microsoft
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
ms.assetid: 07724c80-5fdf-4745-a750-214630100439
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a972f2bb682c9a43a5671d457b8a1efc29d2af2a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791521"
---
# <a name="subarray-method-uint8array"></a>Metoda subarray (Uint8Array)
Pobiera nowy widok Uint8Array [arraybuffer — obiekt](../../javascript/reference/arraybuffer-object.md) magazynu dla tej tablicy, określając imię i nazwisko członkami subarray.  
  
## <a name="syntax"></a>Składnia  
  
```JavaScript  
var newUint8Array = uint8Array.subarray(begin, end);  
```  
  
## <a name="parameters"></a>Parametry  
 `newUint8Array`  
 Podtablica zwracana przez tę metodę.  
  
 `begin`  
 Indeks początku tablicy.  
  
 `end`  
 Indeks końca tablicy. Jest to wyłącznie.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli dowolny `begin` lub `end` jest ujemna, odnosi się do indeksu z końca tablicy, w przeciwieństwie do od początku. Jeśli `end` jest określony, subarray zawiera wszystkie elementy z `begin` do końca tablicy typu. Zakres określony przez `begin` i `end` wartości jest zablokowane za pomocą zakres prawidłowy indeks bieżącego tablicy. Jeśli obliczona długość nowej tablicy z kontrolą typów będzie ujemna, zostanie ona zablokowana na poziomie wartości zero. Zwracana tablica jest tego samego typu, co tablica, na której ta metoda jest wywoływana.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak uzyskać podtablicę o długości dwóch elementów, poczynając od pierwszego elementu tablicy.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var intArr = new Uint8Array(buffer.byteLength);  
            var subArr = intArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]