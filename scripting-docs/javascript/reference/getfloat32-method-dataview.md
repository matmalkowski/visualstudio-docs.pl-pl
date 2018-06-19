---
title: getFloat32 — metoda (DataView) | Dokumentacja firmy Microsoft
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
ms.assetid: adecf671-bde4-46be-a875-33b6d6e970b1
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 75fc5be6d8563a44504ae2d1c7ddd9429eccb390
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790459"
---
# <a name="getfloat32-method-dataview"></a>getFloat32 — Metoda (DataView)
Pobiera wartość Float32 na określone przesunięcie bajtów od początku widoku. Brak bez wyrównania ograniczenia; wartości wielobajtowego mogą być pobierane z dowolnym przesunięcie.  
  
## <a name="syntax"></a>Składnia  
  
```  
var testFloat = dataView.getFloat32(byteOffset, littleEndian);   
```  
  
## <a name="parameters"></a>Parametry  
 `testFloat`  
 Wymagany. Wartość Float32, która jest zwracana z metody.  
  
 `byteOffset`  
 Miejsce w buforze, w którym ma być pobrana wartość.  
  
 `littleEndian`  
 Opcjonalny. Jeśli wartość false lub niezdefiniowany odczytuje wartość big-endian, w przeciwnym razie wartość little endian są odczytywane.  
  
## <a name="remarks"></a>Uwagi  
 Te metody zgłosić wyjątek, jeśli będą one odczytu za końcem widoku.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak uzyskać pierwszy Float32 w widoku danych.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            alert(dataView.getFloat32(0));  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]