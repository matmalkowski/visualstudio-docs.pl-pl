---
title: Operator przypisania dodawania (+=) (JavaScript) | Dokumentacja firmy Microsoft
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
- +=
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- addition assignment operator (+=)
- += operator
- assignment operators, JavaScript
ms.assetid: 8517d05c-38b0-4107-bea4-253eb420f438
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38d86c537dda90dd7f44923b97384b3609dad5ba
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24788944"
---
# <a name="addition-assignment-operator--javascript"></a>Operator przypisania dodawania (+=) (JavaScript)
Dodaje wartości wyrażenia wartości zmiennej i przypisuje wynik do zmiennej.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
result += expression   
```  
  
## <a name="parameters"></a>Parametry  
 `result`  
 Dowolnej zmiennej.  
  
 `expression`  
 Dowolne wyrażenie.  
  
## <a name="remarks"></a>Uwagi  
 Za pomocą tego operatora jest dokładnie taka sama jak określenie: `result = result + expression`.  
  
 Typy dwóch wyrażeń określają zachowanie `+=` operatora.  
  
|IF|Następnie|  
|--------|----------|  
|Oba wyrażenia są liczbowego lub typu Boolean|Dodaj|  
|Oba wyrażenia są ciągami|Łączenie|  
|Jedno wyrażenie jest liczbowego, a drugi to ciąg|Łączenie|  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Operator dodawania (+)](../../javascript/reference/addition-operator-decrement-javascript.md)   
 [Kolejność wykonywania działań](../../javascript/operator-subtractprecedence-javascript.md)   
 [Podsumowanie dla operatorów (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)