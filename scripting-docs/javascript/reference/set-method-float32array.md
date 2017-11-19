---
title: Metoda Set (Float32Array) | Dokumentacja firmy Microsoft
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
ms.assetid: 0d486ed3-72eb-4af2-b0a6-ae727c588883
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fdd3d5b350f44aaf5b96a320e0b447587c07ac22
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="set-method-float32array"></a>Metoda set (Float32Array)
Ustaw wartość lub tablicę wartości.  
  
## <a name="syntax"></a>Składnia  
  
```JavaScript  
float32Array.set(index, value);  
float32Array.set(array, offset);  
  
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
            var floatArr = new Float32Array(buffer.byteLength / 4);  
            floatArr.set(0, 9);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]