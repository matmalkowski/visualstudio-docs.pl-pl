---
title: "caller — właściwość (funkcja) (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: caller
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- caller property
- function calls, functions that are executing
ms.assetid: ae210853-7160-4102-9cfd-ab489f180ce1
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c6eef1b8304612c2ed16a4cc389bf3b2a28b70f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="caller-property-function-javascript"></a>caller — Właściwość (Funkcja) (JavaScript)
Pobiera funkcji, która wywołała bieżącej funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
functionName.caller  
```  
  
## <a name="remarks"></a>Uwagi  
 `functionName` Obiekt o nazwie żadnej wykonuje funkcji.  
  
 `caller` Właściwość jest zdefiniowana dla funkcji tylko podczas wykonuje funkcji. Jeśli funkcja jest wywoływana od góry poziom [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] program, `caller` zawiera `null`.  
  
 Jeśli `caller` właściwość jest używana w kontekście ciągu, wynikiem jest taki sam jak `functionName`.`toString`, oznacza to, że jest wyświetlany tekst decompiled funkcji.  
  
 Poniższy przykład przedstawia użycie `caller` właściwości:  
  
```JavaScript  
function CallLevel(){  
   if (CallLevel.caller == null)  
      return("CallLevel was called from the top level.");  
   else  
      return("CallLevel was called by another function.");  
}  
  
document.write(CallLevel());  
  
// Output: CallLevel was called from the top level.  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Function — instrukcja](../../javascript/reference/function-statement-javascript.md)