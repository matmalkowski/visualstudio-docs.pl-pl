---
title: Właściwość length (funkcja) (JavaScript) | Dokumentacja firmy Microsoft
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
- length Property
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Length property
- length property (function)
ms.assetid: fdc8e1c9-0dac-4e1b-ba3a-11073c37ef63
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4fbd0334c18da2c6ef8de8366555d79f791e6855
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790858"
---
# <a name="length-property-function-javascript"></a>length — Właściwość (Funkcja) (JavaScript)
Pobiera liczbę argumentów zdefiniowany dla funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
functionName.length  
```  
  
## <a name="remarks"></a>Uwagi  
 Wymagane *functionName* jest nazwa funkcji.  
  
 **Długość** właściwość funkcji jest inicjowana przez aparat skryptów do liczby argumentów w definicji funkcji, gdy jest tworzone wystąpienie funkcji.  
  
 Co się dzieje, gdy funkcja jest wywoływana z liczbą argumentów jest inna niż wartość jego **długość** właściwość zależy od funkcji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie **długość** właściwości:  
  
```JavaScript  
function ArgTest(a, b){  
    var s = "";  
  
    s += "Expected Arguments: " + ArgTest.length;  
    s += "<br />";  
    s += "Passed Arguments: " + arguments.length;  
  
    return s;  
}  
  
document.write(ArgTest(1, 2));  
  
// Output:   
// Expected Arguments: 2  
// Passed Arguments: 2  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [arguments — właściwość (funkcja)](../../javascript/reference/arguments-property-function-javascript.md)   
 [length — właściwość (tablica)](../../javascript/reference/length-property-array-javascript.md)   
 [length — właściwość (ciąg)](../../javascript/reference/length-property-string-javascript.md)