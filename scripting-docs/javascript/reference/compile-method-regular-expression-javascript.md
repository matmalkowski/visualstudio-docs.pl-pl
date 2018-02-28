---
title: "Compile — metoda (wyrażenie regularne) (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- compile
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- regular expressions, compiling
- Compile method
- compiling source code, regular expressions
ms.assetid: dc28cae3-478d-49b5-b5ea-203e5edfe195
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8b8de23a9e4f0e03fbf042195867ad9426e4c6bb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="compile-method-regular-expression-javascript"></a>compile — Metoda (wyrażenie regularne) (JavaScript)
Kompiluje wyrażenia regularnego na wewnętrzny format szybsze wykonywanie.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
rgExp.compile(pattern, [flags])   
```  
  
## <a name="parameters"></a>Parametry  
 `rgExp`  
 Wymagany. Wystąpienie **wyrażenia regularnego** obiektu. Może być nazwą zmiennej lub literałem.  
  
 *wzorzec*  
 Wymagany. Wyrażenia ciągu zawierającego wzorzec wyrażenia regularnego do skompilowania  
  
 `flags`  
 Opcjonalny. Dostępne flagi, które mogą być łączone, są:  
  
-   g (wyszukiwanie globalne dla wszystkich wystąpień elementu *wzorzec*)  
  
-   i (ignorowanie wielkości liter)  
  
-   m (wielowierszowy wyszukiwania)  
  
## <a name="remarks"></a>Uwagi  
 **Skompilować** metoda konwertuje *wzorzec* na wewnętrzny format szybsze wykonywanie. Umożliwia to efektywne korzystanie z wyrażeń regularnych w pętli, na przykład. Skompilowane wyrażenia regularnego przyspiesza rzeczy podczas wielokrotnie ponowne użycie jednego wyrażenia. Żadnych dodatkowych zalet jest uzyskane, jednak w przypadku zmiany wyrażenia regularnego.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie **skompilować** metody:  
  
```JavaScript  
function CompileDemo(){  
   var rs;  
   var s = "AaBbCcDdEeFfGgHhIiJjKkLlMmNnOoPp"  
   // Create regular expression for uppercase only.  
   var r = new RegExp("[A-Z]", "g");  
   var a1 = s.match(r)              // Find matches.  
   // Compile the regular expression for lowercase only.  
   r.compile("[a-z]", "g");  
// Find matches.  
   var a2 = s.match(r)                
   return(a1 + "\n" + a2);  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Dotyczy**: [obiektu będącego wyrażeniem regularnym](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Składnia wyrażeń regularnych (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)