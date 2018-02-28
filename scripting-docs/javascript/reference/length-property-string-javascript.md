---
title: "length — właściwość (ciąg) (JavaScript) | Dokumentacja firmy Microsoft"
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
- length Property
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- strings [Visual Studio], length
- Length property
- length property (String)
ms.assetid: 7dbd4a0e-c24e-4561-9b5b-e75e649a10a4
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 706a7f6986086f95613e09b9a8355eb5bc2702a7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="length-property-string-javascript"></a>length — Właściwość (Ciąg) (JavaScript)
Zwraca długość `String` obiektu.  
  
> [!WARNING]
>  Ciągi języka JavaScript są niezmienne, długość ciągu nie mogą być modyfikowane.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      strVariable.length  
"String Literal".length   
```  
  
## <a name="remarks"></a>Uwagi  
 `length` Właściwość zawiera całkowitą wskazującą liczbę znaków w `String` obiektu. Ostatni znak w `String` obiekt ma indeks i`length` - 1.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób użycia `length`. Ciągi języka JavaScript są niezmienne i nie można zmodyfikować w miejscu. Jednak można zapisać odwróconej ciągu do tablicy, a następnie wywołać `join` znakiem pustym, który tworzy ciąg bez znaków separatora.  
  
```JavaScript  
var str = "every good boy does fine";  
        var start = 0;  
        var end = str.length - 1;  
        var tmp = "";  
        var arr = new Array(end);  
  
        while (end >= 0) {  
            arr[start++] = str.charAt(end--);  
        }  
  
// Join the elements of the array with a   
        var str2 = arr.join('');  
        document.write(str2);  
  
// Output: enif seod yob doog yreve  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]