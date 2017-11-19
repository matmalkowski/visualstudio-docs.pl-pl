---
title: "Source — właściwość (wyrażenie regularne) (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: source
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Source property
ms.assetid: d58ac57e-fcde-49d1-bbba-e8c4218448c4
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 05bf118aec0f31de11a3df6f4b875fad3092e53d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="source-property-regular-expression-javascript"></a>source — Właściwość (wyrażenie regularne) (JavaScript)
Zwraca kopię tekst wzorzec wyrażenia regularnego. Tylko do odczytu. `rgExp` Argument jest **wyrażenia regularnego** obiektu. Może być nazwą zmiennej lub literałem.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
rgExp.source  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie **źródła** właściwości:  
  
```JavaScript  
function SourceDemo(re, s){  
   var s1;  
   // Test string for existence of regular expression.  
   if (re.test(s))  
      s1 = " contains ";  
   else  
      s1 = " does not contain ";  
   // Get the text of the regular expression itself.  
   return(s + s1 + re.source);  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Dotyczy**: [obiektu będącego wyrażeniem regularnym](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekt będący wyrażeniem regularnym](../../javascript/reference/regular-expression-object-javascript.md)   
 [Obiekt będący wyrażeniem regularnym](../../javascript/reference/regular-expression-object-javascript.md)   
 [Składnia wyrażeń regularnych (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)