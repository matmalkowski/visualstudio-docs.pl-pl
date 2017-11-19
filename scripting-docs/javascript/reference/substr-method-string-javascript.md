---
title: "substr — metoda (ciąg) (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: substr
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: substr method
ms.assetid: f12541c1-2623-482e-941d-2e22bc3c4a4a
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b002bfefbeb81c534c882fa4a4720c93ccca185
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="substr-method-string-javascript"></a>substr — Metoda (Ciąg) (JavaScript)
Pobiera ciąg, zaczynając od określonej lokalizacji i o określonej długości.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
stringvar.substr(start [, length ])   
```  
  
## <a name="parameters"></a>Parametry  
 `stringvar`  
 Wymagany. Literał ciągu lub `String` obiektu, z której jest wyodrębniany podciąg.  
  
 `start`  
 Wymagany. Położenie początkowe żądaną podciąg. Indeks pierwszego znaku w ciągu wynosi zero.  
  
 `length`  
 Opcjonalny. Liczba znaków do uwzględnienia w zwrócony podciąg.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `length` jest zerowy lub ujemne, zwracany jest pustym ciągiem. Jeśli nie zostanie określony, podciąg będzie nadal występować na końcu `stringvar`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `substr` metody.  
  
```JavaScript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.substr(10, 5);    
document.write("[" + ss + "] <br>");  
  
ss = s.substr(10);  
document.write("[" + ss + "] <br>");  
  
ss = s.substr(10, -5);  
document.write("[" + ss + "] <br>");  
  
// Output:  
// [brown]   
// [brown fox jumps over the lazy dog.]   
// []  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Dotyczy**: [ciągu obiektu](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [substring — metoda (ciąg)](../../javascript/reference/substring-method-string-javascript.md)