---
title: Operator dodawania (+) (JavaScript) | Dokumentacja firmy Microsoft
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
- +
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arithmetic operators, addition
- strings [Visual Studio], concatenating
- concatenation operators, vs. addition operator
- addition operator
- + operator
ms.assetid: ec1237d3-e78b-4e77-bd7d-c0204cf03acd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 70ff02b1f234da7b88d28e66da82262ccef7bfaf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="addition-operator--javascript"></a>Operator dodawania (+) (JavaScript)
Dodaje wartość wyrażenia liczbowego jednego do drugiego lub łączy dwa ciągi.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
result = expression1 + expression2  
```  
  
## <a name="parameters"></a>Parametry  
 `result`  
 Dowolnej zmiennej.  
  
 `expression1`  
 Dowolne wyrażenie.  
  
 `expression2`  
 Dowolne wyrażenie.  
  
## <a name="remarks"></a>Uwagi  
 Typy dwóch wyrażeń określają zachowanie  **+**  operatora.  
  
|IF|Następnie|  
|--------|----------|  
|Oba wyrażenia są liczbowego lub typu Boolean|Dodaj|  
|Oba wyrażenia są ciągami|Łączenie|  
|Jedno wyrażenie jest liczbowego, a drugi to ciąg|Łączenie|  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Operator przypisania dodawania (+=)](../../javascript/reference/addition-assignment-operator-decrement-equal-javascript.md)   
 [Kolejność wykonywania działań](../../javascript/operator-subtractprecedence-javascript.md)   
 [Podsumowanie dla operatorów (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)