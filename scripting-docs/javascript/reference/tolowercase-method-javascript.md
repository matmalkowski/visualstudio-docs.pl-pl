---
title: toLowerCase — metoda (JavaScript) | Dokumentacja firmy Microsoft
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
- toLowerCase
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toLowerCase method
ms.assetid: dfd543b9-3e7a-4f83-a391-9cde109ad6bc
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b7510e074c11cf3d3f63b965bcd6f14946dc5a16
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791701"
---
# <a name="tolowercase-method-javascript"></a>toLowerCase — Metoda (JavaScript)
Konwertuje wszystkie znaki alfabetyczne w ciągu na małe litery.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      strVariable.toLowerCase()  
"String Literal".toLowerCase()   
```  
  
## <a name="remarks"></a>Uwagi  
 `toLowerCase` — Metoda nie ma wpływu na znaki inne niż alfanumeryczne.  
  
 W poniższym przykładzie pokazano skutków `toLowerCase` metody:  
  
```JavaScript  
var str1 = "This is a STRING.";  
var str2 = str1. toLowerCase();  
document.write(str2);  
  
// Output: this is a string.  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Dotyczy**: [ciągu obiektu](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [toLocaleLowerCase — metoda (ciąg)](../../javascript/reference/tolocalelowercase-method-string-javascript.md)   
 [toUpperCase — metoda (ciąg)](../../javascript/reference/touppercase-method-string-javascript.md)