---
title: 'CA2219: Nie zgłaszaj wyjątków w klauzulach wyjątków | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
helpviewer_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
ms.assetid: 7b9b0bee-4e8e-49a4-8c40-52142b49061f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: abe5fe25297c61e84e19857747c19b3602f78e0b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ca2219-do-not-raise-exceptions-in-exception-clauses"></a>CA2219: Nie zgłaszaj wyjątków w klauzulach wyjątków
|||  
|-|-|  
|TypeName|DoNotRaiseExceptionsInExceptionClauses|  
|CheckId|CA2219|  
|Kategoria|Microsoft.Usage|  
|Zmiana kluczowa|Bez podziału, krytyczne|  
  
## <a name="cause"></a>Przyczyna  
 Wyjątek `finally`, filtr lub klauzulę błędów.  
  
## <a name="rule-description"></a>Opis reguły  
 W klauzuli wyjątek zgłoszony wyjątek, znacznie zwiększa trudności debugowania.  
  
 Jeśli wyjątek jest zgłaszany w `finally` lub klauzuli błędów ukrywa aktywny wyjątek, jeśli istnieje. Dzięki temu można twardych wykrycie i zdebugowanie pierwotnego błędu.  
  
 Jeśli wyjątek jest zgłaszany w klauzuli filtru, środowiska uruchomieniowego dyskretnie przechwytuje wyjątek i powoduje, że dla filtru wartości FALSE. Nie istnieje sposób, aby odróżnić oceny filtr na wartość FAŁSZ i Trwa throw z filtrem wyjątku. Utrudnia wykrywanie i debugowanie błędów w logice filtru.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby rozwiązać to naruszenie tej reguły, nie jawnie wywołuj wyjątku z `finally`, filtr lub klauzulę błędów.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżenia dla tej reguły. Nie istnieją żadne scenariusze, w których wystąpił wyjątek w klauzuli wyjątek zapewnia korzyści wykonywanie kodu.  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1065: Nie zgłaszaj wyjątków w nieoczekiwanych lokalizacjach](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Ostrzeżenia dotyczące projektu](../code-quality/design-warnings.md)