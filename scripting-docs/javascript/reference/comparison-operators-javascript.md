---
title: "Operatory porównania (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Comparison
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- comparison operators, script
- greater than operator
- comparison operators
- greater than or equal to operator
- inequity operator
- identity operator
ms.assetid: 084f90f0-d010-47cf-96dd-13d637fc9b68
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 067d570523fc2241b4f2e0442785a49aedb15200
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="comparison-operators-javascript"></a>Operatory porównania (JavaScript)
Zwraca wartość logiczną wskazującą wyniku porównania.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
expression1 comparisonoperator expression2  
```  
  
## <a name="parameters"></a>Parametry  
 `expression1`  
 Dowolne wyrażenie.  
  
 `comparisonoperator`  
 Dowolny operator porównania.  
  
 `expression2`  
 Dowolne wyrażenie.  
  
## <a name="remarks"></a>Uwagi  
 Podczas porównywania ciągów, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] używa wartości wyrażenia ciągu znaków Unicode.  
  
 Poniżej opisano, jak różne grupy operatorów zachowują się w zależności od typu i wartości `expression1` i `expression2`:  
  
 Operatory relacyjne: `<`, `>`, `<=`,`>=`  
  
-   Próba konwersji zarówno `expression1` i `expression2` na liczby.  
  
-   Jeśli oba wyrażenia są ciągami, wykonaj porównania ciągów.  
  
-   Jeśli jedno z wyrażeń ma `NaN`, zwróć `false`.  
  
-   Ujemna zero jest równa zero dodatnie.  
  
-   Nieskończoności ujemnej jest mniejsza niż wszystko wraz z tym elementem.  
  
-   Nieskończoności dodatniej jest większa niż wszystko wraz z tym elementem.  
  
 Operatory porównania: `==`,`!=`  
  
-   W przypadku różnych rodzajów dwóch wyrażeń spróbuj przekonwertować je na ciąg, liczbę lub wartość logiczną.  
  
-   `NaN`nie jest równa niczego wraz z tym elementem.  
  
-   Ujemna zero jest równa zero dodatnie.  
  
-   `null`równa się zarówno `null` i `undefined`.  
  
-   Wartości są traktowane jako równe, jeśli są one identycznych ciągów, wartość liczbowa odpowiednik liczby, tego samego obiektu, identyczne wartości logiczne, lub (jeśli różne typy) może zostać przekształcone w jeden z tych sytuacji.  
  
-   Co inne porównania jest uważany za nierówne.  
  
 Operatory tożsamości: `===`,`!==`  
  
 Tych operatorów działają tak samo, jak operatory równości, z tą różnicą, że odbywa się bez konwersji typu. Jeśli typy oba wyrażenia nie są takie same, te wyrażenia zawsze zwracają `false`.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kolejność wykonywania działań](../../javascript/operator-subtractprecedence-javascript.md)   
 [Podsumowanie dla operatorów (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)