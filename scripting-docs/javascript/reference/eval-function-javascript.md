---
title: Eval — funkcja (JavaScript) | Dokumentacja firmy Microsoft
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
- eval
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- eval function
- parsing, code
- parser
ms.assetid: 85587e39-9325-4b75-b9f9-9d7d475a2120
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 388e486f58bb70fd192701060a5faefaed8bd98e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790441"
---
# <a name="eval-function-javascript"></a>eval — Funkcja (JavaScript)
Oblicza [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] kod i go uruchomi.  
  
## <a name="syntax"></a>Składnia  
  
```  
eval(codeString)   
```  
  
## <a name="parameters"></a>Parametry  
 `codeString`  
 Wymagany. A `String` wartości, która zawiera nieprawidłowy [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] kodu.  
  
## <a name="remarks"></a>Uwagi  
 `eval` Funkcja umożliwia dynamiczne wykonanie [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] kod źródłowy.  
  
 `codeString` Przez zostanie przeanalizowany ciąg [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] analizatora składni i wykonywane.  
  
 Kod przekazany do `eval` funkcja jest wykonywana w tym samym kontekście co wywołanie `eval` funkcji.  
  
 Jeśli to możliwe, użyj [funkcja JSON.parse](../../javascript/reference/json-parse-function-javascript.md) można zdeserializować tekst JavaScript Object Notation (JSON). `JSON.parse` Funkcji jest bardziej bezpieczne i wykonuje szybciej niż `eval` funkcji.  
  
## <a name="example"></a>Przykład  
 Poniższy kod inicjuje zmienną `myDate` Data testu.  
  
```JavaScript  
var dateFn = "Date(1971,3,8)";  
var myDate;  
eval("myDate = new " + dateFn + ";");  
  
document.write(myDate);  
  
// Output: Thu Apr 8 00:00:00 PDT 1971  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Dotyczy**: [obiekt globalny](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [String — obiekt](../../javascript/reference/string-object-javascript.md)