---
title: "var — instrukcja (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/22/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: var_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- declaring variables, var statement
- var statement
ms.assetid: 56f900af-a5c4-4667-9664-5956d30f0aae
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 839b6904fa59b6f4ea9a5c4d8e00213cd351517a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="var-statement-javascript"></a>var — Instrukcja (JavaScript)
Deklaruje zmienną.  
  
## <a name="syntax"></a>Składnia  
  
```  
var variable1 = value1  
```  
  
## <a name="parameters"></a>Parametry  
 `variable1`  
 Nazwa zmiennej został zadeklarowany.  
  
 `value1`  
 Wartość początkowa przypisaną do zmiennej.  
  
## <a name="remarks"></a>Uwagi  
 Użyj `var` instrukcji do deklarowania zmiennych. Można przypisać wartości do zmiennych przy deklarowaniu je lub później w skrypcie.  
  
 Zmienna została zadeklarowana po raz pierwszy jest wyświetlana w skrypcie.  
  
 Można zadeklarować zmiennej, bez użycia `var` — słowo kluczowe i przypisz jej wartość. Jest to nazywane *niejawne deklaracji*, i nie jest zalecane. Deklaracja niejawne daje zmiennej zakresu globalnego. Deklaracja zmiennej na poziomie procedury, zwykle nie chcesz ma zasięg globalny. Aby uniknąć, której będzie zmienne globalne, należy użyć `var` — słowo kluczowe w Twojej deklaracja zmiennej.  
  
 Jeśli nie zainicjować zmiennej użytkownika w `var` instrukcji, zostaje automatycznie przypisany [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] wartość `undefined`.  
  
## <a name="example"></a>Przykład  
 Poniższe przykłady przedstawiają użycie `var` instrukcji.  
  
```JavaScript  
var index;  
var name = "Thomas Jefferson";  
var answer = 42, counter, numpages = 10;  
var myarray = new Array();  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Function — instrukcja](../../javascript/reference/function-statement-javascript.md)   
 [New — Operator](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Array — obiekt](../../javascript/reference/array-object-javascript.md)   
 [Zmienne](../../javascript/variables-javascript.md)