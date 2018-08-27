---
title: 'CA2219: Nie zgłaszaj wyjątków w klauzulach wyjątków | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
helpviewer_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
ms.assetid: 7b9b0bee-4e8e-49a4-8c40-52142b49061f
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3f3ea7368026e2e120e877a8689319762fa2b55e
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2018
ms.locfileid: "42900404"
---
# <a name="ca2219-do-not-raise-exceptions-in-exception-clauses"></a>CA2219: Nie zgłaszaj wyjątków w klauzulach wyjątków
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA2219: Nie zgłaszaj wyjątków w klauzulach wyjątków](https://docs.microsoft.com/visualstudio/code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses).

|||
|-|-|
|TypeName|DoNotRaiseExceptionsInExceptionClauses|
|CheckId|CA2219|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału, istotne|

## <a name="cause"></a>Przyczyna
 Wyjątek jest generowany z `finally`, filtr lub klauzuli fault.

## <a name="rule-description"></a>Opis reguły
 Gdy wyjątek jest zgłaszany w klauzuli wyjątek, zwiększa znacznie utrudnia debugowanie.

 Gdy wyjątek jest zgłaszany w `finally` lub klauzuli fault ukrywa aktywny wyjątek, jeśli jest obecny. Dzięki temu można trudno wykrycie i zdebugowanie pierwotnego błędu.

 Gdy wyjątek jest zgłaszany w klauzuli filtru, środowisko uruchomieniowe dyskretnie przechwytuje wyjątek i powoduje, że filtr na wartość false. Nie istnieje żaden sposób odróżnić filtr oceny false, a wyjątek jest wyrzuca wyjątków z filtru. Utrudnia to wykrywanie i debugowanie błędów w logice filtru.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby rozwiązać problem to naruszenie tej zasady, nie jawnie zgłaszała wyjątku z `finally`, filtr lub klauzuli fault.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Brak żadnych scenariuszy, w których wyjątek zgłaszany w klauzuli wyjątek zapewnia korzyści wykonywanie kodu.

## <a name="related-rules"></a>Powiązane reguły
 [CA1065: Nie zgłaszaj wyjątków w nieoczekiwanych lokalizacjach](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)

## <a name="see-also"></a>Zobacz też
 [Ostrzeżenia dotyczące projektu](../code-quality/design-warnings.md)



