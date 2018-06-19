---
title: while — instrukcja (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- while_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- loop structures, while statements
- while statement
ms.assetid: d63777cf-0e1a-4555-8d3a-334381001f48
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de64bf9181a0fc86a528fa7af21216b99530f217
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791887"
---
# <a name="while-statement-javascript"></a>while — Instrukcja (JavaScript)
Wykonuje instrukcję lub serię instrukcji, dopóki nie zostanie określony warunek `false`.  
  
## <a name="syntax"></a>Składnia  
  
```  
while (expression) {  
    statements  
}   
```  
  
## <a name="parameters"></a>Parametry  
 `expression`  
 Wymagany. Wyrażenie logiczne, który jest sprawdzany przed każdej iteracji pętli. Jeśli `expression` jest `true`, pętla jest wykonywana. Jeśli `expression` jest `false`, pętla zostanie zakończony.  
  
 `statements`  
 Opcjonalny. Co najmniej jeden instrukcje do wykonania, jeśli `expression` jest `true`.  
  
## <a name="remarks"></a>Uwagi  
 `while` Instrukcji kontroli `expression` przed pętli jest wykonywany jako pierwszy. Jeśli `expression` jest `false` w tej chwili nie został wykonany pętli.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `while` instrukcji.  
  
```JavaScript  
var i = 0;  
var j = 10;  
while (i < 100) {  
    if (i == j)  
        break;  
    i++;  
}  
document.write(i);  
  
// Output: 10  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcja BREAK](../../javascript/reference/break-statement-javascript.md)   
 [Continue — instrukcja](../../javascript/reference/continue-statement-javascript.md)   
 [do... while — instrukcja](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [for — instrukcja](../../javascript/reference/for-statement-javascript.md)   
 [for... w instrukcji](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)