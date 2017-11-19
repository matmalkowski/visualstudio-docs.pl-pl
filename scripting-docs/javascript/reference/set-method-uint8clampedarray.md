---
title: "set — metoda (Uint8ClampedArray) | Dokumentacja firmy Microsoft"
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
ms.assetid: 1298443d-5c4c-4329-9ad2-35e213dca157
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed7635559e615746c577560f1a9266b26acd959d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="set-method-uint8clampedarray"></a>set — metoda (Uint8ClampedArray)
Ustaw wartość lub tablicę wartości.  
  
## <a name="syntax"></a>Składnia  
  
```JavaScript  
uint8ClampedArray.set(index, value);  
uint8ClampedArray.set(array, offset);  
  
```  
  
## <a name="parameters"></a>Parametry  
 `index`  
 Indeks lokalizacji do ustawienia.  
  
 `value`  
 Wartość do ustawienia.  
  
 `array`  
 Tablica wartości (z kontrolą lub bez kontroli typów) do ustawienia.  
  
 `offset`  
 Indeks w bieżącej tablicy oznaczający pozycję, od której mają być zapisywane wartości.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli tablica wejściowa jest typu tablicy, dwie tablice może używać tego samego podstawowego [ArrayBuffer](../../javascript/reference/arraybuffer-object.md). W takim przypadku ustawienie wartości odbywa się tak, jakby wszystkie dane, najpierw ma został skopiowany do buforu tymczasowego, który nie nakłada się na albo tablic, a następnie dane z buforu tymczasowego jest kopiowana do bieżącego tablicy.  
  
 Jeśli offset plus Długość podanej tablicy jest poza zakresem dla bieżącego typu tablicy, wyjątek.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia, jak ustawić pierwszy element tablicy.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var intArr = new Uint8ClampedArray(buffer.byteLength);  
            intArr.set(0, 9);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Arraybuffer — obiekt](../../javascript/reference/arraybuffer-object.md)   
 [Obiekt Uint8ClampedArray](../../javascript/reference/uint8clampedarray-object-javascript.md)