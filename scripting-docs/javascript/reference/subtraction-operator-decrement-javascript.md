---
title: Operator odejmowania (-) (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '-'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '- operator, about - operator'
- '- operator'
- negation operator
- subtraction operator, syntax
- arithmetic operators, subtraction
- operators, subtraction
ms.assetid: cd0681d3-15cd-49fe-b4dd-e087de55d778
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb79aab0a57c733871dbfc73ac96c7ddbf4db37c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="subtraction-operator---javascript"></a>Operator odejmowania (-) (JavaScript)
Odejmuje wartość jednego wyrażenia z innego lub udostępnia jednoargumentowy Negacja jedno wyrażenie.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
result = number1 - number2;  
```  
  
## <a name="parameters"></a>Parametry  
 *wynik*  
 Wszelkie liczbowa zmiennej.  
  
 `number`  
 Dowolne wyrażenie liczbowe.  
  
 `number1`  
 Dowolne wyrażenie liczbowe.  
  
 `number2`  
 Dowolne wyrażenie liczbowe.  
  
## <a name="remarks"></a>Uwagi  
 W składni 1  **-**  operator to operator odejmowania arytmetyczne, używany do obliczenia różnicy między dwiema liczbami. W składni 2  **-**  operator służy jako Jednoargumentowy operator negacji do wskazywania ujemną wartość wyrażenia.  
  
 W składni 2 podobnie jak w przypadku wszystkie operatory jednoargumentowe wyrażenia są obliczane w następujący sposób:  
  
-   Jeśli zastosowano do niezdefiniowanego lub `null` wyrażenia, błędów czasu wykonywania jest wywoływane.  
  
-   Obiekty są konwertowane na ciągi.  
  
-   Ciągi są konwertowane na liczby, jeśli to możliwe. W przeciwnym razie błąd czasu wykonywania.  
  
-   Wartości logiczna są traktowane jako cyfry (0, jeśli jest to wartość false, 1, jeśli ma wartość true).  
  
 Operator jest stosowany do wynikowa liczba. W składni 2, jeśli wynikowa liczba jest różna od zera *wynik* jest równa liczbie wynikowy przy użyciu swojego konta cofnąć. Jeśli wynikowa liczba wynosi zero, *wynik* wynosi zero.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Operator przypisania odejmowania (-)](../../javascript/reference/subtraction-assignment-operator-decrement-equal-javascript.md)   
 [Kolejność wykonywania działań](../../javascript/operator-subtractprecedence-javascript.md)   
 [Podsumowanie dla operatorów (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)