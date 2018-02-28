---
title: "TRIM — metoda (ciąg) (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- trim method
ms.assetid: 03d38c7e-25cd-4ede-b58e-1a10b5249bab
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de358981cfbf569ef35be95b55b3e9856027df35
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="trim-method-string-javascript"></a>trim — Metoda (Ciąg) (JavaScript)
Usuwa z ciągu początkowe i końcowe białe znaki oraz znaki końca wiersza.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
stringObj.trim()  
```  
  
## <a name="parameters"></a>Parametry  
 `stringObj`  
 Wymagany. A `String` obiektu lub literałem ciągu. Ten ciąg nie jest modyfikowany przez `trim` metody.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca oryginalny ciąg z usuniętymi początkowymi i końcowymi białymi znakami oraz znakami końca wiersza.  
  
## <a name="remarks"></a>Uwagi  
 Usuwane znaki to spacja, tabulator, wysuw strony, powrót karetki i wysuw wiersza. Zobacz [znaki specjalne](../../javascript/advanced/special-characters-javascript.md) Aby uzyskać pełną listę znaków terminatora biały znak lub wiersza.  
  
 Na przykład pokazujący sposób implementować metodę przycinania zobacz [prototypy i dziedziczenie](../../javascript/advanced/prototypes-and-prototype-inheritance.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `trim` metody.  
  
```JavaScript  
var message = "    abc def     \r\n  ";  
  
document.write("[" + message.trim() + "]");  
document.write("<br/>");  
document.write("length: " + message.trim().length);  
  
// Output:  
//  [abc def]  
//  length: 7  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Znaki specjalne](../../javascript/advanced/special-characters-javascript.md)   
 [String — obiekt](../../javascript/reference/string-object-javascript.md)   
 [Przewijanie, przesuwać i powiększać przykładowej aplikacji](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)