---
title: Oczekiwano funkcji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5002
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f62ade94-9f6f-4832-9b9b-49a06a385bbe
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aa2db3e95d4baece288c9f984a7a9cf7a82c9d1d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24788713"
---
# <a name="function-expected"></a>Oczekiwana funkcja
Albo próbował wywołać za pomocą jednego z **prototypu funkcji** metody dla obiektu, który nie był `Function` obiekt, lub użyć obiektu w kontekście wywołania funkcji. Na przykład poniższy kod tworzy ten błąd, ponieważ **przykład** nie jest funkcją.  
  
```JavaScript  
var example = new Object();  // Create a new object called "example".  
var x = example();           // Try and call example as if it were a function.  
```  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Wywoływać tylko **prototypu funkcji** metody `Function` obiektów.  
  
-   Upewnij się, że używasz operator wywołania funkcji `()` można wywołać tylko funkcje.  
  
## <a name="see-also"></a>Zobacz też  
 [Function — obiekt](../../javascript/reference/function-object-javascript.md)   
 [prototype — właściwość (obiekt)](../../javascript/reference/prototype-property-object-javascript.md)