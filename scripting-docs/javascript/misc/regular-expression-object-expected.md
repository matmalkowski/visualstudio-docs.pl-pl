---
title: "Oczekiwano obiektu będącego wyrażeniem regularnym | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5016
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: e226096c-c58f-4bcb-a71e-fa32ce474b67
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9a5a0f3cb3b86e2e01d522f85d0dae23e9c9d3ca
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="regular-expression-object-expected"></a>Oczekiwano obiektu będącego wyrażeniem regularnym
Użytkownik próbował wywołać **RegExp.prototype.toString** lub **RegExp.prototype.valueOf** metody dla obiekt typu innego niż `RegExp`. Obiekt tego typu wywołania musi być typu `RegExp`.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Tylko wywołania **RegExp.prototype.toString** lub **RegExp.prototype.valueOf** metod na obiektach typu `RegExp`.  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekt będący wyrażeniem regularnym](../../javascript/reference/regular-expression-object-javascript.md)   
 [Składnia wyrażeń regularnych (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)