---
title: getUint16 — metoda (DataView) | Dokumentacja firmy Microsoft
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
ms.assetid: 3c0d9ad8-30b0-42a3-b0fe-aa805398c396
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2da1ea7bdbbbc1d99f9b7b6c33e4b3d83e0ba84f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790510"
---
# <a name="getuint16-method-dataview"></a>getUint16 — Metoda (DataView)
Pobiera wartość Uint16 na określone przesunięcie bajtów od początku widoku. Brak bez wyrównania ograniczenia; wartości wielobajtowego mogą być pobierane z dowolnym przesunięcie.  
  
## <a name="syntax"></a>Składnia  
  
```  
var testInt = dataView.getUint16(byteOffset, littleEndian);   
```  
  
## <a name="parameters"></a>Parametry  
 `testInt`  
 Wymagany. Wartość Uint16, która jest zwracana z metody.  
  
 `byteOffset`  
 Miejsce w buforze, w którym ma być pobrana wartość.  
  
 `littleEndian`  
 Opcjonalny. Jeśli wartość false lub niezdefiniowany odczytuje wartość big-endian, w przeciwnym razie wartość little endian są odczytywane.  
  
## <a name="remarks"></a>Uwagi  
 Te metody zgłosić wyjątek, jeśli będą one odczytu za końcem widoku.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak uzyskać pierwszy Uint16 w widoku danych.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            alert(dataView.getUint16(0));  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]