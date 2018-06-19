---
title: Input — właściwość ($_) (RegExp) (JavaScript) | Dokumentacja firmy Microsoft
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
- $_
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- input property
- $_ property
ms.assetid: 88c6d1d8-56f7-4334-a7eb-e899aec9cda4
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8a447950783473d975bfe799eaa2bf18008e539e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790741"
---
# <a name="input-property--regexp-javascript"></a>input — Właściwość ($_) (RegExp) (JavaScript)
Zwraca ciąg, względem którego przeprowadzono wyszukiwania wyrażenia regularnego. Tylko do odczytu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
RegExp.input  
```  
  
## <a name="remarks"></a>Uwagi  
 Obiekt skojarzony z tą właściwością jest zawsze globalnej `RegExp` obiektu.  
  
 Wartość **wejściowych** właściwość zostanie zmodyfikowana w dowolnym momencie przeszukane parametry zostaną zmienione.  
  
 Poniższy przykład przedstawia użycie **wejściowych** właściwości:  
  
```JavaScript  
function inputDemo(){  
   var s;  
   var re = new RegExp("d(b+)(d)","ig");  
   var str = "cdbBdbsbdbdz";  
   var arr = re.exec(str);  
   s = "The string used for the match was " + RegExp.input;   
   return(s);  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Dotyczy**: [RegExp — obiekt](../../javascript/reference/regexp-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Składnia wyrażeń regularnych (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)