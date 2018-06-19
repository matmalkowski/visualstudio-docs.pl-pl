---
title: byteLength właściwość (DataView) | Dokumentacja firmy Microsoft
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
ms.assetid: 6274285f-b673-48f6-a1e7-89ff7ee348b5
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e2a9eb55a40722c42ccc9711c434061e98b64039
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24788920"
---
# <a name="bytelength-property-dataview"></a>byteLength Właściwość (DataView)
Tylko do odczytu. Długość tego widoku od początku jego buforu ArrayBuffer, w bajtach, ustalona podczas tworzenia.  
  
## <a name="syntax"></a>Składnia  
  
```JavaScript  
var byteLength = dataView.byteLength;  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób uzyskania długości DataView z XMLHttpRequest.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            alert(dataView.byteLength);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]