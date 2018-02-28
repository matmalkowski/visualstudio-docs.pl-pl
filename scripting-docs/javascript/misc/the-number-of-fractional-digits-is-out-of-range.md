---
title: "Liczba cyfr ułamkowych jest poza zakresem | Dokumentacja firmy Microsoft"
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
- VS.WebClient.Help.SCRIPT5026
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: dbe05d7d-fcf6-4823-9c61-4b814d1ad3c4
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 17ffec5e6b4cfff85b49f61e7105ca8ce3d75c78
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="the-number-of-fractional-digits-is-out-of-range"></a>Liczba cyfr ułamkowych jest poza zakresem
Próbowano przekazać nieprawidłowy argument do funkcji **Number.prototype.toExponential**. Argument funkcji **toExponential()** musi należeć do zakresu od 0 do 20 (włącznie).  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Upewnij się, argument **toExponential()** nie jest za duża albo za mała.  
  
## <a name="see-also"></a>Zobacz też  
 [toExponential — metoda (numer)](../../javascript/reference/toexponential-method-number-javascript.md)