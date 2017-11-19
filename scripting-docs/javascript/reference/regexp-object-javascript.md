---
title: "RegExp — obiekt (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: RegExp
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- RegExp object, overview
- RegExp object
ms.assetid: 7f6b1073-8cbb-49ed-94b6-56833ba663c5
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b7319e4556721bcfd397061ce525acfb3278c6b9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="regexp-object-javascript"></a>RegExp — Obiekt (JavaScript)
Obiekt globalne wewnętrzny przechowuje informacje o wynikach wzorzec wyrażenia regularnego jest zgodny.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
RegExp.property   
```  
  
## <a name="remarks"></a>Uwagi  
 Wymagane *właściwości* argument może być jednym z `RegExp` właściwości obiektu.  
  
 `RegExp` Obiektu nie można tworzyć bezpośrednio, ale jest zawsze dostępne do użycia. Ukończenie wyszukiwania pomyślne wyrażenia regularnego początkowej wartości różnych właściwości `RegExp` obiektu są następujące:  
  
|Właściwość|Skrócona|Wartość początkowa|  
|--------------|---------------|-------------------|  
|indeks||-1|  
|dane wejściowe|$_|Pusty ciąg.|  
|lastIndex||-1|  
|lastMatch|$&|Pusty ciąg.|  
|lastParen|$+|Pusty ciąg.|  
|leftContext|$`|Pusty ciąg.|  
|rightContext|$'|Pusty ciąg.|  
|$1 - $9|$1 - $9|Pusty ciąg.|  
  
 Jego właściwości mają niezdefiniowana jako ich wartość dopiero po ukończeniu wyszukiwania pomyślne wyrażenia regularnego.  
  
 Globalny `RegExp` obiekt nie należy mylić z **wyrażenia regularnego** obiektu. Nawet jeśli ich dźwiękowej jak samo, są one oddzielne. Właściwości globalne `RegExp` obiekt zawiera stale zaktualizowane informacje o każdym dopasowaniu po wystąpieniu, podczas właściwości **wyrażenia regularnego** obiekt zawiera tylko informacje o występujących dopasowań z tym wystąpieniem **wyrażenie regularne**.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wykonuje wyszukiwanie wyrażenia regularnego. Wyświetla wyniki pasujące i submatches z globalnej `RegExp` obiektu i z tablicy, która jest zwracana w wyniku `exec` metody.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
<a name="js56jsobjregexpprop"></a>   
## <a name="properties"></a>Właściwości  
 [$1... $9 — właściwości](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md) &#124; [właściwość indeksu](../../javascript/reference/index-property-regexp-javascript.md) &#124; [input — właściwość](../../javascript/reference/input-property-dollar-regexp-javascript.md) &#124; [lastIndex właściwość](../../javascript/reference/lastindex-property-regexp-javascript.md) &#124; [lastMatch właściwość](../../javascript/reference/lastmatch-property-dollar-regexp-javascript.md) &#124; [lastParen właściwość](../../javascript/reference/lastparen-property-dollar-regexp-javascript.md) &#124; [leftContext właściwość](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md) &#124; [rightContext właściwość](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)  
  
## <a name="methods"></a>Metody  
 `RegExp` Obiekt nie ma żadnych metod.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekt będący wyrażeniem regularnym](../../javascript/reference/regular-expression-object-javascript.md)   
 [Składnia wyrażeń regularnych (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [String — obiekt](../../javascript/reference/string-object-javascript.md)