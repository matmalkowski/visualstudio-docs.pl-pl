---
title: "CA1065: Nie zgłaszaj wyjątków w nieoczekiwanych lokalizacjach | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1065
- DoNotRaiseExceptionsInUnexpectedLocations
helpviewer_keywords:
- DoNotRaiseExceptionsInUnexpectedLocations
- CA1065
ms.assetid: 4e1bade4-4ca2-4219-abc3-c7b2d741e157
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3511778536bb9664726fc9a61b4773c209a0fd46
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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
  
-   Metody Get właściwości  
  
-   Metod dostępu zdarzeń  
  
-   Metody Equals  
  
-   Metody GetHashCode  
  
-   Metody ToString  
  
-   Konstruktory statyczne  
  
-   Finalizatory  
  
-   Metody Dispose  
  
-   Operatory równości  
  
-   Niejawne rzutowanie operatory  
  
 W poniższych sekcjach omówiono te typy metody.  
  
### <a name="property-get-methods"></a>Metody Get właściwości  
 Właściwości są zasadniczo inteligentne pól. W związku z tym powinien zachowują się podobnie jak możliwie pola. Pola nie zgłaszają wyjątki, a nie powinien właściwości. Jeśli właściwość, która zgłasza wyjątek, należy rozważyć zmianę jego metody.  
  
 Następujące wyjątki są może zostać wygenerowany przy użyciu metody get właściwości:  
  
-   <xref:System.InvalidOperationException?displayProperty=fullName>i wszystkich pochodnych (w tym <xref:System.ObjectDisposedException?displayProperty=fullName>)  
  
-   <xref:System.NotSupportedException?displayProperty=fullName>i wszystkich pochodnych  
  
-   <xref:System.ArgumentException?displayProperty=fullName>(tylko z indeksowana get)  
  
-   <xref:System.Collections.Generic.KeyNotFoundException>(tylko z indeksowana get)  
  
### <a name="event-accessor-methods"></a>Metod dostępu zdarzeń  
 Metod dostępu zdarzeń powinno być proste operacje, które nie zgłaszają wyjątki. Zdarzenie nie powinien zgłosić wyjątek podczas próby Dodaj lub usuń program obsługi zdarzeń.  
  
 Następujące wyjątki są może zostać zgłoszony w accesor zdarzeń:  
  
-   <xref:System.InvalidOperationException?displayProperty=fullName>i wszystkich pochodnych (w tym <xref:System.ObjectDisposedException?displayProperty=fullName>)  
  
-   <xref:System.NotSupportedException?displayProperty=fullName>i wszystkich pochodnych  
  
-   <xref:System.ArgumentException>i pochodne  
  
### <a name="equals-methods"></a>Metody Equals  
 Następujące **jest równe** metod nie powinny zgłaszają wyjątki:  
  
-   <xref:System.Object.Equals%2A?displayProperty=fullName>  
  
-   [M:IEquatable.Equals](http://go.microsoft.com/fwlink/?LinkId=113472)  
  
 **Jest równe** metoda powinna zwrócić `true` lub `false` zamiast generowania wyjątku. Na przykład, jeśli jest równe jest przekazywany dwa niezgodne typy powinien on tylko zwrócić `false` zamiast zgłaszanie <xref:System.ArgumentException>.  
  
### <a name="gethashcode-methods"></a>Metody GetHashCode  
 Następujące **GetHashCode** metody zazwyczaj powinno nie zgłaszają wyjątki:  
  
-   <xref:System.Object.GetHashCode%2A>  
  
-   [M:IEqualityComparer.GetHashCode(T)](http://go.microsoft.com/fwlink/?LinkId=113477)  
  
 **GetHashCode** powinien zawsze zwracać wartość. W przeciwnym razie zostaną utracone elementów w tablicy skrótów.  
  
 Wersje **GetHashCode** które trwają argument może zgłosić <xref:System.ArgumentException>. Jednak **Object.GetHashCode** nigdy nie powinien zgłosić wyjątek.  
  
### <a name="tostring-methods"></a>Metody ToString  
 Debuger używa <xref:System.Object.ToString%2A?displayProperty=fullName> Aby wyświetlić informacje o obiektach w formacie ciągu. W związku z tym **ToString** nie należy zmieniać stanu obiektu i nie powinien nie zgłaszają wyjątki.  
  
### <a name="static-constructors"></a>Konstruktory statyczne  
 Wyrzucanie wyjątków w konstruktorze statycznym powoduje, że typ stanie się bezużyteczne w bieżącej domenie aplikacji. Bardzo dobrze Przyczyna (na przykład problem zabezpieczeń) powinny mieć dla generowania wyjątku w konstruktorze statycznym.  
  
### <a name="finalizers"></a>Finalizatory  
 Zgłaszanie wyjątków z finalizator powoduje, że CLR niepowodzenie szybkie, który rys, dół procesu. W związku z tym zgłaszanie wyjątków w finalizator zawsze należy unikać.  
  
### <a name="dispose-methods"></a>Metody Dispose  
 A <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> — metoda nie powinien zgłosić wyjątek. Metoda Dispose jest często określane jako część logiki w oczyszczania `finally` klauzuli. W związku z tym jawne zgłaszanie wyjątków z Dispose wymusza użytkownikowi na dodawanie obsługi wewnątrz wyjątków `finally` klauzuli.  
  
 **Dispose(false)** ścieżka kodu powinien nigdy nie zgłaszają wyjątki, ponieważ to jest prawie zawsze wywoływana z finalizator.  
  
### <a name="equality-operators--"></a>Operatory równości (==,! =)  
 Podobnie jak metody Equals Operatory równości powinien zwrócić albo `true` lub `false` i nie powinny zgłaszać wyjątków.  
  
### <a name="implicit-cast-operators"></a>Niejawne rzutowanie operatory  
 Ponieważ użytkownik jest często bez "świadomości" operator niejawne rzutowanie została wywołana, wyjątek zgłoszony przez operator niejawne rzutowanie jest zupełnie nieoczekiwane. W związku z tym żadne wyjątki powinny zostać zgłoszony w operatory niejawnej rzutowania.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Dla metody pobierające właściwości albo zmień logikę, tak aby nie ma ono zgłosić wyjątek, lub zmień właściwość w metodę.  
  
 Dla wszystkich innych metody typów wymienionymi wcześniej Zmień logikę tak, aby go już musi zgłosić wyjątek.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli naruszenie spowodowane przez deklaracji wyjątku zamiast zwrócony wyjątek.  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA2219: Nie zgłaszaj wyjątków w klauzulach wyjątków](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Ostrzeżenia projektu](../code-quality/design-warnings.md)