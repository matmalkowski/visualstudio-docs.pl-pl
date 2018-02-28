---
title: Operator przypisania modulo (JavaScript) | Dokumentacja firmy Microsoft
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
- '%='
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '%= operator [JavaScript]'
- modulus assignment operator [JavaScript]
- assignment operators, JavaScript
ms.assetid: 9147ffbc-b598-4c44-b8f3-7b57914f6e9f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c61a0fda53b50146f25a8e9c2e04dba9490c494c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="modulus-assignment-operator--javascript"></a>Operator przypisania modulo (JavaScript)
Dzieli wartość zmiennej przez wartość wyrażenia i przypisuje pozostałe do zmiennej.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
result %= expression  
```  
  
## <a name="arguments"></a>Argumenty  
 `result`  
 Dowolnej zmiennej.  
  
 `expression`  
 Dowolne wyrażenie liczbowe.  
  
## <a name="remarks"></a>Uwagi  
 Przy użyciu `%=` operator jest dokładnie taka sama, jak określenie:  
  
```  
result = result % expression  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Operator modulo](../../javascript/reference/modulus-operator-decrementjavascript.md)   
 [Kolejność wykonywania działań](../../javascript/operator-subtractprecedence-javascript.md)   
 [Podsumowanie dla operatorów (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)