---
title: Zestaw reguł zabezpieczeń dla zarządzanego kodu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 564aeac6-03fa-41b0-b655-88179f0ab01b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 6712454fad2acaf57b3cb4d8f1740366a396ec6e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31925045"
---
# <a name="security-rules-rule-set-for-managed-code"></a>Zestaw reguł zabezpieczeń dla zarządzanego kodu
Należy uwzględnić reguły reguły zabezpieczeń firmy Microsoft, aby zmaksymalizować liczbę zgłaszanych potencjalnych problemów zabezpieczeń.

|Reguła|Opis|
|----------|-----------------|
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|Sprawdź zapytania SQL w poszukiwaniu luk w zabezpieczeniach|
|[CA2102](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)|Przechwytuj wyjątki bez atrybutu CLSCompliant w ogólnych procedurach obsługi|
|[CA2103](../code-quality/ca2103-review-imperative-security.md)|Przejrzyj zabezpieczenia imperatywne|
|[CA2104](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)|Nie deklaruj typów referencyjnych tylko do odczytu|
|[CA2105](../code-quality/ca2105-array-fields-should-not-be-read-only.md)|W przypadku pól tablicy nie można odczytać tylko|
|[CA2106](../code-quality/ca2106-secure-asserts.md)|Bezpieczne potwierdzeń|
|[CA2107](../code-quality/ca2107-review-deny-and-permit-only-usage.md)|Przejrzyj Odmów i permit only|
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Przejrzyj zabezpieczenia deklaratywne dla typów wartości|
|[CA2109](../code-quality/ca2109-review-visible-event-handlers.md)|Przejrzyj widoczne programy obsługi zdarzeń|
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|Wskaźniki nie powinny być widoczne|
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Zabezpieczone typy nie powinny ujawniać pól|
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|Zabezpieczenie metody powinno być nadzbiorem typu|
|[CA2115](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)|Wywołanie GC. KeepAlive, gdy używasz zasobów natywnych|
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|Metody z atrybutem APTCA powinny wywoływać tylko metody APTCA|
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|Typy APTCA powinny rozszerzać tylko typy bazowe APTCA|
|[CA2118](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md)|Przegląd wykorzystania SuppressUnmanagedCodeSecurityAttribute|
|[CA2119](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|Pieczętuj metody, które spełniają wymagania interfejsów prywatnych|
|[CA2120](../code-quality/ca2120-secure-serialization-constructors.md)|Zabezpieczaj konstruktory serializacji|
|[CA2121](../code-quality/ca2121-static-constructors-should-be-private.md)|Konstruktory statyczne powinny być prywatne|
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|Nie ujawniaj pośrednio metod żądaniami linkdemand|
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Zastąpienie powinny być identyczne z bazowym|
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Opakuj podatne na koniec spróbuj klauzule zewnętrzne|
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Typ żądań konsolidacji wymaga żądań dziedziczenia|
|[CA2130](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|Krytyczne stałe zabezpieczeń powinny być przezroczyste|
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Typy krytyczne dla zabezpieczeń nie może uczestniczyć w równoważnikach typów|
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Konstruktory domyślne muszą być co najmniej tak ważne, jak podstawowe konstruktory domyślne|
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Delegatów należy powiązać z metodami ze spójną jawnością|
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Metody muszą przechowywać spójną jawność podczas nadpisywania metod bazowych|
|[CA2135](../code-quality/ca2135-level-2-assemblies-should-not-contain-linkdemands.md)|Zestawy poziomu 2 nie powinny zawierać LinkDemands|
|[CA2136](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md)|Elementy członkowskie nie powinny mieć skonfliktowanych adnotacji przezroczystości|
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|Jawne metody muszą zawierać tylko weryfikowalne IL|
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Jawne metody nie mogą wywoływać metod z atrybutem suppressunmanagedcodesecurity|
|[CA2139](../code-quality/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md)|Jawne metody nie mogą używać atrybutu HandleProcessCorruptingExceptions|
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Kod o przezroczystym nie może odwoływać się elementów krytycznych dla zabezpieczeń|
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Jawne metody nie mogą spełniać LinkDemands|
|[CA2142](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)|Kod o przezroczystym nie powinien być chroniony za pomocą LinkDemands|
|[CA2143](../code-quality/ca2143-transparent-methods-should-not-use-security-demands.md)|Jawne metody nie powinny używać żądania kontroli zabezpieczeń|
|[CA2144](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)|Kod o przezroczystym nie powinien ładować zestawów z tablic bajtowych|
|[CA2145](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)|Jawne metody nie powinny być dekorowane za pomocą SuppressUnmanagedCodeSecurityAttribute|
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Typy muszą być co najmniej tak ważne, jak ich typy podstawowe i interfejsy|
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Jawne metody nie mogą używać zabezpieczeń potwierdzeń|
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Jawne metody nie mogą wywoływać kodu natywnego|
|[CA2210](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md)|Zestawy powinny mieć prawidłowe silne nazwy|