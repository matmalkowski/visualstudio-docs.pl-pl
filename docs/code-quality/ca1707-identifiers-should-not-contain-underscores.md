---
title: 'CA1707: Identyfikatory nie powinny zawierać podkreśleń'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotContainUnderscores
- CA1707
helpviewer_keywords:
- CA1707
- IdentifiersShouldNotContainUnderscores
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4eed69f8c08d6106bf30e9c1884512e384a7a269
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
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