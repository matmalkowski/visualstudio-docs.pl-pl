---
title: Bitowy Operator OR (|) (JavaScript) | Dokumentacja firmy Microsoft
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
- '|'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- bitwise operators, OR operator
- OR operator
- '| operator'
ms.assetid: ffc8f758-3151-478e-bafb-fc78f1c469a0
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a91c616c84b9d38154bf936f61fb856a4ebad0f7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24788983"
---
# <a name="bitwise-or-operator--javascript"></a>Bitowy operator OR (|) (JavaScript)
Wykonuje logiczną lub dwóch wyrażeń.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
result = expression1 | expression2  
```  
  
## <a name="parameters"></a>Parametry  
 *wynik*  
 Dowolnej zmiennej.  
  
 *wyrażenie1*  
 Dowolne wyrażenie.  
  
 *wyrażenie2*  
 Dowolne wyrażenie.  
  
## <a name="remarks"></a>Uwagi  
 **&#124;** operator analizuje binarna reprezentacja wartości dwóch wyrażeń i wykonuje logiczną operację lub na nich. Wynik operacji działa w następujący sposób:  
  
```JavaScript  
0101   (expression1)  
1100   (expression2)  
----  
1101   (result)  
```  
  
 Każdy razem z wyrażeń ma wartość 1 w cyfrę, wynik będzie mieć wartość 1 w tym cyfr. W przeciwnym razie wynik będzie mieć wartość 0 w tym cyfr.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Operator lub Operator przypisania (&#124; =)](../../javascript/reference/bitwise-or-assignment-operator-decrement-equal-javascript.md)   
 [Kolejność wykonywania działań](../../javascript/operator-subtractprecedence-javascript.md)   
 [Podsumowanie dla operatorów (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)