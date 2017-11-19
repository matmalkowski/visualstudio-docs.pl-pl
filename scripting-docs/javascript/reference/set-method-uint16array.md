---
title: Metoda Set (Uint16Array) | Dokumentacja firmy Microsoft
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
ms.assetid: 5bfbc50b-d786-4c0d-918a-ae1241a32626
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 74d8e521bc6af4e2994ba1fc81de82c0e3eb1721
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="set-method-uint16array"></a>Metoda set (Uint16Array)
Ustaw wartość lub tablicę wartości.  
  
## <a name="syntax"></a>Składnia  
  
```JavaScript  
uint16Array.set(index, value);  
uint16Array.set(array, offset);  
  
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
 Jeśli tablica wejściowa jest tablicą TypedArray, te dwie tablice mogą używać tego samego podstawowego ArrayBuffer. W tej sytuacji ustawianie wartości odbywa się, tak jakby wszystkie dane były najpierw kopiowane do tymczasowego buforu, który nie nakłada się na żadną z tablic, a następnie dane z buforu tymczasowego są kopiowane do bieżącej tablicy.  
  
 Jeśli przesunięcie plus długość danej tablicy jest poza zakresem dla bieżącej tablicy TypedArray, zgłaszany jest wyjątek.  
  
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
            var intArr = new Uint16Array(buffer.byteLength / 2);  
            intArr.set(0, 9);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]