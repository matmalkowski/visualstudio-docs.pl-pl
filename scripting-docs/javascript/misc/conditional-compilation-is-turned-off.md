---
title: Kompilacja warunkowa jest wyłączona. | Dokumentacja firmy Microsoft
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
- VS.WebClient.Help.SCRIPT1030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 59a030b0-a6c6-47f2-b90e-c0ed204d5116
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8f2eabb900e24072c8f390061b5d6081de9bc889
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24788764"
---
# <a name="conditional-compilation-is-turned-off"></a>Kompilacja warunkowa jest wyłączona
Próbowano użyć zmiennej kompilacja warunkowa bez pierwszy zwroty kompilacji warunkowej na. Włączanie kompilacja warunkowa informuje [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] kompilatora, aby zinterpretować identyfikatory począwszy jako zmienne kompilacji warunkowej. Aby to zrobić, począwszy od warunkowego kodu za pomocą instrukcji:  
  
```  
/*@cc_on @*/  
```  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Dodaj następującą instrukcję do początku warunkowego kodu:  
  
    ```JavaScript  
    /*@cc_on @*/  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilacja warunkowa](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Zmienne kompilacji warunkowej](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_on— Instrukcja](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@if— Instrukcja](../../javascript/reference/at-if-statement-javascript.md)   
 [@set— Instrukcja](../../javascript/reference/at-set-statement-javascript.md)