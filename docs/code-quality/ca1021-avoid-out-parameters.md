---
title: 'CA1021: Unikanie parametrów wyjściowych'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1021
- AvoidOutParameters
helpviewer_keywords:
- AvoidOutParameters
- CA1021
ms.assetid: 970f2304-842c-4fb7-9734-f3871da8d479
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 86503ae5abb994b5b1d687744371a57ff6086e43
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca1021-avoid-out-parameters"></a>CA1021: Unikanie parametrów wyjściowych
|||
|-|-|
|TypeName|AvoidOutParameters|
|CheckId|CA1021|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Zawiera publiczne lub chronione metody w typie publicznego `out` parametru.

## <a name="rule-description"></a>Opis reguły
 Przekazywanie typów przez odwołanie (przy użyciu `out` lub `ref`) wymaga środowiska z wskaźników, zrozumienie, jak są różne typy wartości i typy referencyjne i obsługi metod zawierających wiele wartości zwrotnych. Ponadto to różnica między `out` i `ref` parametry powszechnie jest niezrozumiały.

 Po "przez odwołanie" jest typem referencyjnym, metoda zamierza użyć parametru do zwrócenia innego wystąpienia obiektu. Przekazywanie poprzez odwołanie typu referencyjnego jest nazywany również przy użyciu podwójnego wskaźnika, wskaźnika do wskaźnika lub pośredni dwa razy. Przy użyciu domyślnej Wywoływanie Konwencji, która jest przekazanie "przez wartość", parametr, który ma już typ referencyjny uzyskuje wskaźnik do obiektu. Wskaźnik nie obiekt, który wskazuje, jest przekazywany przez wartość. Przekaż przez wartość oznacza, że metoda nie można zmienić wskaźnik do jego punktu do nowego wystąpienia typu referencyjnego. Jednak można zmienić obiektu, na które wskazuje zawartość. Dla większości aplikacji jest wystarczające i zapewni żądane zachowanie.

 Jeśli metoda musi zwracać innego wystąpienia, w tym celu należy użyć wartość zwracaną przez metodę. Zobacz <xref:System.String?displayProperty=fullName> klasy dla różnych metod, które działają na ciągi i zwraca nowe wystąpienie ciągu. Użycie tego modelu wywołującego należy zdecydować, czy jest zachowywana oryginalna obiektu.

 Mimo że wartości zwracane są typowe, a rzadko, odpowiednia `out` i `ref` parametrów wymaga kodowania w językach umiejętności i pośredniego projektu. Biblioteka architektów, którzy projektowania dla wszystkich użytkowników nie oczekiwać użytkownikom pracy wzorca z `out` lub `ref` parametrów.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Ustalenie naruszenie tej reguły, która jest spowodowany przez typ wartości ma metodę zwracać obiektu jako jego wartości zwracanej. Jeśli metoda musi zwracać wiele wartości, zmodyfikowanie go do zwrócenia przez pojedyncze wystąpienie obiektu, który zawiera wartości.

 Aby rozwiązać naruszenie tej reguły, która jest spowodowany przez typ referencyjny, upewnij się, czy zachowanie ma zwrócić nowe wystąpienie klasy odwołania. Jeśli tak jest, metoda należy używać jej wartości zwracanej w tym celu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły. Ten projekt może jednak spowodować problemów z użytecznością.

## <a name="example"></a>Przykład
 Następująca biblioteka zawiera dwa implementacji klasy, która generuje odpowiedzi na opinie użytkownika. Pierwszy implementacji (`BadRefAndOut`) wymusza na użytkowniku biblioteki, aby zarządzać trzy wartości zwracanych. Drugi implementacji (`RedesignedRefAndOut`) upraszcza czynności użytkownika przez zwrócenie wystąpienia klasy kontenera (`ReplyData`) który zarządza danych jako pojedyncza jednostka.

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_1.cs)]

## <a name="example"></a>Przykład
 Następującej aplikacji przedstawiono czynności użytkownika. Wywołanie do biblioteki zmienioną (`UseTheSimplifiedClass` — metoda) jest bardziej bezpośrednie i zwracanych przez metodę informacji z łatwością zarządzać. Dane wyjściowe z dwóch metod jest identyczne.

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_2.cs)]

## <a name="example"></a>Przykład
 Biblioteki następujący przykład przedstawia sposób `ref` parametrów dla typów odwołań są używane i przedstawia lepiej zaimplementować tę funkcję.

 [!code-csharp[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_3.cs)]

## <a name="example"></a>Przykład
 Następującej aplikacji wywołuje każdą z tych metod w bibliotece, aby zademonstrować zachowanie.

 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_4.cs)]

 W tym przykładzie tworzy następujące dane wyjściowe.

 **Zmiana wskaźnik - przekazany przez wartość:**
**12345**
**12345**
**wskaźnik zmiana - przekazany przez odwołanie:** 
 ** 12345**
**12345 ABCDE**
**przekazanie przez wartość zwrotna:**
**12345 ABCDE**
## <a name="try-pattern-methods"></a>Wypróbuj metody wzorca

### <a name="description"></a>Opis
 Metody, które implementują **spróbuj\<coś >** wzorca, takich jak <xref:System.Int32.TryParse%2A?displayProperty=fullName>, nie wywołuj to naruszenie. W poniższym przykładzie przedstawiono struktury (typ wartości), który implementuje <xref:System.Int32.TryParse%2A?displayProperty=fullName> metody.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.TryPattern#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_5.cs)]

## <a name="related-rules"></a>Powiązanych reguł
 [CA1045: Nie przekazuj typów przez odwołanie](../code-quality/ca1045-do-not-pass-types-by-reference.md)