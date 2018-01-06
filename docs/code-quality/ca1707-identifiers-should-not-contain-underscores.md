---
title: "CA1707: Identyfikatory nie powinny zawierać podkreśleń | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IdentifiersShouldNotContainUnderscores
- CA1707
helpviewer_keywords:
- CA1707
- IdentifiersShouldNotContainUnderscores
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 582b7c95663633a4aada6a479a17306354c16b7f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707: Identyfikatory nie powinny zawierać podkreśleń
|||  
|-|-|  
|TypeName|IdentifiersShouldNotContainUnderscores|  
|CheckId|CA1707|  
|Kategoria|Microsoft.Naming|  
|Zmiana kluczowa|Dzielenie — gdy zestawów<br /><br /> Dzielenie non - zgłoszony w parametrach typu|  
  
## <a name="cause"></a>Przyczyna  
 Nazwa identyfikatora zawiera znak podkreślenia (_).  
  
## <a name="rule-description"></a>Opis reguły  
 Przez konwencję identyfikatory nazw nie zawierają znaku podkreślenia (_). Reguła sprawdza przestrzeni nazw, typy elementów członkowskich i parametry.  
  
 Konwencje nazewnictwa Podaj wygląd wspólnej dla bibliotek przeznaczonych środowisko uruchomieniowe języka wspólnego. Zmniejsza to nauki jest wymagany dla nowej biblioteki oprogramowania, którą można tworzyć bardziej niezawodne klienta, czy biblioteka został opracowany przez osobę, która ma doświadczenia w rozwijającym się kodu zarządzanego.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Usuń wszystkie znaki podkreślenia z nazwy.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Identyfikatory powinny różnić się nie tylko wielkością liter](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)