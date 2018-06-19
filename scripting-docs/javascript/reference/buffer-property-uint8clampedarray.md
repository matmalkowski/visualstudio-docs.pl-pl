---
title: bufor właściwości (Uint8ClampedArray) | Dokumentacja firmy Microsoft
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
ms.assetid: 4b87d767-4246-4cf4-bb1d-241b3516397a
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a16ee962b3d8dcdbd99eb10b5870f3564ba351d4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24788947"
---
# <a name="buffer-property-uint8clampedarray"></a>bufor właściwości (Uint8ClampedArray)
Tylko do odczytu. Pobiera [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) , do którego odwołuje tej tablicy.  
  
## <a name="syntax"></a>Składnia  
  
```JavaScript  
var arrayBuffer = uint8ClampedArray.buffer;  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak pobrać ArrayBuffer tablicy.  
  
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
            alert(intArr.buffer.byteLength);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Arraybuffer — obiekt](../../javascript/reference/arraybuffer-object.md)   
 [Obiekt Uint8ClampedArray](../../javascript/reference/uint8clampedarray-object-javascript.md)