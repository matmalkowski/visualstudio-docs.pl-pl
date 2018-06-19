---
title: 'CA1702: Wyrazy złożone należy zapisywać z uwzględnieniem wielkości liter'
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
helpviewer_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4703c43c81df13432f45fb4ba519a02b39a839e0
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31917846"
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702: Wyrazy złożone należy zapisywać z uwzględnieniem wielkości liter

|||
|-|-|
|TypeName|CompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1702|
|Kategoria|Microsoft.Naming|
|Zmiana kluczowa|Uruchamiany po wybraniu podziału zestawów.<br /><br /> Bez podziału — po dotyczące parametrów typu.|

## <a name="cause"></a>Przyczyna

Nazwa identyfikatora zawiera wiele wyrazów i co najmniej jeden z nich wydaje się wyrazem złożonym, w którym wielkość liter nie jest poprawna.

## <a name="rule-description"></a>Opis reguły

Nazwa identyfikatora jest podzielony na wyrazy, które są oparte na wielkość liter. Każda kombinacja ciągłe word dwie jest sprawdzana przez moduł sprawdzania pisowni biblioteki. Jeśli został on rozpoznany, identyfikator tworzy naruszenia reguły. Przykłady wyrazy złożone, które powodują naruszenie to "Kontrolną" i "MultiPart", które powinny być pisane w formie "Kontrolną" i "Multipart", odpowiednio. Ze względu na poprzednie użycie wspólnej, kilka wyjątków są wbudowane w zasady i oflagowane kilka pojedynczych słów, takich jak "Narzędzi" i "Filename", które powinny mieć prawidłową wielkość jako dwa różne wyrazy (w tym przypadku "Narzędzi" i "FileName").

Konwencje nazewnictwa Podaj wygląd wspólnej dla bibliotek przeznaczonych środowisko uruchomieniowe języka wspólnego. Zmniejsza to nauki jest wymagany dla nowej biblioteki oprogramowania, którą można tworzyć bardziej niezawodne klienta, czy biblioteka został opracowany przez osobę, która ma doświadczenia w rozwijającym się kodu zarządzanego.

## <a name="how-to-fix-violations"></a>Jak rozwiązać naruszeń

Zmień nazwę, dzięki czemu jest prawidłową wielkość liter.

## <a name="language"></a>Język

Moduł sprawdzania pisowni obecnie sprawdza tylko względem słowniki kulturę opartą na języku angielskim. Kultura projektu w pliku projektu można zmienić, dodając **CodeAnalysisCulture** elementu.

Na przykład:

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> Jeśli ustawisz kultury na inny niż kulturę opartą na język angielski, to reguł analizy kodu dyskretnie jest wyłączona.

## <a name="when-to-suppress-warnings"></a>Kiedy pomijanie ostrzeżeń

Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli obie części wyraz złożony są rozpoznawane przez słownik pisowni i celem jest użycie dwóch wyrazów.

## <a name="related-rules"></a>Powiązanych reguł

- [CA1701: Wyrazy złożone ciągu zasobu powinny mieć prawidłową wielkość liter](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Identyfikatory powinny różnić się nie tylko wielkością liter](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Zobacz także

- [Wskazówki dotyczące nazewnictwa](/dotnet/standard/design-guidelines/naming-guidelines)
- [Konwencje dotyczące wielkości liter](/dotnet/standard/design-guidelines/capitalization-conventions)