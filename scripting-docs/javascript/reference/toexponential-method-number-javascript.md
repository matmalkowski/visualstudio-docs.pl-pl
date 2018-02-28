---
title: "toExponential — metoda (numer) (JavaScript) | Dokumentacja firmy Microsoft"
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
- toExponential
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toExponential method
ms.assetid: 7c4a6d84-3c1f-4cc4-a67d-7753e5d4ed66
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fff2f2bc0c443fa9308c8d01dcea42a3cec9ff04
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="toexponential-method-number-javascript"></a>toExponential — Metoda (Numer) (JavaScript)
Reprezentuje liczbę w notacji wykładniczej.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
numObj. toExponential([fractionDigits])  
```  
  
## <a name="parameters"></a>Parametry  
 `numObj`  
 Wymagany. A **numer** obiektu.  
  
 `fractionDigits`  
 Opcjonalny. Liczba cyfr po punkcie dziesiętnym. Musi być z zakresu 0 - 20 włącznie.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca reprezentację ciągu z liczbą w notacji wykładniczej. Ciąg zawiera jedną cyfrę przed separatorem dziesiętnym i może zawierać `fractionDigits` cyfry po nim.  
  
 Jeśli `fractionDigits` nie zostanie podany, `toExponential` metoda zwraca należy jednoznacznie określić numer dowolną liczbę cyfr.  
  
## <a name="example"></a>Przykład  
  
```JavaScript  
var num = new Number(123);  
var exp = num.toExponential();  
document.write(exp);  
document.write("<br/>");  
  
num = new Number(123.456);  
exp = num.toExponential(5);  
document.write(exp);  
  
// Output:   
// 1.23e+2  
// 1.23456e+2  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Dotyczy**: [numer obiektu](../../javascript/reference/number-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [toFixed — metoda (numer)](../../javascript/reference/tofixed-method-number-javascript.md)   
 [toPrecision — metoda (numer)](../../javascript/reference/toprecision-method-number-javascript.md)