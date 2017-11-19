---
title: "Math.sign — funkcja (JavaScript) | Dokumentacja firmy Microsoft"
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
ms.assetid: 8b462020-ceff-4947-8dd1-c78e6aff8d98
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2cae32118f2265e02c67592facff8e49e8edd633
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="mathsign-function-javascript"></a>Math.sign — funkcja (JavaScript)
Zwraca znak liczby, wskazującą, czy liczba jest dodatnia, ujemną lub 0.  
  
## <a name="syntax"></a>Składnia  
  
```  
Math.sign(number)  
```  
  
## <a name="remarks"></a>Uwagi  
 Wymagane `number` argument jest wyrażenia liczbowego, który na potrzeby logowania.  
  
 Wartość zwracana jest jedną z następujących czynności:  
  
-   `NaN`, jeśli `number` jest `NaN`.  
  
-   -0, jeśli `number` jest - 0.  
  
-   + 0, jeśli `number` jest + 0.  
  
-   -1, jeśli `number` jest ujemna, a nie - 0.  
  
-   + 1, jeśli `number` jest dodatnia, a nie + 0.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]