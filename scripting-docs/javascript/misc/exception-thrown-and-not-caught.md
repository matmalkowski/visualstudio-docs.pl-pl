---
title: "Wyjątek zgłoszony i nieprzechwycony | Dokumentacja firmy Microsoft"
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
- VS.WebClient.Help.SCRIPT5022
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b5235490-a8e7-42e3-804e-d85235bc6f05
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 839ff08da4d26406b508a206c809b0813d2b32e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="exception-thrown-and-not-caught"></a>Wyjątek zgłoszony i nieprzechwycony
Zostanie uwzględnione `throw` instrukcji w kodzie, ale nie znajdował się w obrębie **spróbuj** bloku, lub nie było nie skojarzone **catch** bloku pułapki błąd. Wyjątki są zgłaszane z poziomu **spróbuj** zablokowane, używając **throw** instrukcji i zgłoszony poza **spróbuj** zablokować z **catch** instrukcji.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Umieść kod, który może zgłosić wyjątek w **spróbuj** blokować i upewnij się, brak odpowiadającego **catch** bloku.  
  
-   Upewnij się, że instrukcji catch oczekuje niepoprawny wyjątek.  
  
-   Jeśli jest zgłoszony wyjątek, upewnij się, że istnieje inny odpowiedniej instrukcji catch.  
  
## <a name="see-also"></a>Zobacz też  
 [Error — obiekt](../../javascript/reference/error-object-javascript.md)   
 [throw — instrukcja](../../javascript/reference/throw-statement-javascript.md)   
 [try... catch... finally — instrukcja](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)