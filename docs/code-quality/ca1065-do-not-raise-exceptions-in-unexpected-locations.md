---
title: 'CA1065: Nie należy wyrzucać wyjątków w nieoczekiwanych lokalizacjach'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1065
- DoNotRaiseExceptionsInUnexpectedLocations
helpviewer_keywords:
- DoNotRaiseExceptionsInUnexpectedLocations
- CA1065
ms.assetid: 4e1bade4-4ca2-4219-abc3-c7b2d741e157
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 477286e437a901d15dd7a13a6bc1d9f7634b3b73
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca1065-do-not-raise-exceptions-in-unexpected-locations"></a>CA1065: Nie należy wyrzucać wyjątków w nieoczekiwanych lokalizacjach

|||
|-|-|
|TypeName|DoNotRaiseExceptionsInUnexpectedLocations|
|CheckId|CA1065|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Metoda, od której nie oczekiwano zgłaszania wyjątków, zgłasza wyjątek.

## <a name="rule-description"></a>Opis reguły

Metody, które nie powinny zgłaszać wyjątków można podzielić w następujący sposób:

- Metody Get właściwości

- Metod dostępu zdarzeń

- Metody Equals

- Metody GetHashCode

- Metody ToString

- Konstruktory statyczne

- Finalizatory

- Metody Dispose

- Operatory równości

- Niejawne rzutowanie operatory

W poniższych sekcjach omówiono te typy metody.

### <a name="property-get-methods"></a>Metody Get właściwości

Właściwości są zasadniczo inteligentne pól. W związku z tym powinien zachowują się podobnie jak możliwie pola. Pola nie zgłaszają wyjątki, a nie powinien właściwości. Jeśli właściwość, która zgłasza wyjątek, należy rozważyć zmianę jego metody.

Następujące wyjątki może zostać wygenerowany przy użyciu metody get właściwości:

- <xref:System.InvalidOperationException?displayProperty=fullName> i wszystkich pochodnych (w tym <xref:System.ObjectDisposedException?displayProperty=fullName>)

- <xref:System.NotSupportedException?displayProperty=fullName> i wszystkich pochodnych

- <xref:System.ArgumentException?displayProperty=fullName> (tylko z indeksowana get)

- <xref:System.Collections.Generic.KeyNotFoundException> (tylko z indeksowana get)

### <a name="event-accessor-methods"></a>Metod dostępu zdarzeń

Metod dostępu zdarzeń powinno być proste operacje, które nie zgłaszają wyjątki. Zdarzenie nie powinien zgłosić wyjątek podczas próby Dodaj lub usuń program obsługi zdarzeń.

Z metody dostępu zdarzeń może zostać wygenerowany następujące wyjątki:

- <xref:System.InvalidOperationException?displayProperty=fullName> i wszystkich pochodnych (w tym <xref:System.ObjectDisposedException?displayProperty=fullName>)

- <xref:System.NotSupportedException?displayProperty=fullName> i wszystkich pochodnych

- <xref:System.ArgumentException> i pochodne

### <a name="equals-methods"></a>Metody Equals

Następujące **jest równe** metod nie powinny zgłaszają wyjątki:

- <xref:System.Object.Equals%2A?displayProperty=fullName>

- <xref:System.IEquatable%601.Equals%2A>

**Jest równe** metoda powinna zwrócić `true` lub `false` zamiast generowania wyjątku. Na przykład, jeśli jest równe jest przekazywany dwa niezgodne typy powinien on tylko zwrócić `false` zamiast zgłaszanie <xref:System.ArgumentException>.

### <a name="gethashcode-methods"></a>Metody GetHashCode

Następujące **GetHashCode** metody zazwyczaj powinno nie zgłaszają wyjątki:

- <xref:System.Object.GetHashCode%2A>

- <xref:System.Collections.IEqualityComparer.GetHashCode%2A>

**GetHashCode** powinien zawsze zwracać wartość. W przeciwnym razie zostaną utracone elementów w tablicy skrótów.

Wersje **GetHashCode** które trwają argument może zgłosić <xref:System.ArgumentException>. Jednak **Object.GetHashCode** nigdy nie powinien zgłosić wyjątek.

### <a name="tostring-methods"></a>Metody ToString

Debuger używa <xref:System.Object.ToString%2A?displayProperty=fullName> Aby wyświetlić informacje o obiektach w formacie ciągu. W związku z tym **ToString** nie należy zmieniać stan obiektu, a nie powinny zgłaszać wyjątków.

### <a name="static-constructors"></a>Konstruktory statyczne

Wyrzucanie wyjątków w konstruktorze statycznym powoduje, że typ stanie się bezużyteczne w bieżącej domenie aplikacji. Powód (na przykład problem zabezpieczeń) powinny mieć dla generowania wyjątku w konstruktorze statycznym.

### <a name="finalizers"></a>Finalizatory

Zgłaszanie wyjątków z finalizator powoduje, że CLR niepowodzenie szybkie, który rys, dół procesu. W związku z tym zgłaszanie wyjątków w finalizator zawsze należy unikać.

### <a name="dispose-methods"></a>Metody Dispose

A <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> — metoda nie powinien zgłosić wyjątek. Metoda Dispose jest często określane jako część logiki oczyszczania w `finally` klauzuli. W związku z tym jawne zgłaszanie wyjątków z Dispose wymusza użytkownikowi na dodawanie obsługi wewnątrz wyjątków `finally` klauzuli.

**Dispose(false)** ścieżka kodu powinien nigdy nie zgłaszają wyjątki, ponieważ metoda Dispose prawie zawsze jest wywoływana z finalizator.

### <a name="equality-operators--"></a>Operatory równości (==,! =)

Podobnie jak metody Equals Operatory równości powinien zwrócić albo `true` lub `false`i nie powinny zgłaszać wyjątków.

### <a name="implicit-cast-operators"></a>Niejawne rzutowanie operatory

Ponieważ użytkownik jest często bez "świadomości" operator niejawne rzutowanie została wywołana, wyjątek zgłoszony przez operator niejawne rzutowanie jest nieoczekiwany. W związku z tym żadne wyjątki powinny zostać zgłoszony w operatory niejawnej rzutowania.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Dla metody pobierające właściwości albo zmień logikę, tak aby nie ma ono zgłosić wyjątek, lub zmień właściwość w metodę.

Dla wszystkich innych metody typów wymienionymi wcześniej Zmień logikę tak, aby go już musi zgłosić wyjątek.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jeśli naruszenie spowodowane przez deklaracji wyjątku zamiast zwrócony wyjątek, jest bezpiecznie pominąć ostrzeżenie od tej reguły.

## <a name="related-rules"></a>Powiązanych reguł

- [CA2219: Nie zgłaszaj wyjątków w klauzulach wyjątku](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)

## <a name="see-also"></a>Zobacz także

- [Ostrzeżenia dotyczące projektu](../code-quality/design-warnings.md)