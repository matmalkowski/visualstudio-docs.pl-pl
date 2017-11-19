---
title: Number.isInteger (Number) (JavaScript) funkcja | Dokumentacja firmy Microsoft
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
ms.assetid: 54fcf68c-0067-4bad-af94-d7ff8c88914a
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20e1b7b463003d3a25ef64bba793b3273371266b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="numberisinteger-function-number-javascript"></a>Number.isInteger (Number) — funkcja (JavaScript)
Zwraca wartość logiczną, wskazującą, czy wartość jest liczbą całkowitą.  
  
## <a name="syntax"></a>Składnia  
  
```  
Number.isInteger(numValue)   
```  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli wartość jest liczbą całkowitą, w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **Dotyczy**: [numer obiektu](../../javascript/reference/number-object-javascript.md)  
  
## <a name="example"></a>Przykład  
  
```JavaScript  
// Returns true  
Number.isInteger(100)  
Number.isInteger(-100)  
  
// Returns false  
Number.isInteger(Number.NaN)  
Number.isInteger(Infinity)  
Number.isInteger(100 / 3)  
Number.isInteger("100")  
  
```