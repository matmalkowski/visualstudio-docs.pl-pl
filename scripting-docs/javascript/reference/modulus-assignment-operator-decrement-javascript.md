---
title: Remainder — Operator przypisania (JavaScript) | Dokumentacja firmy Microsoft
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
- '%='
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '%= operator [JavaScript]'
- remainder assignment operator [JavaScript]
- assignment operators, JavaScript
ms.assetid: 9147ffbc-b598-4c44-b8f3-7b57914f6e9f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: be7db43931374a71672c42ae059767585a9a5757
ms.sourcegitcommit: 873c0e1a31def013bcca1b0caa0eb0249de89bec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2018
ms.locfileid: "29753526"
---
# <a name="remainder-assignment-operator--javascript"></a>Operator przypisania reszty (JavaScript)
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
 [Operator reszty](../../javascript/reference/modulus-operator-decrementjavascript.md)   
 [Kolejność wykonywania działań](../../javascript/operator-subtractprecedence-javascript.md)   
 [Podsumowanie dla operatorów (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)