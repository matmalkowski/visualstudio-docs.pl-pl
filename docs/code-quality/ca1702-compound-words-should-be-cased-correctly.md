---
title: "CA1702: Wyrazy złożone powinien mieć prawidłową wielkość liter | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
helpviewer_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9c8606656b7ffe5f64c4c162b85d24bdbd9b1de0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702: Wyrazy złożone należy zapisywać z uwzględnieniem wielkości liter
|||  
|-|-|  
|TypeName|CompoundWordsShouldBeCasedCorrectly|  
|CheckId|CA1702|  
|Kategoria|Microsoft.Naming|  
|Zmiana kluczowa|Uruchamiany po wybraniu podziału zestawów.<br /><br /> Bez podziału — po dotyczące parametrów typu.|  
  
## <a name="cause"></a>Przyczyna  
 Nazwa identyfikatora zawiera wiele słów i co najmniej jedno ze słów wydaje się być wyraz złożony, który nie jest poprawnie liter.  
  
## <a name="rule-description"></a>Opis reguły  
 Nazwa identyfikatora jest podzielony na wyrazy, które są oparte na wielkość liter. Każda kombinacja ciągłe word dwie jest sprawdzana przez moduł sprawdzania pisowni biblioteki. Jeśli został on rozpoznany, identyfikator tworzy naruszenia reguły. Przykłady wyrazy złożone, które powodują naruszenie to "Kontrolną" i "MultiPart", które powinny być pisane w formie "Kontrolną" i "Multipart", odpowiednio. Ze względu na poprzednie użycie wspólnej, kilka wyjątków są wbudowane w zasady i oflagowane kilka pojedynczych słów, takich jak "Narzędzi" i "Filename", które powinny mieć prawidłową wielkość jako dwa różne wyrazy (w tym przypadku "Narzędzi" i "FileName").  
  
 Konwencje nazewnictwa Podaj wygląd wspólnej dla bibliotek przeznaczonych środowisko uruchomieniowe języka wspólnego. Zmniejsza to nauki jest wymagany dla nowej biblioteki oprogramowania, którą można tworzyć bardziej niezawodne klienta, czy biblioteka został opracowany przez osobę, która ma doświadczenia w rozwijającym się kodu zarządzanego.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Zmień nazwę, dzięki czemu jest prawidłową wielkość liter.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli obie części wyraz złożony są rozpoznawane przez słownik pisowni i celem jest użycie dwóch wyrazów.  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1701: Wyrazy złożone ciągu zasobu powinny mieć prawidłową wielkość liter](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
 [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Identyfikatory powinny różnić się tylko wielkością liter](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Zasady nazewnictwa](/dotnet/standard/design-guidelines/naming-guidelines)   
 [Konwencje wielkość liter](/dotnet/standard/design-guidelines/capitalization-conventions)