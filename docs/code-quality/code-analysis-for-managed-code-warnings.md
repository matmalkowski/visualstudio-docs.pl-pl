---
title: "Analiza kodu dla zarządzanego kodu — ostrzeżenia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.project.vcfxcoptool.enablefxcop
helpviewer_keywords:
- managed code analyis, warnings
- warnings, managed code analysis
- managed code analysis warnings
- code analysis,managed code
ms.assetid: 3c2741ff-0d3a-42e6-acd5-d42310bd03c4
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 689fe39cfb8a7719efbba15b412800d9dfa78361
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="code-analysis-for-managed-code-warnings"></a>Analiza kodu dla zarządzanego kodu — Ostrzeżenia
Narzędzie do analizy kodu zarządzanego zawiera ostrzeżenia, które wskazują naruszeń zasady w bibliotekach kodu zarządzanego. Ostrzeżenia są podzielone na reguły obszarów, takich jak projekt, lokalizacji, wydajności i zabezpieczeń. Każde ostrzeżenie oznacza naruszenia reguły analizy kodu zarządzanego. Ta sekcja zawiera szczegółowe omówienie i przykłady dotyczące każdego ostrzeżenia analizy kodu zarządzanego.  
  
 W poniższej tabeli przedstawiono typ informacji dostępnych dla każdego ostrzeżenia.  
  
|Element|Opis|  
|----------|-----------------|  
|Typ|Właściwość TypeName reguły.|  
|CheckId|Unikatowy identyfikator reguły. Pomijanie ostrzeżenie-source używane CheckId i kategorii.|  
|Kategoria|Kategoria ostrzeżenia.|  
|Zmiana kluczowa|Określa, czy poprawka dla naruszenia reguły jest istotne zmiany. Fundamentalne zmiany oznacza, że zestaw, który ma zależności w elemencie docelowym, który spowodował naruszenie nie zostanie ponownie skompilowana z nowym stałej wersji i może się nie powieść w czasie wykonywania z powodu zmiany. Gdy dostępnych jest wiele poprawek i co najmniej jedną poprawkę są istotne zmiany jednego nie będzie, została określona zarówno "Krytyczne" i "Krytyczne z systemem innym niż".|  
|Przyczyna|Określonego kodu zarządzanego, która powoduje wygenerowanie ostrzeżenia reguły.|  
|Opis|W tym artykule omówiono problemy, które znajdują się za ostrzeżenia.|  
|Jak naprawić naruszenia|Wyjaśniono, jak zmienić kod źródłowy, które spełniają reguły i uniemożliwić zostanie wygenerowane ostrzeżenie.|  
|Kiedy pominąć ostrzeżenia|Opisuje, gdy jest bezpiecznie pominąć ostrzeżenie z reguły.|  
|Przykładowy kod|Przykłady, które naruszają zasady i poprawić przykłady, które spełniają reguły.|  
|Ostrzeżenia pokrewne|Powiązane ostrzeżenia.|  
  
## <a name="in-this-section"></a>W tej sekcji  
  
|||  
|-|-|  
|[Ostrzeżenia dzięki CheckId](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)|Wyświetla wszystkie ostrzeżenia dzięki CheckId|  
|[Ostrzeżenia dotyczące kryptografii](../code-quality/cryptography-warnings.md)|Ostrzeżenia, które obsługują bezpieczniejszy bibliotek i aplikacji za pośrednictwem prawidłowe użycie kryptograficzne.|  
|[Ostrzeżenia dotyczące projektu](../code-quality/design-warnings.md)|Ostrzeżenia, które obsługują odpowiedniej biblioteki projektu określony przez [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] zaleceń dotyczących projektowania.|  
|[Ostrzeżenia dotyczące globalizacji](../code-quality/globalization-warnings.md)|Ostrzeżenia, które obsługują bibliotek gotowe i aplikacji.|  
|[Ostrzeżenia dotyczące współdziałania](../code-quality/interoperability-warnings.md)|Ostrzeżenia, które obsługują funkcję interakcji z klientami COM.|  
|[Ostrzeżenia dotyczące konserwacji](../code-quality/maintainability-warnings.md)|Ostrzeżenia, które obsługują konserwacji biblioteki i aplikacji.|  
|[Ostrzeżenia dotyczące mobilności](../code-quality/mobility-warnings.md)|Ostrzeżenia, które obsługują efektywne zużycie energii.|  
|[Ostrzeżenia dotyczące nazewnictwa](../code-quality/naming-warnings.md)|Ostrzeżenia, które obsługują przestrzeganie konwencje nazewnictwa [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] zaleceń dotyczących projektowania.|  
|[Ostrzeżenia dotyczące wydajności](../code-quality/performance-warnings.md)|Ostrzeżenia, które obsługują bibliotek wysokiej wydajności i aplikacji.|  
|[Ostrzeżenia dotyczące przenośności](../code-quality/portability-warnings.md)|Ostrzeżenia, które obsługują przenośność na różnych platformach.|  
|[Ostrzeżenia dotyczące niezawodności](../code-quality/reliability-warnings.md)|Ostrzeżenia, które obsługują niezawodności biblioteki i aplikacji, takich jak odpowiednie użycie pamięci i wątku.|  
|[Ostrzeżenia dotyczące zabezpieczeń](../code-quality/security-warnings.md)|Ostrzeżenia, które obsługują bezpieczniejszy bibliotek i aplikacji.|  
|[Ostrzeżenia dotyczące użycia](../code-quality/usage-warnings.md)|Ostrzeżenia, które obsługują odpowiednie użycie [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].|  
|[Błędy zasad analizy kodu](../code-quality/code-analysis-policy-errors.md)|Błędy, które wystąpić, jeśli zasad analizy kodu nie jest spełniony na zaewidencjonowania.|