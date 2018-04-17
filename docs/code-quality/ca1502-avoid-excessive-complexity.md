---
title: 'CA1502: Unikaj nadmiernej złożoności | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- AvoidExcessiveComplexity
- CA1502
helpviewer_keywords:
- CA1502
- AvoidExcessiveComplexity
ms.assetid: d735454b-2f8f-47ce-907d-f7a5a5391221
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 990a1336019325313c2152b38b7fa8525d52720a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ca1502-avoid-excessive-complexity"></a>CA1502: Unikaj nadmiernej złożoności
|||  
|-|-|  
|TypeName|AvoidExcessiveComplexity|  
|CheckId|CA1502|  
|Kategoria|Microsoft.Maintainability|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Metoda ma złożoność cyklomatyczną nadmierne.  
  
## <a name="rule-description"></a>Opis reguły  
 *Złożoność Cyklomatyczną* mierzy liczbę niezależnych liniowo ścieżek za pomocą metody, która jest określana przez liczba i złożoność warunkowych gałęzi. Złożoność cyklomatyczną niski na ogół wskazuje metodę, która ułatwia zrozumienie, testowania i obsługi. Złożoność cyklomatyczną jest obliczana na podstawie Wykres przepływu sterowania, metody i znajduje się w następujący sposób:  
  
 złożoność cyklomatyczną = liczba krawędzi - liczba węzłów + 1  
  
 gdy węzeł reprezentuje Rozgałęzienie logiki i krawędzi reprezentuje wiersz między węzłami.  
  
 Reguła raporty naruszenie, gdy złożoność cyklomatyczną jest więcej niż 25.  
  
 Dowiedz się więcej o metryk kodu [mierzenie złożoności i łatwości konserwacji zarządzanego kodu](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md),  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, zrefaktoryzuj metodę, aby zmniejszyć złożoność cyklomatyczną o jej.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli łatwo nie można zmniejszyć złożoność i metoda jest łatwe do zrozumienia, testowania i obsługi. W szczególności, metody, która zawiera dużą `switch` (`Select` w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) instrukcja jest kandydatem do wykluczenia. Ryzyko destabilizing kod podstawowy opóźnione w cyklu rozwoju lub wprowadzenia nieoczekiwane zmiany zachowania środowiska uruchomieniowego w uprzednio wysłane kod może przeważają zalet utrzymanie refaktoryzacji kodu.  
  
## <a name="how-cyclomatic-complexity-is-calculated"></a>Sposób obliczania złożoność Cyklomatyczną  
 Złożoność cyklomatyczną jest obliczany przez dodanie 1 do następującego:  
  
-   Liczba gałęzi (takich jak `if`, `while`, i `do`)  
  
-   Liczba `case` instrukcje w `switch`  
  
 Poniższe przykłady przedstawiają metody, które mają różne złożoności cyklomatycznej.  
  
## <a name="example"></a>Przykład  
 **Złożoność Cyklomatyczną o wartości 1**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_1.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_1.vb)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_1.cs)]  
  
## <a name="example"></a>Przykład  
 **Złożoność Cyklomatyczną o wartości 2**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_2.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_2.vb)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_2.cs)]  
  
## <a name="example"></a>Przykład  
 **Złożoność Cyklomatyczną o wartości 3**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_3.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_3.vb)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_3.cs)]  
  
## <a name="example"></a>Przykład  
 **Złożoność Cyklomatyczną o wartości 8**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_4.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_4.vb)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_4.cs)]  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1501: Unikaj nadmiernego dziedziczenia](../code-quality/ca1501-avoid-excessive-inheritance.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Mierzenie złożoności i poziomu łatwości konserwacji kodu zarządzanego](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)