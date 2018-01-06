---
title: "CA1701: Wyrazy złożone ciągu zasobu powinny mieć prawidłową wielkość liter | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ResourceStringCompoundWordsShouldBeCasedCorrectly
- CA1701
helpviewer_keywords:
- CA1701
- ResourceStringCompoundWordsShouldBeCasedCorrectly
ms.assetid: 4ddbe09f-24b8-4c47-9373-a06f4487ca0d
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0b4b154d6e959e636ee75481816a2424d5ea2e18
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701: Wyrazy złożone ciągu zasobu należy zapisywać z uwzględnieniem wielkości liter
|||  
|-|-|  
|TypeName|ResourceStringCompoundWordsShouldBeCasedCorrectly|  
|CheckId|CA1701|  
|Kategoria|Microsoft.Naming|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Ciąg zasobu zawiera wyraz złożony, który nie ma mieć prawidłową wielkość liter.  
  
## <a name="rule-description"></a>Opis reguły  
 Każdego wyrazu w ciągu zasobu jest podzielony na tokeny, które są oparte na wielkość liter. Każda ciągła kombinacja dwóch tokenów jest sprawdzana przez bibliotekę sprawdzania pisowni firmy Microsoft. Jeżeli zostanie rozpoznana, dane słowo powoduje naruszenie reguły. Przykłady wyrazy złożone, które powodują naruszenie to "Kontrolną" i "MultiPart", które powinny być pisane w formie "Kontrolną" i "Multipart", odpowiednio. Ze względu na poprzednie użycie wspólnej kilka wyjątków są wbudowane w zasady, a oflagowane kilka pojedynczych słów, takich jak "Narzędzi" i "Filename", które powinny być pisane w formie dwóch unikatowych słów. W tym przykładzie zostanie oznaczony "Narzędzi" i "Nazwa_pliku".  
  
 Konwencje nazewnictwa Podaj wygląd wspólnej dla bibliotek przeznaczonych środowisko uruchomieniowe języka wspólnego. Zmniejsza to nauki jest wymagany dla nowej biblioteki oprogramowania, którą można tworzyć bardziej niezawodne klienta, czy biblioteka został opracowany przez osobę, która ma doświadczenia w rozwijającym się kodu zarządzanego.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Zmień litery słowa, dzięki czemu jest prawidłową wielkość liter.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli obie części wyraz złożony są rozpoznawane przez słownik pisowni i celem jest użycie dwóch wyrazów.  
  
 Można również dodać wyrazy złożone do słownika niestandardowego sprawdzania pisowni. Wyrazy do słownika nie powodują naruszeń. Aby uzyskać więcej informacji, zobacz [porady: dostosowywanie słownika analizy kodu](../code-quality/how-to-customize-the-code-analysis-dictionary.md).  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1702: W wyrazach złożonych należy poprawnie używać wielkości liter](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
 [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Identyfikatory powinny różnić się nie tylko wielkością liter](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Konwencje wielkość liter](/dotnet/standard/design-guidelines/capitalization-conventions)   
 [Wskazówki dotyczące nazewnictwa](/dotnet/standard/design-guidelines/naming-guidelines)