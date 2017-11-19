---
title: "instanceof — Operator (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: instanceof_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: instanceOf operator
ms.assetid: 92467bdc-56b5-42dc-adbd-a219776454d2
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 672047cb066a812d16edc693638c3d6d8295798b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="instanceof-operator-javascript"></a>instanceof — Operator (JavaScript)
Zwraca wartość logiczną, wskazującą, czy obiekt jest wystąpienie danej klasy.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
result = object instanceof class  
```  
  
## <a name="parameters"></a>Parametry  
 `result`  
 Wymagany. Dowolnej zmiennej.  
  
 `object`  
 Wymagany. Dowolne wyrażenie obiektu.  
  
 `class`  
 Wymagany. Występuje, określony klasy obiektów.  
  
## <a name="remarks"></a>Uwagi  
 `instanceof` Operator zwraca `true` Jeśli `object` jest wystąpieniem `class`. Zwraca `true` Jeśli `true` Jeśli `class` znajduje się w łańcuchu prototypu obiektu. Zwraca `false` Jeśli `object` nie jest wystąpieniem `class`, lub jeśli `object` jest `null`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `instanceof` operatora.  
  
```JavaScript  
function objTest(obj){  
    var i, t, s = "";  
    t = new Array();  
    t["Date"] = Date;  
    t["Object"] = Object;  
    t["Array"] = Array;  
        for (i in t){  
            if (obj instanceof t[i]) {   
                s += "obj is an instance of " + i + "<br/>";  
            }  
            else {  
                s += "obj is not an instance of " + i + "<br/>";  
        }  
    }  
    return(s);  
}  
  
var obj = new Date();  
document.write(objTest(obj));  
  
// Output:   
// obj is an instance of Date  
// obj is an instance of Object  
// obj is not an instance of Array  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kolejność wykonywania działań](../../javascript/operator-subtractprecedence-javascript.md)   
 [Podsumowanie dla operatorów (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)