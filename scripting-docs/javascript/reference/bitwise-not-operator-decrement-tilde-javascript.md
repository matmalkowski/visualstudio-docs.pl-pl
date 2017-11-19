---
title: Bitowy Operator NOT (~) (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ~
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- NOT operator
- bitwise operators, NOT operator
ms.assetid: 39f92474-fe05-4a8b-9ad8-caca93f82bca
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aec64b055b260efb7a4b0d952aed9b3a5d7ddc82
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-not-operator--javascript"></a>Bitowy operator NOT (~) (JavaScript)
Wykonuje bitowe NOT (negacji) na wyrażeniu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
result = ~ expression  
```  
  
## <a name="parameters"></a>Parametry  
 *wynik*  
 Dowolnej zmiennej.  
  
 *wyrażenie*  
 Dowolne wyrażenie.  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie operatory jednoargumentowe, takich jak `~` operatora, ocenę wyrażeń w następujący sposób:  
  
-   Jeśli zastosowano do niezdefiniowanego lub `null` wyrażenia, błędów czasu wykonywania jest wywoływane.  
  
-   Obiekty są konwertowane na ciągi.  
  
-   Ciągi są konwertowane na liczby, jeśli to możliwe. W przeciwnym razie błąd czasu wykonywania.  
  
-   Wartości logiczna są traktowane jako cyfry (0, jeśli jest to wartość false, 1, jeśli ma wartość true).  
  
 Operator jest stosowany do wynikowa liczba.  
  
 `~` Operator analizuje binarna reprezentacja wartości wyrażenia i wykonuje operację bitową negację na nim.  
  
 Dowolną cyfrę, który jest 1 w wyrażeniu staje się 0 w wyniku. Dowolną cyfrę, który ma wartość 0 w wyrażeniu staje się 1 w wyniku.  
  
 Poniższy przykład przedstawia użycie operatora testu koniunkcji operator NOT (~).  
  
```  
var temp = ~5;  
```  
  
 Wartość wynikową jest -6, jak pokazano w poniższej tabeli.  
  
|Wyrażenie|Wartość binarna (dwa na dopełnienia)|Wartości dziesiętnej|  
|----------------|---------------------------------------|-------------------|  
|5|00000000 00000000 00000000 00000101|5|  
|~5|11111111 11111111 11111111 11111010|-6|  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Logiczny Operator NOT (!)](../../javascript/reference/logical-not-operator-decrement-exclpt-javascript.md)   
 [Kolejność wykonywania działań](../../javascript/operator-subtractprecedence-javascript.md)   
 [Podsumowanie dla operatorów (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)