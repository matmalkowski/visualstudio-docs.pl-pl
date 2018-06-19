---
title: setFloat32 — metoda (DataView) | Dokumentacja firmy Microsoft
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
ms.assetid: b3f68048-c817-48d2-bc17-945e3bcc94d7
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a72bf2781bfbae7c7cd301d02ad71ebfbeffa13
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791254"
---
# <a name="setfloat32-method-dataview"></a>setFloat32 — Metoda (DataView)
Ustawia wartość Float32 na określone przesunięcie bajtów od początku widoku. Brak bez wyrównania ograniczenia; wartości wielobajtowego może być ustawiona na dowolnym przesunięcie.  
  
## <a name="syntax"></a>Składnia  
  
```  
dataView.setFloat32 (byteOffset, value, littleEndian);   
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
 Poniższy przykład pokazuje, jak ustawić pierwszy Float32 w widoku danych.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setFloat32(0, 9.1);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]