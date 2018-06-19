---
title: String.fromcodepoint — funkcja (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 7c4c057b-c67a-4b10-afdd-4f75c7c5988c
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0905b392606bec9fb59b08a04129ce30cb013db1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791287"
---
# <a name="stringfromcodepoint-function-javascript"></a>String.fromCodePoint — funkcja (JavaScript)
Zwraca ciąg skojarzone z punkt kodu Unicode UTF-16.  
  
## <a name="syntax"></a>Składnia  
  
```  
String.fromCodePoint(...codePoints);  
```  
  
#### <a name="parameters"></a>Parametry  
 `...codePoints`  
 Wymagany. Parametr rest, który określa co najmniej jedna wartość punktu kodu UTF-16.  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja zwraca `RangeError` wyjątek Jeśli `...codePoints` nie jest prawidłowy punkt kodu UTF-16.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `fromCodePoint` funkcji.  
  
```JavaScript  
var str1 = String.fromCodePoint(0x20BB7);  
var str2 = String.fromCodePoint(98);  
var str3 = String.fromCodePoint(97, 98, 99);  
  
if(console && console.log) {  
    console.log(str1);  
    console.log(str2);  
    console.log(str3);  
}  
  
// Output:  
// 𠮷  
// b  
// abc   
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]