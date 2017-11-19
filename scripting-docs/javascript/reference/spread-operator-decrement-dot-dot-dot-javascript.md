---
title: Operator rozwijania (...) (JavaScript) | Dokumentacja firmy Microsoft
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
ms.assetid: 10263a4c-bd27-4d87-9917-fb4b6bf373db
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a07d480360441906c445faa196f6d7771f97d75d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="spread-operator--javascript"></a>Operator rozwijania (...) (JavaScript)
Pozwala części tablicy literału, aby można było zainicjować iterable wyrażenia (np. innej tablicy literału) i umożliwia wyrażenie można rozszerzyć, aby wiele argumentów (w wywołaniach funkcji).  
  
## <a name="syntax"></a>Składnia  
  
```  
var array = [[arg0ToN ,] ...iterable [, arg0ToN]]  
func([args ,] ...iterable [, args | ...iterable])  
  
```  
  
## <a name="parameters"></a>Parametry  
 `iterable`  
 Wymagany. Obiekt iterable.  
  
 `arg0ToN`  
 Opcjonalny. Co najmniej jeden element literał tablicy.  
  
 `args`  
 Opcjonalny. Jeden lub więcej argumentów do funkcji.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji dotyczących Iteratory, zobacz [Iteratory i generatory](../../javascript/advanced/iterators-and-generators-javascript.md). Aby uzyskać więcej informacji na temat używania operator rozpiętości jako parametru rest, zobacz [funkcji](../../javascript/functions-javascript.md).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie kodu stosowania operator rozpiętości jest odróżniające przy użyciu `concat` metody.  
  
```JavaScript  
var a, b, c, d, e;  
a = [1,2,3];  
b = "dog";  
c = [42, "cat"];  
  
// Using the concat method.  
d = a.concat(b, c);  
  
// Using the spread operator.  
e = [...a, b, ...c];  
  
console.log(d);  
console.log(e);  
  
// Output:  
// 1, 2, 3, "dog", 42, "cat"  
// 1, 2, 3, "dog", 42, "cat"  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia sposób użycia operator rozpiętości w wywołaniu funkcji. W tym przykładzie literały macierzy dwa są przekazywane do funkcji przy użyciu operatora rozpowszechniania i tablic są rozwijane do wielu argumentów.  
  
```JavaScript  
function f(a, b, c, x, y, z) {  
  return a + b + c + x + y + z;  
}  
  
var args = [1, 2, 3];  
console.log(f(...args, 4, ...[5, 6]));  
  
// Output:  
// 21  
  
```  
  
## <a name="example"></a>Przykład  
 Przy użyciu operatorów rozpowszechniania, można uprościć kod, który wcześniej wymagane użycie `apply`.  
  
```JavaScript  
function f(x, y, z) {  
    return x + y + z;  
}  
  
var args = [1, 2, 3];  
  
// Old method  
f.apply(this, args);  
// New method  
f(...args);  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kolejność wykonywania działań](../../javascript/operator-subtractprecedence-javascript.md)   
 [Podsumowanie dla operatorów (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)