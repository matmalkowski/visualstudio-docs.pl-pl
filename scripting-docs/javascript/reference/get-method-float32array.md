---
title: Metoda Get (Float32Array) | Dokumentacja firmy Microsoft
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
ms.assetid: f859481c-0bb8-43d3-9d54-38d303e44397
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea17b3d26a1f192843a2fb9d2d87f62fe26fceff
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="get-method-float32array"></a>Metoda get (Float32Array)
Pomijalne. Pobiera element wskazywany przez określony indeks.  
  
## <a name="syntax"></a>Składnia  
  
```JavaScript  
var value = float32Array.get(index);  
```  
  
## <a name="parameters"></a>Parametry  
 `value`  
 Wartość zwracana przez tę metodę.  
  
 `index`  
 Indeks wskazujący element tablicy do pobrania.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia, jak pobrać pierwszy element tablicy.  
  
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
            var element = floatArr.getFloat32(0);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]