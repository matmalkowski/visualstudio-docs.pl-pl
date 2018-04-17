---
title: 'CA1045: Nie przekazuj typów przez odwołanie | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1045
- DoNotPassTypesByReference
helpviewer_keywords:
- CA1045
- DoNotPassTypesByReference
ms.assetid: bcc3900a-e092-4bb8-896f-cb83f6289968
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6640942827834ff1eafeecc84e1256ce3589443b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ca1045-do-not-pass-types-by-reference"></a>CA1045: Nie przekazuj typów przez odwołanie
|||  
|-|-|  
|TypeName|DoNotPassTypesByReference|  
|CheckId|CA1045|  
|Kategoria|Microsoft.Design|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Zawiera publiczne lub chronione metody w typie publicznego `ref` parametr, który przyjmuje typu pierwotnego, typu odwołania lub typem wartości, która nie jest jedną z wbudowanych typów.  
  
## <a name="rule-description"></a>Opis reguły  
 Przekazywanie typów przez odwołanie (przy użyciu `out` lub `ref`) wymaga środowiska z wskaźników, zrozumienie, jak są różne typy wartości i typy referencyjne i obsługi metod, które mają wiele wartości zwrotnych. Ponadto to różnica między `out` i `ref` parametry powszechnie jest niezrozumiały.  
  
 Po "przez odwołanie" jest typem referencyjnym, metoda zamierza użyć parametru do zwrócenia innego wystąpienia obiektu. (Przekazywanie poprzez odwołanie typu referencyjnego jest nazywany również przy użyciu podwójnego wskaźnika, wskaźnika do wskaźnika lub double pośredni.) Przy użyciu domyślnego wywoływanie Konwencji, która jest przekazanie "przez wartość", parametr, który ma już typ referencyjny uzyskuje wskaźnik do obiektu. Wskaźnik nie obiekt, który wskazuje, jest przekazywany przez wartość. Przekazywanie poprzez wartość oznacza, że metoda nie można zmienić wskaźnik, aby go wskazać nowe wystąpienie klasy odwołania typu, ale można zmienić obiektu, na które wskazuje zawartość. Dla większości aplikacji jest wystarczające i daje zachowanie, które mają.  
  
 Jeśli metoda musi zwracać innego wystąpienia, w tym celu należy użyć wartość zwracaną przez metodę. Zobacz <xref:System.String?displayProperty=fullName> klasy dla różnych metod, które działają na ciągi i zwraca nowe wystąpienie ciągu. Przy użyciu tego modelu, jest pozostawiany do wywołującego zdecydować, czy jest zachowywana oryginalna obiektu.  
  
 Mimo że wartości zwracane są typowe, a rzadko, odpowiednia `out` i `ref` parametrów wymaga kodowania w językach umiejętności i pośredniego projektu. Biblioteka architektów, którzy projektowania dla wszystkich użytkowników nie oczekiwać użytkownikom pracy wzorca z `out` lub `ref` parametrów.  
  
> [!NOTE]
>  Podczas pracy z parametrami dużych struktur dodatkowych zasobów, które są wymagane, aby skopiować te struktury może spowodować wpływ na wydajność podczas przekazywania przez wartość. W takich sytuacjach należy rozważyć przy użyciu `ref` lub `out` parametrów.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Ustalenie naruszenie tej reguły, która jest spowodowany przez typ wartości ma metodę zwracać obiektu jako jego wartości zwracanej. Jeśli metoda musi zwracać wiele wartości, zmodyfikowanie go do zwrócenia przez pojedyncze wystąpienie obiektu, który zawiera wartości.  
  
 Aby rozwiązać naruszenie tej reguły, która jest spowodowany przez typ referencyjny, upewnij się, czy zachowanie, które mają ma zwrócić nowe wystąpienie klasy odwołania. Jeśli tak jest, metoda należy używać jej wartości zwracanej w tym celu.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Można bezpiecznie pominąć ostrzeżenie od tej reguły; Ten projekt może jednak spowodować problemów z użytecznością.  
  
## <a name="example"></a>Przykład  
 Następująca biblioteka zawiera dwa implementacji klasy, która generuje odpowiedzi na opinie użytkownika. Pierwszy implementacji (`BadRefAndOut`) wymusza na użytkowniku biblioteki, aby zarządzać trzy wartości zwracanych. Drugi implementacji (`RedesignedRefAndOut`) upraszcza czynności użytkownika przez zwrócenie wystąpienia klasy kontenera (`ReplyData`) który zarządza danych jako pojedyncza jednostka.  
  
 [!code-csharp[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_1.cs)]  
  
## <a name="example"></a>Przykład  
 Następującej aplikacji przedstawiono czynności użytkownika. Wywołanie do biblioteki zmienioną (`UseTheSimplifiedClass` — metoda) jest bardziej bezpośrednie i informacje, które jest zwracany przez metodę można łatwo zarządzać. Dane wyjściowe z dwóch metod jest identyczne.  
  
 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_2.cs)]  
  
## <a name="example"></a>Przykład  
 Biblioteki następujący przykład przedstawia sposób `ref` parametrów dla typów odwołań są używane i pokazuje lepiej zaimplementować tę funkcję.  
  
 [!code-csharp[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_3.cs)]  
  
## <a name="example"></a>Przykład  
 Następującej aplikacji wywołuje każdą z tych metod w bibliotece, aby zademonstrować zachowanie.  
  
 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_4.cs)]  
  
 W tym przykładzie tworzy następujące dane wyjściowe.  
  
 **Zmiana wskaźnik - przekazany przez wartość:**  
**12345**  
**12345**  
**Zmiana wskaźnik - przekazywana przez odwołanie:**  
**12345**  
**12345 ABCDE**  
**Przekazywanie poprzez wartość zwrotna:**  
**12345 ABCDE**   
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1021: Unikaj parametrów out](../code-quality/ca1021-avoid-out-parameters.md)