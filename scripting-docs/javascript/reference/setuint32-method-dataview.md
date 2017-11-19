---
title: "setUint32 — metoda (DataView) | Dokumentacja firmy Microsoft"
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
ms.assetid: ab2894fe-4cdc-40c8-9503-951e42ca61e7
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4e4d2bf075c46f84c75a174b0ca5954b9cedf154
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="setuint32-method-dataview"></a>setUint32 — Metoda (DataView)
Ustawia wartość Uint32 na określone przesunięcie bajtów od początku widoku. Brak bez wyrównania ograniczenia; wartości wielobajtowego może być ustawiona na dowolnym przesunięcie.  
  
## <a name="syntax"></a>Składnia  
  
```  
dataView.setUint32 (byteOffset, value, littleEndian);   
```  
  
## <a name="parameters"></a>Parametry  
 `byteOffset`  
 Miejsce w buforze, w którym ma być pobrana wartość.  
  
 `value`  
 Wartość do ustawienia.  
  
 `littleEndian`  
 Opcjonalny. Jeśli wartość false lub niezdefiniowany powinna być zapisana wartość big-endian, w przeciwnym razie wartość little endian mają być zapisywane.  
  
## <a name="remarks"></a>Uwagi  
 Te metody zgłosić wyjątek, jeśli zapisują poza koniec widoku.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak ustawić pierwszy Uint32 w widoku danych.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setUint32(0, 9);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]