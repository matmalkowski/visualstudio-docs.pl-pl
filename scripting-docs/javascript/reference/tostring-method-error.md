---
title: "toString — metoda (błąd) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 5d6d9712-c06d-4b31-9bc9-e46f6bb5cd38
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d774ff8c0f5338f4178b2262bf8ac8cadc074453
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="tostring-method-error"></a>toString — Metoda (Błąd)
Zwraca reprezentację ciągu wystąpił błąd.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
error.toString()  
```  
  
## <a name="parameters"></a>Parametry  
 `date`  
 Wymagany. Błąd do reprezentowania jako ciąg.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca "Błąd:" oraz komunikat o błędzie.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `toString` metody z powodu błędu.  
  
```JavaScript  
var myError = new Error();  
myError.message = "My Error";  
var errorString = myError.toString();  
document.write(errorString);  
  
// Output: Error: My Error  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]