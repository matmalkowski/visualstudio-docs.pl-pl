---
title: Operatory dekrementacji (--) (JavaScript) i inkrementacji (++) | Dokumentacja firmy Microsoft
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
- --
- ++
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- increment operators, syntax
- ++ operator
- ++ operator, about ++ operator
- decrement operators, syntax
- -- operator
ms.assetid: 49eaf4cf-8818-478d-a429-cdd2ece20811
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 806bd321bb1f81d585a6595b8cf2842571164921
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790714"
---
# <a name="increment--and-decrement----operators-javascript"></a>Operatory inkrementacji (++) i dekrementacji (--) (JavaScript)
Zwiększa operator inkrementacji i dekrementacji zmniejsza operator wartość zmiennej o jeden.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      result = ++variable  
result = --variable  
result = variable++  
result = variable--  
```  
  
## <a name="parameters"></a>Parametry  
 `result`  
 Dowolnej zmiennej.  
  
 `variable`  
 Dowolnej zmiennej.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli operator występuje przed zmiennej, wartość jest modyfikowana przed obliczone wyrażenie. Jeśli operator pojawia się po zmienna, wartość jest modyfikowana po wyrażenie jest obliczane.  Innymi słowy, podane `j = ++k;`, wartość `j` jest oryginalna wartość `k` plus jeden; podane `j = k++;`, wartość `j` jest oryginalnej wartości elementu `k`, który jest zwiększany po jego wartość jest przypisany do `j`.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kolejność wykonywania działań](../../javascript/operator-subtractprecedence-javascript.md)   
 [Podsumowanie dla operatorów (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)