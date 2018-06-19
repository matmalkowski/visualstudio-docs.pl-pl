---
title: Rozszerzony zestaw reguł poprawności dla zarządzanego kodu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 5b181f5b-6c7a-4e46-a783-360e1da427a0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 5bb373879bf4dd9c31ed7d8a7d832a270a158279
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31926559"
---
# <a name="extended-correctness-rules-rule-set-for-managed-code"></a>Rozszerzony zestaw reguł poprawności dla zarządzanego kodu
Zestaw reguł firmy Microsoft rozszerzone reguły poprawności maksymalizuje błędów użycia logiki i framework, które są zgłaszane przez analizę kodu. Dodatkowy nacisk jest kładziony na określone scenariusze, takie jak współdziałanie COM i aplikacji dla urządzeń przenośnych. Należy rozważyć dołączenie tego zestawu, jeśli jeden z tych scenariuszy dotyczy projektu lub w celu znalezienia dodatkowych problemów w projekcie reguł.

 Reguły poprawności firmy Microsoft z rozszerzony zestaw reguł zawiera reguły, ustawionych w regule podstawowe reguły poprawności firmy Microsoft. Podstawowe reguły poprawności obejmują reguły ustawionych w regule reguł zalecanych Minimum firmy Microsoft. Aby uzyskać więcej informacji, zobacz [zestaw reguł podstawowe reguły poprawności dla zarządzanego kodu](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md) i [ustawić zarządzane zalecane reguły dla zarządzanego kodu](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)

 W poniższej tabeli opisano wszystkie reguły w zestawie reguł Microsoft rozszerzone reguły poprawności.

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
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|Typy wyliczeniowe powinny mieć wartość zero|
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|Dokonaj przeciążenia operatora równości przy przeciążaniu operatorów dodawania i odejmowania|
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Nie należy przekazywać literałów jako zlokalizowanych parametrów|
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Normalizuj ciągi na wielkie litery|
|[CA1806](../code-quality/ca1806-do-not-ignore-method-results.md)|Nie Ignoruj wyników metod|
|[CA1816](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)|Wywołanie GC. Metodę SuppressFinalize poprawnie|
|[CA1819](../code-quality/ca1819-properties-should-not-return-arrays.md)|Właściwości nie powinny zwracać tablic|
|[CA1820](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|Testuj obecność pustych ciągów przy użyciu długości ciągu|
|[CA1903](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|Używaj tylko API z frameworku docelowego|
|[CA2004](../code-quality/ca2004-remove-calls-to-gc-keepalive.md)|Usuń wywołania do wykazu Globalnego. Utrzymywania aktywności|
|[CA2006](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|Używaj klasy SafeHandle w celu hermetyzacji zasobów natywnych|
|[CA2102](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)|Przechwytuj wyjątki bez atrybutu CLSCompliant w ogólnych procedurach obsługi|
|[CA2104](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)|Nie deklaruj typów referencyjnych tylko do odczytu|
|[CA2105](../code-quality/ca2105-array-fields-should-not-be-read-only.md)|W przypadku pól tablicy nie można odczytać tylko|
|[CA2106](../code-quality/ca2106-secure-asserts.md)|Bezpieczne potwierdzeń|
|[CA2115](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)|Wywołanie GC. KeepAlive, gdy używasz zasobów natywnych|
|[CA2119](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|Pieczętuj metody, które spełniają wymagania interfejsów prywatnych|
|[CA2120](../code-quality/ca2120-secure-serialization-constructors.md)|Zabezpieczaj konstruktory serializacji|
|[CA2121](../code-quality/ca2121-static-constructors-should-be-private.md)|Konstruktory statyczne powinny być prywatne|
|[CA2130](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|Krytyczne stałe zabezpieczeń powinny być przezroczyste|
|[CA2205](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Użyj zarządzanych odpowiedników funkcji Win32 API|
|[CA2215](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)|Metody Dispose powinny wywoływać metodę dispose klasy podstawowej|
|[CA2221](../code-quality/ca2221-finalizers-should-be-protected.md)|Finalizatory powinny być chronione|
|[CA2222](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|Nie obniżaj dziedziczonej widoczności elementów członkowskich|
|[CA2223](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md)|Elementy Członkowskie powinny różnić się bardziej, niż typem zwracanym|
|[CA2224](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|Zastąp metodę equals przeciążając operator equals|
|[CA2226](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|Operatory powinny mieć symetryczne przeciążenia|
|[CA2227](../code-quality/ca2227-collection-properties-should-be-read-only.md)|Właściwości kolekcji powinny być tylko do odczytu|
|[CA2239](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|Udostępnij metody deserializacji pól opcjonalnych|
|[CA1032](../code-quality/ca1032-implement-standard-exception-constructors.md)|Zaimplementuj standardowe konstruktory wyjątków|
|[CA1054](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|Parametry identyfikatora URI nie powinny być ciągami|
|[CA1055](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|Identyfikator URI zwracać wartości nie powinny być ciągami|
|[CA1056](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|Właściwości identyfikatora URI nie powinny być ciągami|
|[CA1057](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|Ciąg identyfikatora URI wywołują przeciążenia System.Uri|
|[CA1402](../code-quality/ca1402-avoid-overloads-in-com-visible-interfaces.md)|Unikaj przeciążeń w interfejsach widocznych dla modelu COM|
|[CA1406](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)|Unikaj argumentów Int64 dla klientów w języku Visual Basic 6|
|[CA1407](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)|Unikaj statycznych elementów członkowskich w typach widocznych dla modelu COM|
|[CA1408](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)|Nie używaj wartości AutoDual elementu ClassInterfaceType|
|[CA1409](../code-quality/ca1409-com-visible-types-should-be-creatable.md)|Typy widoczne dla modelu COM powinny mieć możliwość utworzenia|
|[CA1411](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)|Metody rejestracji modelu COM nie powinny być widoczne|
|[CA1412](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)|Oznacz interfejsy ComSource jako IDispatch|
|[CA1413](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)|Unikaj pól niepublicznych w typach wartości widocznych dla modelu COM|
|[CA1414](../code-quality/ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md)|Oznacz logiczne argumenty P/Invoke za pomocą MarshalAs|
|[CA1600](../code-quality/ca1600-do-not-use-idle-process-priority.md)|Nie używaj priorytetu procesu bezczynności|
|[CA1601](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|Nie używaj czasomierzy, które uniemożliwiają zmianę stanu zasilania|
|[CA1824](../code-quality/ca1824-mark-assemblies-with-neutralresourceslanguageattribute.md)|Oznacz zestawy za pomocą atrybutu NeutralResourcesLanguageAttribute|
|[CA2001](../code-quality/ca2001-avoid-calling-problematic-methods.md)|Unikaj wywoływania problematycznych metod|
|[CA2003](../code-quality/ca2003-do-not-treat-fibers-as-threads.md)|Nie Traktuj włókien jako wątków|
|[CA2135](../code-quality/ca2135-level-2-assemblies-should-not-contain-linkdemands.md)|Zestawy poziomu 2 nie powinny zawierać LinkDemands|
|[CA2136](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md)|Elementy członkowskie nie powinny mieć skonfliktowanych adnotacji przezroczystości|
|[CA2139](../code-quality/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md)|Jawne metody nie mogą używać atrybutu HandleProcessCorruptingExceptions|
|[CA2142](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)|Kod o przezroczystym nie powinien być chroniony za pomocą LinkDemands|
|[CA2143](../code-quality/ca2143-transparent-methods-should-not-use-security-demands.md)|Jawne metody nie powinny używać żądania kontroli zabezpieczeń|
|[CA2144](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)|Kod o przezroczystym nie powinien ładować zestawów z tablic bajtowych|
|[CA2145](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)|Jawne metody nie powinny być dekorowane za pomocą SuppressUnmanagedCodeSecurityAttribute|
|[CA2204](../code-quality/ca2204-literals-should-be-spelled-correctly.md)|Literały powinny być napisane poprawnie|
|[CA2211](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|Pola niebędące stałymi nie powinny być widoczne|
|[CA2217](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|Nie oznaczaj typów wyliczeniowych atrybutem FlagsAttribute|
|[CA2218](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)|Zastąp GetHashCode przy zastępowaniu Equals|
|[CA2219](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)|Nie wywołuj wyjątków w klauzulach wyjątków|
|[CA2225](../code-quality/ca2225-operator-overloads-have-named-alternates.md)|Operator overloads ma nazwanych zastępców|
|[CA2228](../code-quality/ca2228-do-not-ship-unreleased-resource-formats.md)|Nie dostarczaj niepublikowanych formatów zasobów|
|[CA2230](../code-quality/ca2230-use-params-for-variable-arguments.md)|Użyj elementu params dla argumentów zmiennych|
|[CA2233](../code-quality/ca2233-operations-should-not-overflow.md)|Operacje nie powinny powodować przepełnienia|
|[CA2234](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)|Przekazuj obiekty System.Uri zamiast ciągów|
|[CA2243](../code-quality/ca2243-attribute-string-literals-should-parse-correctly.md)|Literały ciągu atrybutu powinny być analizowane poprawnie|