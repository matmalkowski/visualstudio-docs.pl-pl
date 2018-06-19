---
title: Operator przecinkowy (,) (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- '%2C'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- comma operator
ms.assetid: 699fa0bf-cd0a-45ee-a291-2fbed4ecd470
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2cb504beefc5ce4c260ec8296e2cf097e17d349e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24789151"
---
# <a name="comma-operator--javascript"></a>Operator przecinkowy (,) (JavaScript)
Powoduje, że dwa wyrażenia do wykonania po kolei.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
expression1, expression2  
```  
  
## <a name="parameters"></a>Parametry  
 `expression1`  
 Dowolne wyrażenie.  
  
 `expression2`  
 Dowolne wyrażenie.  
  
## <a name="remarks"></a>Uwagi  
 `,` Operatora powoduje, że wyrażenia do wykonania w kolejności od lewej do prawej. Użycia `,` jest operator w wyrażeniu przyrostu `for` pętli. Na przykład:  
  
```JavaScript  
j=25;  
for (i = 0; i < 10; i++, j++)  
{  
   k = i + j;  
}  
```  
  
 `for` Instrukcji umożliwia tylko jedno wyrażenie wykonywanej na końcu każdej przekazywania pętli. `,` Operator umożliwia wielu wyrażeń traktowane jako jedno wyrażenie, dlatego może być zwiększane obie zmienne.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [for — instrukcja](../../javascript/reference/for-statement-javascript.md)   
 [Kolejność wykonywania działań](../../javascript/operator-subtractprecedence-javascript.md)   
 [Podsumowanie dla operatorów (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)