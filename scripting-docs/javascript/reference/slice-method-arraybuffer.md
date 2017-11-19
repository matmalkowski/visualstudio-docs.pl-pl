---
title: Metoda slice (ArrayBuffer) | Dokumentacja firmy Microsoft
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
ms.assetid: 2dcc51ff-f444-4d51-80ba-3bcd845ba0ae
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25fc10a02b4a3422a6720ad91c8bba29906da0e5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="slice-method-arraybuffer"></a>Metoda slice (ArrayBuffer)
Zwraca część [ArrayBuffer](../../javascript/reference/arraybuffer-object.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
arrayBufferObj.slice(start, [end])   
```  
  
## <a name="parameters"></a>Parametry  
 `arrayBufferObj`  
 Wymagany. [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) sekcji zostaną skopiowane z obiektu.  
  
 `start`  
 Wymagany. Indeks typu byte na początku sekcji do skopiowania.  
  
 `end`  
 Opcjonalny. Indeks bajtów koniec sekcji do skopiowania.  
  
## <a name="remarks"></a>Uwagi  
 `slice` Metoda zwraca [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) obiekt zawierający określoną część `arrayBufferObj`.  
  
 `slice` Metoda kopiuje do, z wyłączeniem bajtów wskazywanym przez `end`. Jeśli `start` lub `end` jest ujemna, określony indeks jest traktowany jako `length`  +  `start` lub `end`, gdzie `length` długość [ArrayBuffer](../../javascript/reference/arraybuffer-object.md). Jeśli `end` pominięcia wyodrębniania będzie nadal występować na końcu `arrayBufferObj`. Jeśli `end` występuje przed `start`, bajty nie są kopiowane do nowego [ArrayBuffer](../../javascript/reference/arraybuffer-object.md).  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach pokazano, jak używać `slice` metody.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer1 = req.response;  
            var buffer2 = buffer1.slice(40, 48);  
            var dataview = new DataView(buffer2);  
            var ints = new Int32Array(buffer2.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt32(i * 4);  
            }  
        alert(ints[1]);  
        }  
    }  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Arraybuffer — obiekt](../../javascript/reference/arraybuffer-object.md)