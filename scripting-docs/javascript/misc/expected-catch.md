---
title: Oczekiwano &#39; catch &#39; | Dokumentacja firmy Microsoft
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
- VS.WebClient.Help.SCRIPT1033
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f1cd947f-eba2-411e-8e84-8ca86f608643
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6cd1e57137d220ebcf3834070e36d8257e2dca7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24788995"
---
# <a name="expected-39catch39"></a>Oczekiwano &#39; catch &#39;
Użyto obsługi wyjątków **spróbuj** zablokować, ale nie zapisano skojarzony **catch** instrukcji. Mechanizm obsługi wyjątków wymaga, aby kod, który może zakończyć się niepowodzeniem, wraz z kodem, który nie należy wykonać, jeśli wystąpi wyjątek, być ujęte w **spróbuj** bloku. Wyjątki są zgłaszane z poziomu **spróbuj** zablokowane, używając **throw** instrukcji i zgłoszony poza **spróbuj** bloku co najmniej jednym **catch**instrukcje.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Dodaj skojarzony **catch** bloku.  
  
-   Spróbuj użyć **koniec** zablokować zamiast **catch** bloku.  
  
## <a name="see-also"></a>Zobacz też  
 [try... catch... finally — instrukcja](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Error — obiekt](../../javascript/reference/error-object-javascript.md)