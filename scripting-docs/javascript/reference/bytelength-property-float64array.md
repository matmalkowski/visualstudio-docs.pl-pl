---
title: "byteLength właściwość (Float64Array) | Dokumentacja firmy Microsoft"
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
ms.assetid: 892498c1-dd6c-4037-89c2-cae29f5d09f2
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 594f2f4b0baca773561f7527b673916a102f50e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="bytelength-property-float64array"></a>byteLength Właściwość (Float64Array)
Tylko do odczytu. Ustalona podczas tworzenia długość (w bajtach) tej tablicy od początku jej ArrayBuffer.  
  
## <a name="syntax"></a>Składnia  
  
```JavaScript  
var arrayByteLength = float64Array.byteLength;  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak można pobrać długości tablicy bajtów.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var floatArr = new Float64Array(buffer.byteLength / 8);  
            alert(floatArr.byteLength);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]