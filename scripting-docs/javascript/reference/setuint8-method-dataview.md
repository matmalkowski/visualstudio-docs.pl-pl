---
title: "setUint8 — metoda (DataView) | Dokumentacja firmy Microsoft"
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
ms.assetid: b294262b-3f4b-4183-a292-5a6982cbdd27
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4ab533520d933b11657175d396433d732536c7a3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="setuint8-method-dataview"></a>setUint8 — Metoda (DataView)
Przechowuje wartość Uint8 na określone przesunięcie bajtów od początku widoku.  
  
## <a name="syntax"></a>Składnia  
  
```  
dataView.setUint8(byteOffset, value);   
```  
  
## <a name="parameters"></a>Parametry  
 `byteOffset`  
 Miejsce w buforze, w którym można ustawić wartości.  
  
 `value`  
 Wartość do ustawienia.  
  
## <a name="remarks"></a>Uwagi  
 Te metody zgłosić wyjątek, jeśli zapisują poza koniec widoku.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak ustawić pierwszy Uint8 w widoku danych.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setUint8(0, 9);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]