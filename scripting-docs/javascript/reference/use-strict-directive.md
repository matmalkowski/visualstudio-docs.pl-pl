---
title: "use strict — dyrektywa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- strict_JavaScriptKeyword
- use strict
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- strict mode
- use strict directive
- use strict
ms.assetid: b532e8c9-548c-4bbe-b2fc-5459ebd62e56
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0bd951255f5d5719c3aa216965605840ba12010d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="use-strict-directive"></a>use strict — Dyrektywa
Ogranicza korzystanie z niektórych funkcji w języku JavaScript. Obsługiwane w programie Internet Explorer 10 i [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] tylko aplikacje.  
  
## <a name="syntax"></a>Składnia  
  
```JavaScript  
use strict  
```  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="example"></a>Przykład  
 Poniższy kod powoduje błąd składniowy, ponieważ w trybie z ograniczeniami wszystkie zmienne musi być zadeklarowany ze `var`.  
  
```JavaScript  
"use strict";  
function testFunction(){  
   var testvar = 4;  
    return testvar;  
}  
intvar = 5;  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Tryb z ograniczeniami](../../javascript/advanced/strict-mode-javascript.md)