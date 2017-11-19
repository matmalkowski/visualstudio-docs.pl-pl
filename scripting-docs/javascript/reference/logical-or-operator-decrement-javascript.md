---
title: Logiczny Operator OR (|) (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '||'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '|| operator'
- logical OR operator
ms.assetid: 95295331-6269-4311-8391-dc1c68e116ab
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 80c8e1bcae57e13642a0c77ae75c7c2aac58ace6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="logical-or-operator--javascript"></a>Operator logiczny OR (||) (JavaScript)
Dokonuje logicznego rozłączenia dwóch wyrażeń.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
result = expression1 || expression2  
```  
  
## <a name="parameters"></a>Parametry  
 *wynik*  
 Dowolnej zmiennej.  
  
 *wyrażenie1*  
 Dowolne wyrażenie.  
  
 *wyrażenie2*  
 Dowolne wyrażenie.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli wynikiem obliczania wyrażenia jednego lub obu tych **True**, *wynik* jest **True**. W poniższej tabeli przedstawiono sposób *wynik* jest określana:  
  
|Jeśli `expression1` jest|I `expression2` jest|`result` Jest|  
|-------------------------|--------------------------|---------------------|  
|Wartość true|Wartość true|Wartość true|  
|Wartość true|False|Wartość true|  
|False|Wartość true|Wartość true|  
|False|False|False|  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]do konwersji wartości inne niż logiczne na wartości logiczne stosowane są następujące reguły:  
  
-   Wszystkie obiekty są traktowane jako true.  
  
-   Ciągi są traktowane jako wartość false, tylko wtedy, gdy są puste.  
  
-   `null`Niezdefiniowane oraz są traktowane jako wartość false.  
  
-   Numery to wartość false, gdy i tylko wtedy, gdy znajdują się one 0.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kolejność wykonywania działań](../../javascript/operator-subtractprecedence-javascript.md)   
 [Podsumowanie dla operatorów (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)