---
title: "toPrecision — metoda (numer) (JavaScript) | Dokumentacja firmy Microsoft"
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
- toPrecision
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toPrecision method
ms.assetid: ac13c82f-1038-447a-823f-f755bba535ca
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eeab7642dcd88677d1b5a7102e3cf342d7ee1d29
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="toprecision-method-number-javascript"></a>toPrecision — Metoda (Numer) (JavaScript)
Reprezentuje numer w notacji wykładniczej lub stałoprzecinkowego z określonej liczby cyfr.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
numObj.toPrecision([precision])  
```  
  
## <a name="parameters"></a>Parametry  
 `numObj`  
 Wymagany. A `Number` obiektu.  
  
 `precision`  
 Opcjonalny. Liczba cyfr znaczących. Musi być z zakresu 1-21, włącznie.  
  
## <a name="return-value"></a>Wartość zwracana  
 W przypadku numerów w notacji wykładniczej `precision` - 1 zwracane są cyfr po punkcie dziesiętnym. W przypadku numerów w notacji stałej `precision` cyfr znaczących są zwracane.  
  
 Jeśli `precision` nie jest podany lub jest **Niezdefiniowany**, **toString** metoda jest wywoływana zamiast tego.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób użycia `toPrecision`.  
  
```JavaScript  
var num = new Number(123);  
var prec = num.toPrecision();  
document.write(prec);  
document.write("<br/>");  
  
num = new Number(123.456);  
prec = num.toPrecision(5);  
document.write(prec);  
  
// Output:  
// 123  
// 123.46  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Dotyczy**: [numer obiektu](../../javascript/reference/number-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [toFixed — metoda (numer)](../../javascript/reference/tofixed-method-number-javascript.md)   
 [toExponential — metoda (numer)](../../javascript/reference/toexponential-method-number-javascript.md)