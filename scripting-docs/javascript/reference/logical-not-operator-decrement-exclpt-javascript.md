---
title: Logiczny Operator NOT (!) (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '!'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Logical NOT operator
- '! operator'
- '! operator, about ! operator'
ms.assetid: 68c3dc71-ae95-4293-9155-67405846d71d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 29c27b9cd670989eb2112de5067e68bd09d76903
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="logical-not-operator--javascript"></a>Operator logiczny NOT (!) (JavaScript)
Wykonuje logiczną negację na wyrażeniu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
result = !expression  
```  
  
## <a name="parameters"></a>Parametry  
 *wynik*  
 Dowolnej zmiennej.  
  
 *wyrażenie*  
 Dowolne wyrażenie.  
  
## <a name="remarks"></a>Uwagi  
 W poniższej tabeli przedstawiono sposób *wynik* jest określana.  
  
|Jeśli `expression` jest|Następnie `result` jest|  
|------------------------|----------------------|  
|Wartość true|False|  
|False|Wartość true|  
  
 Wszystkie operatory jednoargumentowe, takich jak **!** Operator obliczać wyrażeń w następujący sposób:  
  
-   Jeśli zastosowano do niezdefiniowanego lub `null` wyrażenia, błędów czasu wykonywania jest wywoływane.  
  
-   Obiekty są konwertowane na ciągi.  
  
-   Ciągi są konwertowane na liczby, jeśli to możliwe. W przeciwnym razie błąd czasu wykonywania.  
  
-   Wartości logiczna są traktowane jako cyfry (0, jeśli jest to wartość false, 1, jeśli ma wartość true).  
  
 Operator jest stosowany do wynikowa liczba.  
  
 Aby uzyskać **!** operator, jeśli *wyrażenie* jest różna od zera, *wynik* wynosi zero. Jeśli *wyrażenie* wynosi zero, *wynik* 1.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Bitowy Operator NOT (~)](../../javascript/reference/bitwise-not-operator-decrement-tilde-javascript.md)   
 [Kolejność wykonywania działań](../../javascript/operator-subtractprecedence-javascript.md)   
 [Podsumowanie dla operatorów (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)