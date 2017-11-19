---
title: Oczekiwano obiektu logicznego | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5010
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 35d71b7f-53fd-44c4-a7c7-b1550c65cfd4
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 600ab26f60c2196ebc682adcffcd6b24c23cd358
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="boolean-expected"></a>Oczekiwano obiektu logicznego
Użytkownik próbował wywołać **Boolean.prototype.toString** lub **Boolean.prototype.valueOf** metody dla obiekt typu innego niż `Boolean`. Obiekt tego typu wywołania musi być typu `Boolean`. Na przykład:  
  
```JavaScript  
var o = new Object;  
o.f = Boolean.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Tylko wywołania typu Boolean**. prototype.toString** lub **Boolean.prototype.valueOf** metod na obiektach typu **Boolean.**  
  
## <a name="see-also"></a>Zobacz też  
 [Boolean — obiekt](../../javascript/reference/boolean-object-javascript.md)   
 [Typy danych](../../javascript/data-types-javascript.md)   
 [Sterowanie przepływem programu](../../javascript/controlling-program-flow-javascript.md)   
 [Kopiowanie, przekazywanie i porównywanie danych](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)