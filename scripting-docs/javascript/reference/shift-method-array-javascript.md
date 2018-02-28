---
title: "SHIFT — metoda (tablica) (JavaScript) | Dokumentacja firmy Microsoft"
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
- shift
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- shift method
ms.assetid: f33baec5-f67e-4760-b7c1-553727bd0423
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 664c3f764950b329cea8356f5b350ee917f0a60f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="shift-method-array-javascript"></a>shift — Metoda (Tablica) (JavaScript)
Usuwa z tablicy pierwszy element i zwraca go.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
arrayObj.shift( )  
```  
  
#### <a name="parameters"></a>Parametry  
 Wymagane `arrayObj` odwołanie jest `Array` obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca element usunąć z tablicy.  
  
## <a name="remarks"></a>Uwagi  
 Poniższy przykład przedstawia użycie `shift` metody.  
  
```JavaScript  
var arr = new Array(10, 11, 12);  
while (arr.length > 0)  
    {  
    var i = arr.shift();  
    document.write (i.toString() + " ");  
    }  
  
// Output:   
// 10 11 12  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [unshift — metoda (tablica)](../../javascript/reference/unshift-method-array-javascript.md)