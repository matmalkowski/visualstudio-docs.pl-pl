---
title: toFixed — metoda (numer) (JavaScript) | Dokumentacja firmy Microsoft
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
- toFixed
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toFixed method
ms.assetid: b5f03400-865e-4ab2-818c-f734c0f6d6f0
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd51dd67632f4e6417fee72fd19575025423bbf1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791629"
---
# <a name="tofixed-method-number-javascript"></a>toFixed — Metoda (Numer) (JavaScript)
Reprezentuje liczbę w notacji stałoprzecinkowe.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
numObj.toFixed([fractionDigits])  
```  
  
## <a name="parameters"></a>Parametry  
 `numObj`  
 Wymagane A `Number` obiektu.  
  
 `fractionDigits`  
 Opcjonalny. Liczba cyfr po punkcie dziesiętnym. Musi być z zakresu 0 - 20 włącznie.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca reprezentację ciągu z liczbą w notacji stałoprzecinkowe zawierający `fractionDigits` cyfr po punkcie dziesiętnym.  
  
 Jeśli `fractionDigits` nie jest podany lub **Niezdefiniowany**, wartością domyślną jest zero.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób użycia `toFixed`.  
  
```JavaScript  
var num = new Number(123);  
var fix = num.toFixed();  
document.write(fix);  
document.write("<br/>");  
  
num = new Number(123.456);  
fix = num.toFixed(5);  
document.write(fix);  
  
// Output:  
// 123  
123.45600  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Dotyczy**: [numer obiektu](../../javascript/reference/number-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [toExponential — metoda (numer)](../../javascript/reference/toexponential-method-number-javascript.md)   
 [toPrecision — metoda (numer)](../../javascript/reference/toprecision-method-number-javascript.md)