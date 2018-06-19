---
title: 'Wykorzystanie — Ostrzeżenia '
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- vs.codeanalysis.usagerules
helpviewer_keywords:
- warnings, usage
- managed code analysis warnings, usage warnings
- usage warnings
ms.assetid: fe7dc2a3-289d-4bf7-a1e4-0947a81287c4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9e83421cefd78582c05f20d1efc936ba60c1fc47
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31927062"
---
# <a name="usage-warnings"></a>Wykorzystanie — Ostrzeżenia 
Ostrzeżenia wykorzystania obsługuje prawidłowego użycia platformy .NET.

## <a name="in-this-section"></a>W tej sekcji

|Reguła|Opis|
|----------|-----------------|
|[CA1801: Przejrzyj nieużywane parametry](../code-quality/ca1801-review-unused-parameters.md)|Podpis metody zawiera parametr, który nie jest używany w jej treści.|
|[CA1806: Nie ignoruj wyników metod](../code-quality/ca1806-do-not-ignore-method-results.md)|Nowy obiekt jest tworzony, ale nigdy nie jest używany; albo metoda, która tworzy i zwraca nowy ciąg, jest wywoływana, ale nowy ciąg nigdy nie jest używany; albo metody COM lub P/Invoke zwracają HRESULT lub kod błędu, który nigdy nie jest używany.|
|[CA1816: Wywołaj poprawnie metodę GC.SuppressFinalize](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)|Metody, która jest implementacją metody Dispose nie wywołuje GC. Metodę SuppressFinalize; lub GC wywołuje metodę, która nie jest implementacją metody Dispose. Metodę SuppressFinalize; lub wywołania metody GC. Metodę SuppressFinalize i przekazuje coś innego niż ten (Me w języku Visual Basic).|
|[CA2200: Zgłoś ponownie wyjątek, aby zachować szczegóły stosu](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|Wyjątek zgłoszony ponownie i wyjątek jest jawnie określone w instrukcji throw. Jeśli ponownie, określając wyjątek w instrukcji throw jest zgłaszany wyjątek, lista wywołania metody między oryginalnej metody, która zgłosiła wyjątek, a bieżąca metoda zostaną utracone.|
|[CA2201: Nie wywołuj zastrzeżonych typów wyjątku](../code-quality/ca2201-do-not-raise-reserved-exception-types.md)|Dzięki temu można twardych wykrycie i zdebugowanie pierwotnego błędu.|
|[CA2202: Nie likwiduj obiektów wiele razy](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|Implementacja metody zawiera ścieżki kodu, które powodują wielokrotne wywołania do System.IDisposable.Dispose lub równoważnika (na przykład użycie metody Close() na niektórych typach) dla tego samego obiektu.|
|[CA2204: Literały powinny być zapisane poprawnie](../code-quality/ca2204-literals-should-be-spelled-correctly.md)|Ciąg literału w treści metody zawiera jeden lub więcej wyrazów, które nie są rozpoznawane przez bibliotekę sprawdzania pisowni Microsoft.|
|[CA2205: Użyj zarządzanych odpowiedników interfejsu API Win32](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Wywołanie platformy metoda jest zdefiniowana i metody z równoważne funkcje istnieje w bibliotece klas programu .NET Framework.|
|[CA2207: Pola statyczne typu wartości inicjuj bezpośrednio](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|Typ wartości deklaruje jawny, statyczny konstruktor. Aby naprawić naruszenie tej zasady, zainicjuj wszystkie dane statyczne, gdy jest on zadeklarowany, i usuń konstruktor statyczny.|
|[CA2208: Poprawnie twórz wystąpienia wyjątków argumentów](../code-quality/ca2208-instantiate-argument-exceptions-correctly.md)|Wywołanie odnosi się do domyślnego (bezparametrowego) konstruktora typu wyjątku, który jest elementem ArgumentException lub od niego pochodzi, albo niepoprawny argument ciągu jest przekazywany do sparametryzowania konstruktora typu wyjątku lub pochodzi od elementu ArgumentException.|
|[CA2211: Pola, które nie są stałe, nie powinny być widoczne](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|Pola statyczne, które nie są ani stałe, ani tylko do odczytu, nie obsługują wielowątkowości. Dostęp do takiego pola muszą być dokładnie kontrolowane i wymaga zaawansowanych technik programowania dla synchronizacji dostępu do obiektu klasy.|
|[CA2212: Nie oznaczaj obsługiwanych składników za pomocą atrybutu WebMethod](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|Metody w typie, który dziedziczy z System.EnterpriseServices.ServicedComponent są oznaczane System.Web.Services.WebMethodAttribute. Ze względu na to, że atrybut WebMethodAttribute i metoda ServicedComponent mają sprzeczne zachowanie i wymagania dotyczące przepływu kontekstu i transakcji, w niektórych scenariuszach zachowanie metod będzie niepoprawne.|
|[CA2213: Pola możliwe do likwidacji powinny zostać zlikwidowane](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Typ, który implementuje element System.IDisposable, deklaruje pola takiego typu, które implementują także IDisposable. Metoda Dispose pola nie jest wywoływana przez metodę Dispose typu deklarującego.|
|[CA2214: Nie wywołuj metod, które można przesłonić, w konstruktorach](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|Konstruktor wywołuje metody wirtualnej, jest to możliwe, że Konstruktor wywołuje metodę wystąpienie nie zostało wykonane.|
|[CA2215: Metody Dispose powinny wywoływać metodę Dispose klasy podstawowej](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)|Jeśli typ dziedziczy z typu usuwalnego, musi on wywołać metodę Dispose typu podstawowego z własną metodę Dispose.|
|[CA2216: Typy możliwe do likwidacji powinny deklarować finalizator](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|Typ, który implementuje interfejs System.IDisposable i ma pól, które sugeruje korzystania z zasobów niezarządzanych nie implementuje finalizator w sposób opisany w metody Object.Finalize.|
|[CA2217: Nie oznaczaj wyliczeń za pomocą atrybutu FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|Wyliczenie widoczne na zewnątrz jest oznaczony atrybutem Flags i ma jedną lub więcej wartości, które nie są potęgami liczby dwa lub kombinacji zdefiniowanych wartości wyliczenie.|
|[CA2218: Przesłoń metodę GetHashCode przy przesłanianiu metody Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)|GetHashCode zwraca wartość opartą na bieżącym wystąpieniu, które jest odpowiednie dla algorytmów wyznaczających wartości skrótu i struktur danych, takich jak tabela skrótów. Dwa obiekty, które są równe i tego samego typu, muszą zwrócić tę samą wartość skrótu.|
|[CA2219: Nie zgłaszaj wyjątków w klauzulach wyjątku](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)|Kiedy wyjątek jest zgłaszany w klauzuli „finally” lub „fault”, nowy wyjątek ukrywa aktywny wyjątek. Gdy wyjątek jest zgłaszany w klauzuli „filter”, środowisko uruchomieniowe dyskretnie przechwytuje wyjątek. Dzięki temu można twardych wykrycie i zdebugowanie pierwotnego błędu.|
|[CA2220: Finalizatory powinny wywoływać finalizatory klasy podstawowej](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|Finalizacja musi być powielana w hierarchii dziedziczenia. Aby to zagwarantować, typy muszą wywołać metody Finalize swoich klas bazowych w ich własnej metodzie Finalize.|
|[CA2221: Finalizatory powinny być chronione](../code-quality/ca2221-finalizers-should-be-protected.md)|Finalizatory muszą korzystać z modyfikatora dostępu „family”.|
|[CA2222: Nie obniżaj dziedziczonej widoczności składowych](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|Nie należy zmieniać modyfikatora dostępu dla dziedziczonych elementów członkowskich. Zmiana dziedziczonej składowej na prywatną nie uniemożliwia wywołującym uzyskania dostępu do implementacji metody klasy podstawowej.|
|[CA2223: Składniki powinny różnić się nie tylko zwracanym typem](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md)|Chociaż środowisko uruchomieniowe języka wspólnego pozwala na używanie typów zwracanych do rozróżnienia między inaczej identycznymi członkami, funkcja ta nie jest objęta specyfikacją języka wspólnego (CLS) ani nie jest wspólną cechą języków programowania .NET.|
|[CA2224: Przesłaniaj metodę Equals w przypadku przeciążania operacji równości operatorów](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|Publiczny typ implementuje operator równości, ale nie przesłania metody Object.Equals.|
|[CA2225: Przeciążenia operatora mają nazwane alternatywy](../code-quality/ca2225-operator-overloads-have-named-alternates.md)|Wykryto przeciążony operator i nie znaleziono metody alternatywnej o oczekiwanej nazwie. Nazwane alternatywnego element członkowski zapewnia dostęp do funkcji operatora i jest dostępne dla deweloperów, którzy programów w językach, które nie obsługują operatory przeciążone.|
|[CA2226: Operatory powinny mieć symetryczne przeciążenia](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|Typ implementuje równości lub operator nierówności i nie implementuje przeciwną operatora.|
|[CA2227: Właściwości kolekcji powinny być tylko do odczytu](../code-quality/ca2227-collection-properties-should-be-read-only.md)|Właściwość zapisywalnej kolekcji pozwala użytkownikowi zastąpić kolekcję inną kolekcją. Właściwość tylko do odczytu uniemożliwia zastępowanie kolekcji, ale nadal umożliwia ustawienie poszczególnych członków.|
|[CA2228: Nie dostarczaj nieopublikowanych formatów zasobów](../code-quality/ca2228-do-not-ship-unreleased-resource-formats.md)|Pliki zasobów, które zostały utworzone przy użyciu wersji wstępnych programu .NET Framework nie może być używana przez obsługiwane wersje programu .NET Framework.|
|[CA2229: Zaimplementuj konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)|Aby naprawić naruszenie tej zasady, należy zaimplementować konstruktora serializacji. Dla zamkniętej klasy należy ustawić konstruktor prywatny; w przeciwnym razie powinien być chroniony.|
|[CA2230: Użyj parametrów dla argumentów zmiennych](../code-quality/ca2230-use-params-for-variable-arguments.md)|Typ publiczny lub chroniony zawiera metodę publiczną lub chronioną, która używa wywoływania VarArgs zamiast słowa kluczowego params.|
|[CA2231: Przeciążaj operator równości w przypadku przesłaniania metody ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Typ wartości zastępuje metodę Object.Equals, ale nie implementuje operatora równości.|
|[CA2232: Oznacz punkty wejścia platformy Windows Forms za pomocą atrybutu STAThread](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|STAThreadAttribute wskazuje, że model wątkowości COM dla aplikacji jest jednowątkowym apartamentem. Atrybut ten musi być obecny w punkcie wejścia każdej aplikacji korzystającej z Windows Forms; jeśli zostanie pominięty, składniki systemu Windows mogą nie działać poprawnie.|
|[CA2233: Operacje nie powinny powodować przepełnienia](../code-quality/ca2233-operations-should-not-overflow.md)|Operacje arytmetyczne powinien nie można wykonać bez uprzedniego sprawdzenia operandów, aby upewnić się, że wynik operacji nie jest poza zakresem możliwych wartości dla typów danych związane.|
|[CA2234: Przekaż obiekty System.Uri zamiast ciągów](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)|Wykonano wywołanie do metody, która ma parametr typu ciąg, którego nazwa zawiera „uri”, „URI”, „urn”, „URN”, „url” lub „URL”.  Deklarujący typ metody zawiera odpowiadające przeciążenie metody z parametrem System.Uri.|
|[CA2235: Oznacz wszystkie pola nieprzeznaczone do serializacji](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Pola wystąpienia typu, który nie może być serializowany, jest zadeklarowany w typie, który jest możliwy do serializacji.|
|[CA2236: Wywołuj metody klasy podstawowej w typach ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|Aby naprawić naruszenie tej zasady, należy wywołać metodę GetObjectData typu podstawowego lub konstruktor serializacji z odpowiadającej metody typu pochodnego albo konstruktora.|
|[CA2237: Oznacz typy ISerializable za pomocą atrybutu SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|Rozpoznane przez środowisko uruchomieniowe języka wspólnego jako możliwy do serializacji, typy musi być oznaczona atrybutem SerializableAttribute, nawet jeśli typ używa niestandardowej serializacji procedury dzięki implementacji interfejsu ISerializable.|
|[CA2238: Zaimplementuj poprawnie metody serializacji](../code-quality/ca2238-implement-serialization-methods-correctly.md)|Metoda, która obsługuje zdarzenie szeregowania, nie ma poprawnej sygnatury zwracanego typu lub widoczności.|
|[CA2239: Określ metody deserializacji dla pól opcjonalnych](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|Typ zawiera pola, które jest oznaczony atrybutem System.Runtime.Serialization.OptionalFieldAttribute i typ nie zapewnia obsługi metody deserializacji zdarzeń.|
|[CA2240: Zaimplementuj poprawnie interfejs ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)|Aby rozwiązać naruszenie tej reguły, wprowadzić metodę GetObjectData widoczne i którą można przesłonić i upewnij się, że wszystkie pola wystąpienia są uwzględnione w procesie serializacji lub jawnie oznaczone atrybutem NonSerializedAttribute.|
|[CA2241: Określ poprawne argumenty dla metod formatowania](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|Format argumentu przekazanego do System.String.Format nie zawiera elementu formatu, który odpowiada każdy argument obiekt, lub na odwrót.|
|[CA2242: Poprawnie testuj nie-liczby (NaN)](../code-quality/ca2242-test-for-nan-correctly.md)|To wyrażenie sprawdza, czy wartość to Single.Nan lub Double.Nan. Użyj Single.IsNan(Single) lub Double.IsNan(Double) do testowania wartości.|
|[CA2243: Analiza literałów typu string atrybutów powinna przebiegać poprawnie](../code-quality/ca2243-attribute-string-literals-should-parse-correctly.md)|Parametr literału ciągu atrybutu nie poprawnie przeanalizować dla danego adresu URL, identyfikator GUID lub wersji.|