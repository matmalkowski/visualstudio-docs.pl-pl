---
title: "Number — obiekt (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Number_JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Number object
ms.assetid: 76e87c37-cf6c-46cc-bafa-04be1fe3d78d
caps.latest.revision: "23"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7cbe58fdc9673a8fffe35b8b15d7edbf86ffa655
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="number-object-javascript"></a>Number — Obiekt (JavaScript)
Obiekt reprezentujący liczbę dowolnego rodzaju. Wszystkie liczby JavaScript są 64-bitowych liczb zmiennoprzecinkowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
numObj = new Number(value)  
```  
  
## <a name="parameters"></a>Parametry  
 `numObj`  
 Wymagany. Nazwa zmiennej, do której `Number` obiekt jest przypisany.  
  
 `value`  
 Wymagany. Wartość liczbowa.  
  
## <a name="remarks"></a>Uwagi  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]Tworzy `Number` obiektów, gdy zmienna jest ustawiona na wartość liczbową, na przykład `var num = 255.336;`. Rzadko jest niezbędne do utworzenia `Number` jawnie obiektów.  
  
 `Number` Obiekt ma własne właściwości i metody, oprócz właściwości i metody dziedziczone z `Object`. Numery są konwertowane na ciągi w pewnych okolicznościach, na przykład podczas dodawania lub połączonych z ciągiem, a także za pomocą numeru środków `toString` metody. Aby uzyskać więcej informacji, zobacz [Operator dodawania (+)](../../javascript/reference/addition-operator-decrement-javascript.md).  
  
 JavaScript ma kilka number — stałe. Aby uzyskać pełną listę, zobacz [stałe numer](../../javascript/reference/number-constants-javascript.md).  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="properties"></a>Właściwości  
 W poniższej tabeli wymieniono właściwości `Number` obiektu.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|[constructor — właściwość](../../javascript/reference/constructor-property-object-javascript.md)|Określa funkcję, która tworzy obiekt.|  
|[prototype — właściwość](../../javascript/reference/prototype-property-object-javascript.md)|Zwraca odwołanie do prototypu klasy obiektów.|  
  
## <a name="functions"></a>Funkcje  
 W poniższej tabeli wymieniono funkcje `Number` obiektu.  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|[Number.isFinite — funkcja](../../javascript/reference/number-isfinite-function-number-javascript.md)|Zwraca wartość logiczną, wskazującą, czy wartość jest wartością skończoną.|  
|[Number.isInteger — funkcja](../../javascript/reference/number-isinteger-function-number-javascript.md)|Zwraca wartość logiczną, wskazującą, czy wartość jest liczbą całkowitą.|  
|[Number.isNaN — funkcja](../../javascript/reference/number-isnan-function-number-javascript.md)|Zwraca wartość logiczną wskazującą, czy wartość jest wartością zarezerwowanej wartości `NaN` (nie liczba).|  
|[Number.isSafeInteger](../../javascript/reference/number-issafeinteger-number-javascript.md)|Zwraca wartość logiczną, wskazującą, czy wartość może być bezpiecznie reprezentowany w języku JavaScript.|  
  
## <a name="methods"></a>Metody  
 W poniższej tabeli przedstawiono metody `Number` obiektu.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[hasOwnProperty — metoda](../../javascript/reference/hasownproperty-method-object-javascript.md)|Zwraca wartość logiczną, która wskazuje, czy obiekt ma właściwość o określonej nazwie.|  
|[isPrototypeOf — metoda](../../javascript/reference/isprototypeof-method-object-javascript.md)|Zwraca wartość logiczną, wskazującą, czy obiekt istnieje w hierarchii prototypu innego obiektu.|  
|[propertyIsEnumerable — metoda](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Zwraca wartość logiczną, która wskazuje, czy określona właściwość jest częścią obiektu i czy jest wyliczalna.|  
|[toExponential — metoda](../../javascript/reference/toexponential-method-number-javascript.md)|Zwraca ciąg zawierający wiele reprezentowane w notacji wykładniczej.|  
|[toFixed — metoda](../../javascript/reference/tofixed-method-number-javascript.md)|Zwraca ciąg reprezentujący liczbę w notacji stałoprzecinkowe.|  
|[toLocaleString — metoda](../../javascript/reference/tolocalestring-number.md)|Zwraca obiekt konwertowana na ciąg w oparciu o bieżące ustawienia regionalne.|  
|[toPrecision — metoda](../../javascript/reference/toprecision-method-number-javascript.md)|Zwraca ciąg zawierający wiele reprezentowaną w notacji wykładniczej lub stałoprzecinkowego, na którym jest określonej liczby cyfr.|  
|[toString — metoda](../../javascript/reference/tostring-method-object-javascript.md)|Zwraca reprezentację ciągu obiektu.|  
|[valueOf — metoda](../../javascript/reference/valueof-method-object-javascript.md)|Zwraca wartość pierwotnych określonego obiektu.|  
  
## <a name="see-also"></a>Zobacz też  
 [JavaScript — obiekty](../../javascript/reference/javascript-objects.md)   
 [Math — obiekt](../../javascript/reference/math-object-javascript.md)   
 [New — Operator](../../javascript/reference/new-operator-decrementjavascript.md)