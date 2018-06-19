---
title: Math — obiekt (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Math object
ms.assetid: 607b94cb-921c-43cd-b514-fdbc13aeced6
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f16fe4edf6a2a49db15d74abc8ebe6e53f955710
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24792184"
---
# <a name="math-object-javascript"></a>Math — Obiekt (JavaScript)
Obiekt wewnętrzny zapewnia funkcje podstawowe matematyce i stałe.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
Math.[{property | method}]  
```  
  
## <a name="parameters"></a>Parametry  
 *Właściwość*  
 Wymagany. Nazwa właściwości **matematyczne**. obiekt.  
  
 *— Metoda*  
 Wymagany. Nazwa metody **matematyczne**. obiekt.  
  
## <a name="remarks"></a>Uwagi  
 **Matematyczne** nie można utworzyć obiektu przy użyciu **nowe** operatora i zwraca błąd, jeśli użytkownik spróbuje to zrobić. Aparat skryptów tworzy po załadowaniu przez aparat. Wszystkie metody i właściwości są dostępne do skryptu przez cały czas.  
  
## <a name="requirements"></a>Wymagania  
 `Math` Obiektu została wprowadzona w systemie [!INCLUDE[jsv1text](../../javascript/reference/includes/jsv1text-md.md)].  
  
<a name="js56jsobjmathprop"></a>   
## <a name="constants"></a>Stałe  
 W poniższej tabeli wymieniono stałe `Math` obiektu.  
  
|Stała|Opis|  
|--------------|-----------------|  
|[Math.e — stała](../../javascript/reference/math-constants-javascript.md)|Stałe matematyczne e. To jest liczba Eulera w, podstawę logarytmów naturalnych.|  
|[Math.ln2 — stała](../../javascript/reference/math-constants-javascript.md)|Logarytm naturalny z 2.|  
|[Math.ln10 — stała](../../javascript/reference/math-constants-javascript.md)|Logarytm naturalny 10.|  
|[Math.log2e — stała](../../javascript/reference/math-constants-javascript.md)|E logarytmu base-2.|  
|[Math.log10e — stała](../../javascript/reference/math-constants-javascript.md)|Base — logarytm o podstawie 10 e.|  
|[Math.pi — stała](../../javascript/reference/math-constants-javascript.md)|Pi. Jest to stosunek obwodu do jego średnica okręgu.|  
|[Math.sqrt1_2 — stała](../../javascript/reference/math-constants-javascript.md)|Pierwiastek kwadratowy liczby 0,5 lub, ekwiwalentnie jeden rozdzielonych pierwiastek kwadratowy liczby 2.|  
|[Math.sqrt2 — stała](../../javascript/reference/math-constants-javascript.md)|Pierwiastek kwadratowy liczby 2.|  
  
<a name="js56jsobjmathmeth"></a>   
## <a name="functions"></a>Funkcje  
 W poniższej tabeli wymieniono funkcje `Math` obiektu.  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|[Math.Abs — funkcja](../../javascript/reference/math-abs-function-javascript.md)|Zwraca wartość bezwzględną liczby.|  
|[Math.ACOS — funkcja](../../javascript/reference/math-acos-function-javascript.md)|Zwraca cosinus liczby.|  
|[Math.ACOSH — funkcja](../../javascript/reference/math-acosh-function-javascript.md)|Zwraca arcus cosinus hiperboliczny (odwrotny cosinus hiperboliczny) dla danej liczby.|  
|[Math.ASIN — funkcja](../../javascript/reference/math-asin-function-javascript.md)|Zwraca arcus sinus liczby.|  
|[Math.ASINH — funkcja](../../javascript/reference/math-asinh-function-javascript.md)|Zwraca odwrotny sinus hiperboliczny liczby.|  
|[Math.ATAN — funkcja](../../javascript/reference/math-atan-function-javascript.md)|Zwraca arcus tangens liczby.|  
|[Math.ATAN2 — funkcja](../../javascript/reference/math-atan2-function-javascript.md)|Zwraca kąt (w radianach) osi X, do punktu o podany współrzędnych y i x.|  
|[Math.ATANH — funkcja](../../javascript/reference/math-atanh-function-javascript.md)|Zwraca odwrotny tangens hiperboliczny liczby.|  
|[Math.ceil — funkcja](../../javascript/reference/math-ceil-function-javascript.md)|Zwraca najmniejsza liczba całkowita, która jest większa niż lub równa podane wyrażenie liczbowe.|  
|[Math.cos — funkcja](../../javascript/reference/math-cos-function-javascript.md)|Zwraca cosinus liczby.|  
|[Math.COSH — funkcja](../../javascript/reference/math-cosh-function-javascript.md)|Zwraca cosinus hiperboliczny liczby.|  
|[Math.EXP — funkcja](../../javascript/reference/math-exp-function-javascript.md)|Zwraca *e* (podstawę logarytmów naturalnych) podniesionej do potęgi.|  
|[Math.expm1 — funkcja](../../javascript/reference/math-expm1-function-javascript.md)|Zwraca wynik odejmowania 1 z (podstawę logarytmów naturalnych) e podniesionej do potęgi).|  
|[Math.Floor — funkcja](../../javascript/reference/math-floor-function-javascript.md)|Zwraca największa liczba całkowita, która jest mniejsza niż podany wyrażenia liczbowego.|  
|[Math.hypot — funkcja](../../javascript/reference/math-hypot-function-javascript.md)|Zwraca pierwiastek kwadratowy liczby sumę kwadratów argumentów.|  
|[Math.imul — funkcja](../../javascript/reference/math-imul-function-javascript.md)|Zwraca iloczyn dwóch liczb, które są traktowane jako 32-bitowych liczb całkowitych ze znakiem.|  
|[Math.log — funkcja](../../javascript/reference/math-log-function-javascript.md)|Zwraca logarytm naturalny liczby.|  
|[Math.log1p — funkcja](../../javascript/reference/math-log1p-function-javascript.md)|Zwraca logarytm naturalny 1 + liczbą.|  
|[Math.LOG10 — funkcja](../../javascript/reference/math-log10-function-javascript.md)|Zwraca logarytm 10 dla danej liczby.|  
|[Math.log2 — funkcja](../../javascript/reference/math-log2-function-javascript.md)|Zwraca logarytm 2 dla danej liczby.|  
|[Math.max — funkcja](../../javascript/reference/math-max-function-javascript.md)|Zwraca wartość większą niż dwóch wyrażeń liczbowych dostarczony.|  
|[Math.min — funkcja](../../javascript/reference/math-min-function-javascript.md)|Zwraca mniejszy z dwóch liczb dostarczony.|  
|[Math.Pow — funkcja](../../javascript/reference/math-pow-function-javascript.md)|Zwraca wartość wyrażenia podstawowe podniesione do określonej potęgi.|  
|[Math.Random — funkcja](../../javascript/reference/math-random-function-javascript.md)|Zwraca pseudolosowych liczbę z przedziału od 0 do 1.|  
|[Math.round — funkcja](../../javascript/reference/math-round-function-javascript.md)|Zwraca wartość wyrażenia liczbowego określonego zaokrąglona do najbliższej liczby całkowitej.|  
|[Math.sign — funkcja](../../javascript/reference/math-sign-function-javascript.md)|Zwraca znak liczby, wskazującą, czy liczba jest dodatnia, ujemną lub 0.|  
|[Math.sin — funkcja](../../javascript/reference/math-sin-function-javascript.md)|Zwraca sinus liczby.|  
|[Math.SINH — funkcja](../../javascript/reference/math-sinh-function-javascript.md)|Zwraca odwrotny sinus hiperboliczny liczby.|  
|[Math.SQRT — funkcja](../../javascript/reference/math-sqrt-function-javascript.md)|Zwraca pierwiastek kwadratowy z liczby.|  
|[Math.tan — funkcja](../../javascript/reference/math-tan-function-javascript.md)|Zwraca tangens liczby.|  
|[Math.TANH — funkcja](../../javascript/reference/math-tanh-function-javascript.md)|Zwraca tangens hiperboliczny liczby.|  
|[Math.TRUNC — funkcja](../../javascript/reference/math-trunc-function-javascript.md)|Zwraca część całkowitą liczbą usunięcie wszelkich cyfr ułamkowych.|  
  
## <a name="see-also"></a>Zobacz też  
 [JavaScript — obiekty](../../javascript/reference/javascript-objects.md)   
 [Number — obiekt](../../javascript/reference/number-object-javascript.md)