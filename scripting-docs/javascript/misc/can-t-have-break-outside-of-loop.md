---
title: "Może &#39; ma t &#39; podziału &#39; poza pętlą | Dokumentacja firmy Microsoft"
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
- VS.WebClient.Help.SCRIPT1019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 11d02172-2a78-4705-a730-d21111db5f42
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb23f1bc3de087515cad9ba4910cf2ebaf640353
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="can39t-have-39break39-outside-of-loop"></a>Może &#39; ma t &#39; podziału &#39; poza pętlą
Podjęto próbę użycia **podziału** — słowo kluczowe poza pętlą. **Podziału** — słowo kluczowe jest używane do kończenia pętli lub `switch` instrukcji. Musi być osadzony w treści pętli lub `switch` instrukcji. Jednak **etykiety** można wykonać podziału — słowo kluczowe.  
  
```  
break labelname;  
```  
  
 Wystarczy etykietą formę **podziału** pętle zagnieżdżone — słowo kluczowe, gdy jest używany lub `switch` instrukcje i potrzebę wyjścia z pętli, które nie jest to najbardziej wewnętrznego.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Upewnij się, że **podziału** — słowo kluczowe jest wyświetlana w otaczającej instrukcji pętli lub przełącznika.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcja BREAK](../../javascript/reference/break-statement-javascript.md)   
 [Sterowanie przepływem programu](../../javascript/controlling-program-flow-javascript.md)   
 [Rozwiązywanie problemów w skryptach](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)