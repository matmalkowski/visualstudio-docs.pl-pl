---
title: lastIndex właściwość (RegExp) (JavaScript) | Dokumentacja firmy Microsoft
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
- lastIndex
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- lastIndex property
ms.assetid: c8ae2a13-6dff-4cbe-b662-aca3d66c2a7f
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d5e24fe14d335e1494b13518543f56025625de0b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790852"
---
# <a name="lastindex-property-regexp-javascript"></a>lastIndex Właściwość (RegExp) (JavaScript)
Zwraca ciąg przeszukane pozycji znaku, w którym rozpoczyna się następnego dopasowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
RegExp.lastIndex  
```  
  
## <a name="remarks"></a>Uwagi  
 Obiekt skojarzony z tą właściwością jest zawsze globalnej `RegExp` obiektu.  
  
 `lastIndex` Właściwość jest liczony od zera, oznacza to, że indeks pierwszego znaku, wynosi zero. Wartość początkowa to -1. Wartość jest modyfikowany po każdej pomyślnego dopasowania.  
  
 `lastIndex` Właściwości jest modyfikowany przez `exec` i **testu** metody `RegExp` obiektu i `match`, **Zastąp**, i **podziału**metody `String` obiektu.  
  
 Mają zastosowanie następujące reguły wartości `lastIndex`:  
  
-   Jeśli nie zostanie odnaleziony odpowiednik `lastIndex` ma ustawioną wartość -1.  
  
-   Jeśli `lastIndex` jest większa niż długość ciągu **test** i `exec` zakończyć się niepowodzeniem i `lastIndex` ma ustawioną wartość -1.  
  
-   Jeśli `lastIndex` jest równa długości ciągu dopasowań wyrażenie regularne, jeśli wzorzec jest zgodny pusty ciąg. W przeciwnym razie dopasowania nie powiedzie się i `lastIndex` jest ustawiany na wartość -1.  
  
-   W przeciwnym razie `lastIndex` jest ustawiona w pozycji dalej po ostatniej dopasowania.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `lastIndex` właściwości. Ta funkcja iteruje po ciągu wyszukiwania i drukowania **indeksu** i `lastIndex` wartości dla każdego wyrazu w ciągu.  
  
```JavaScript  
function RegExpTest()  
{  
   var ver = Number(ScriptEngineMajorVersion() + "." + ScriptEngineMinorVersion())  
   if (ver < 5.5)  
   {  
      document.write("You need a newer version of JavaScript for this to work");  
      return;  
   }  
  
   var src = "The quick brown fox jumps over the lazy dog.";  
  
   // Create regular expression pattern with a global flag.  
   var re = /\w+/g;  
  
   // Get the next word, starting at the position of lastindex.  
   var arr;  
   while ((arr = re.exec(src)) != null)  
      {  
      // New line:  
      document.write ("<br />");    
      document.write (arr.index + "-" + re.lastIndex + " ");  
      document.write (arr);  
      }  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Dotyczy**: [RegExp — obiekt](../../javascript/reference/regexp-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Składnia wyrażeń regularnych (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)