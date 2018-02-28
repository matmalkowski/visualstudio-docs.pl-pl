---
title: Oczekiwano obiektu wyliczenia | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5015
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: dc6e32c1-a6e6-4e12-ac99-e3f65f91c8d7
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 485e6e387f07fd3a54727f5f8e08c0a00743c6d9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="enumerator-object-expected"></a>Oczekiwano obiektu wyliczenia
Użytkownik próbował wywołać **Enumerator.prototype.atEnd, Enumerator.prototype.item, Enumerator.prototype.moveFirst,** lub **Enumerator.prototype.moveNext** metody dla obiekt typu innych niż `Enumerator`. Obiekt tego typu wywołania musi być typu `Enumerator`. Oto przykładowy kod, który dzieli tej reguły:  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Tylko wywołania **Enumerator.prototype.atEnd**, **Enumerator.prototype.item**, **Enumerator.prototype.moveFirst**, lub  **Enumerator.prototype.moveNext** metod na obiektach typu `Enumerator`. Aby sprawdzić, czy obiekt jest `Enumerator` obiekt, należy użyć:  
  
    ```  
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Enumerator — obiekt](../../javascript/reference/enumerator-object-javascript.md)