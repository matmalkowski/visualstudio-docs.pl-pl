---
title: Operator logiczny AND (&amp;&amp;) (JavaScript) | Dokumentacja firmy Microsoft
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
- '&&'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- logical AND operator
- '&& operator'
ms.assetid: 4714dea9-1999-444a-8acd-72f0851e4f65
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2107eb89c5ca964cf08172050b49307cb150590f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="logical-and-operator-ampamp-javascript"></a>Operator logiczny AND (&amp;&amp;) (JavaScript)
Dokonuje logicznego połączenia dwóch wyrażeń.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
result = expression1 && expression2   
```  
  
## <a name="parameters"></a>Parametry  
 `result`  
 Dowolnej zmiennej.  
  
 `expression1`  
 Dowolne wyrażenie.  
  
 `expression2`  
 Dowolne wyrażenie.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `expression1` daje w wyniku `false`, `result` jest `expression1`. W przeciwnym razie `result` jest `expression2`. W rezultacie zwraca operacji `true` Jeśli obydwa argumenty operacji są prawdziwe; w przeciwnym razie zwraca `false`.  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]do konwersji wartości inne niż logiczne na wartości logiczne stosowane są następujące reguły:  
  
-   Wszystkie obiekty są traktowane jako `true`.  
  
-   Ciągi są traktowane jako `false` jeśli są puste.  
  
-   `null`i `undefined` są traktowane jako `false`.  
  
-   Liczba jest `false` jest zero.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kolejność wykonywania działań](../../javascript/operator-subtractprecedence-javascript.md)   
 [Podsumowanie dla operatorów (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)