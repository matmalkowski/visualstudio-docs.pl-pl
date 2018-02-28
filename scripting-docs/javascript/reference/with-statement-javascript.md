---
title: "with — instrukcja (JavaScript) | Dokumentacja firmy Microsoft"
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
- with_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- With statement
ms.assetid: 892c7621-ae9e-4c10-8adb-05532274b1ca
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 35d49b13261c66cde0ecd53517a99361f6aecb79
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="with-statement-javascript"></a>with — Instrukcja (JavaScript)
Określa domyślny obiekt dla instrukcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
with (object) {  
    statements  
}   
```  
  
## <a name="parameters"></a>Parametry  
 `object`  
 Domyślny obiekt.  
  
 `statements`  
 Co najmniej jeden instrukcje, dla którego `object` jest domyślny obiekt.  
  
## <a name="remarks"></a>Uwagi  
 `with` Instrukcja jest najczęściej używany do zmniejszyć ilość kodu, które trzeba zapisać w niektórych sytuacjach.  
  
> [!WARNING]
>  Korzystanie z `with` jest niedozwolone w trybie z ograniczeniami. Korzystanie z `with` wprowadzić kod trudniejsze do odczytu i debugowania i ogólnie należy unikać.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie `Math` obiekt jest używany wielokrotnie:  
  
```JavaScript  
x = Math.cos(3 * Math.PI) + Math.sin(Math.LN10)   
y = Math.tan(14 * Math.E)  
```  
  
## <a name="example"></a>Przykład  
 Jeśli przepisywania przykład aby użyć `with` instrukcję kodu staje się bardziej zwięzły:  
  
```JavaScript  
with (Math){  
   x = cos(3 * PI) + sin (LN10)    
   y = tan(14 * E)  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Ta instrukcja](../../javascript/reference/this-statement-javascript.md)