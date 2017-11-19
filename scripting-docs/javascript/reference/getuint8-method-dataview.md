---
title: "getUint8 — metoda (DataView) | Dokumentacja firmy Microsoft"
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
ms.assetid: 9fbf4be3-4c0b-4963-a7a1-d57f1501b4cf
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 315baa2ca5abfe006a7f8d524619479d99a11fc9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="getuint8-method-dataview"></a>getUint8 — Metoda (DataView)
Pobiera wartość Uint8 na określone przesunięcie bajtów od początku widoku. Brak bez wyrównania ograniczenia; wartości wielobajtowego mogą być pobierane z dowolnym przesunięcie.  
  
## <a name="syntax"></a>Składnia  
  
```  
var testInt = dataView.getUint8(byteOffset);   
```  
  
## <a name="parameters"></a>Parametry  
 `testInt`  
 Wymagany. Wartość Uint8, która jest zwracana z metody.  
  
 `byteOffset`  
 Miejsce w buforze, w którym ma być pobrana wartość.  
  
## <a name="remarks"></a>Uwagi  
 Te metody zgłosić wyjątek, jeśli będą one odczytu za końcem widoku.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak uzyskać pierwszy Uint8 w widoku danych.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            alert(dataView.getUint8(0));  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]