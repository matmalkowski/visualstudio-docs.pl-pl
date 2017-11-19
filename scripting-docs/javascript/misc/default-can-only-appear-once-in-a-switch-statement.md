---
title: "&#39; domyślne &#39; może wystąpić tylko raz w &#39; Przełącz &#39; Instrukcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT1027
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a94100f4-6ee5-4759-b635-9d309e47111e
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e60dd1ce6b4102ab856cd3d45416175c7030e8d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="39default39-can-only-appear-once-in-a-39switch39-statement"></a>&#39; domyślne &#39; może wystąpić tylko raz w &#39; Przełącz &#39; — Instrukcja
Podjęto próbę użycia **domyślne** instrukcji więcej niż raz w instrukcji switch. W przypadku domyślnej jest zawsze ostatniej instrukcji case w instrukcji switch (jest to fall-through).  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Usuń wszystkie dodatkowe **domyślne** przypadek oświadczenia użytkownika `switch` instrukcji (Użyj na większości jeden domyślny instrukcji case w instrukcji switch).  
  
## <a name="see-also"></a>Zobacz też  
 [Switch — instrukcja](../../javascript/reference/switch-statement-javascript.md)   
 [Sterowanie przepływem programu](../../javascript/controlling-program-flow-javascript.md)   
 [JavaScript słowa zastrzeżone](../../javascript/reference/javascript-reserved-words.md)