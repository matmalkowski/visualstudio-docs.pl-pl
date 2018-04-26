---
title: Zarządzane zalecane Reguły dla zarządzanego kodu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 1d1160f8-4e51-4e70-99cd-82ad10ee7b32
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 489d7fba60b3c7d72b7d0d5f1e94436ae5123c52
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="managed-recommended-rules-rule-set-for-managed-code"></a>Zarządzane zalecane Reguły dla zarządzanego kodu
Można użyć programu Microsoft zarządzane zalecane reguły skupić się na najpoważniejszych problemów w kodzie zarządzanym, w tym potencjalnych luk w zabezpieczeniach, awarii aplikacji i inne ważne błędy logiki i projektowania. Należy dołączyć ten zestaw reguł w każdego niestandardowego zestawu reguł tworzonego dla projektów.

|Reguła|Opis|
|----------|-----------------|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Typy, które posiadają pola usuwalne powinny być usuwalne|
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|Poprawnie Zadeklaruj procedury obsługi zdarzeń|
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|Oznacz zestawy atrybutem Assemblyversion|
|[CA1033](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|Metody interfejsu powinny móc zostać wywołane przez typy podrzędne|
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|Typy, które posiadają natywne zasoby powinny być usuwalne|
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|Przenieś P/Invokes do klasy NativeMethods|
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|Nie ukrywaj metod klasy podstawowej|
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|Prawidłowo zaimplementować interfejs IDisposable|
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|Nie zgłaszaj wyjątków w nieoczekiwanych lokalizacjach|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Należy unikać duplikowania akceleratorów|
|[CA1400](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|Punkty wejścia P/Invoke powinny istnieć|
|[CA1401](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|P/Invoke nie powinny być widoczne|
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Typy z automatycznym układem nie powinny być widoczne dla modelu COM|
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|Wywołać GetLastError natychmiast po P/Invoke|
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|Typy podstawowe typu widocznego modelu COM powinny być widoczne dla modelu COM|
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|Metody rejestracji modelu COM powinny być zgodne.|
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|Poprawnie zadeklarować P/Invoke|
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Usuń puste finalizatory|
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Pola typu wartości powinny być przenośne|
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Deklaracje P/Invoke powinny być przenośne|
|[CA2002](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Nie blokuj obiektów o słabej tożsamości|
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|Sprawdź zapytania SQL w poszukiwaniu luk w zabezpieczeniach|
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Określ kierowanie dla argumentów ciągu P/Invoke|
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Przejrzyj zabezpieczenia deklaratywne dla typów wartości|
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|Wskaźniki nie powinny być widoczne|
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Zabezpieczone typy nie powinny ujawniać pól|
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|Zabezpieczenie metody powinno być nadzbiorem typu|
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|Metody z atrybutem APTCA powinny wywoływać tylko metody APTCA|
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|Typy APTCA powinny rozszerzać tylko typy bazowe APTCA|
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|Nie ujawniaj pośrednio metod żądaniami linkdemand|
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Zastąpienie powinny być identyczne z bazowym|
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Opakuj podatne na koniec spróbuj klauzule zewnętrzne|
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Typ żądań konsolidacji wymaga żądań dziedziczenia|
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Typy krytyczne dla zabezpieczeń nie może uczestniczyć w równoważnikach typów|
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Konstruktory domyślne muszą być co najmniej tak ważne, jak podstawowe konstruktory domyślne|
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Delegatów należy powiązać z metodami ze spójną jawnością|
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Metody muszą przechowywać spójną jawność podczas nadpisywania metod bazowych|
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|Jawne metody muszą zawierać tylko weryfikowalne IL|
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Jawne metody nie mogą wywoływać metod z atrybutem suppressunmanagedcodesecurity|
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Kod o przezroczystym nie może odwoływać się elementów krytycznych dla zabezpieczeń|
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Jawne metody nie mogą spełniać LinkDemands|
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Typy muszą być co najmniej tak ważne, jak ich typy podstawowe i interfejsy|
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Jawne metody nie mogą używać zabezpieczeń potwierdzeń|
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Jawne metody nie mogą wywoływać kodu natywnego|
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|Ponownie, aby zachować szczegóły stosu|
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|Nie Likwiduj wielokrotnie obiektów|
|[CA2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|Inicjowanie pól statycznych typu wartościowego|
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|Nie należy oznaczać obsługiwanych składników znacznikiem WebMethod|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Pola usuwalne powinny zostać usunięte.|
|[CA2214](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|Nie należy wywoływać nadpisywalnych metod w konstruktorach|
|[CA2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|Typy usuwalne powinny deklarować finalizator|
|[CA2220](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|Finalizatory powinny wywoływać finalizator klasy podstawowej|
|[CA2229](../code-quality/ca2229-implement-serialization-constructors.md)|Zaimplementować konstruktory serializacji|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Przeciąż operator equals przy zastępowaniu ValueType.Equals|
|[CA2232](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|Punkty wejścia formularzy systemu Windows Oznacz za pomocą STAThread|
|[CA2235](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Oznaczyć wszystkie nieserializowane pola|
|[CA2236](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|Wywołanie metod klasy podstawowej typu ISerializable|
|[CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|Oznacz typy ISerializable atrybutem SerializableAttribute|
|[CA2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|Poprawnie Implementuj metody serializacji|
|[CA2240](../code-quality/ca2240-implement-iserializable-correctly.md)|Poprawnie zaimplementować ISerializable|
|[CA2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|Podaj poprawne argumenty metod formatowania|
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|Testowania poprawnie liczby (NaN)|