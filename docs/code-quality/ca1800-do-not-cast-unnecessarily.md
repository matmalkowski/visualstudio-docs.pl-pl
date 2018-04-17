---
title: 'CA1800: Nie Rzutuj niepotrzebnie | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 10/26/2017
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1800
- DoNotCastUnnecessarily
helpviewer_keywords:
- DoNotCastUnnecessarily
- CA1800
ms.assetid: b79a010a-6627-421e-8955-6007e32fa808
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- VB
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 81a8260b63e5f2206a124e98db9d519bd3dda6fc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800: Nie przeprowadzaj niepotrzebnych operacji rzutowania
|||  
|-|-|  
|TypeName|DoNotCastUnnecessarily|  
|CheckId|CA1800|  
|Kategoria|Microsoft.Performance|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
Metoda wykonuje zduplikowanych rzutowań w jednym z jego argumentów lub zmiennych lokalnych.

Do ukończenia analizy przez tę regułę przetestowany zestaw muszą zostać skompilowane przy użyciu informacji o debugowaniu, a program skojarzony plik bazy danych (.pdb) muszą być dostępne.  
  
## <a name="rule-description"></a>Opis reguły  
Zduplikowane rzutowania zmniejszają wydajność, zwłaszcza gdy rzutowania są wykonywane w niedużej iteracji. Dla operacji jawnego rzutowania duplikatów Zapisz wynik rzutowania w zmiennej lokalnej i użyć zmiennej lokalnej zamiast operacji rzutowania zduplikowane.  
  
Jeśli C# `is` operator używany do sprawdzania, czy rzutowanie powiedzie się przed wykonaniem rzeczywistego rzutowania należy wziąć pod uwagę testowanie `as` operator zamiast tego. To zapewnia te same funkcje bez wykonywanego przez operację niejawne rzutowanie `is` operatora. W języku C# w wersji 7.0 lub nowszy, należy użyć `is` operatora z [dopasowanie wzorca](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is) można sprawdzić konwersji typu i rzutowania wyrażenia ze zmienną tego typu w jednym kroku.
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby rozwiązać naruszenie tej reguły, zmodyfikuj implementacji metody, aby zminimalizować liczbę operacji rzutowania.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Jest bezpieczne, aby pominąć ostrzeżenie od tej reguły lub całkowicie, ignorowanie reguły, jeśli wydajność nie ma znaczenia.  
  
## <a name="examples"></a>Przykłady  
 W poniższym przykładzie przedstawiono metodę, która narusza regułę przy użyciu języka C# `is` operatora. Druga metoda spełnia reguły, zastępując `is` operatora z testem przed wynik `as` operatora, co zmniejsza liczbę operacji rzutowania na iteracji od dwóch do jednego. Trzecia metoda spełnia również reguły za pomocą `is` z [dopasowanie wzorca](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is) utworzyć zmienną odpowiedniego typu, jeśli konwersja typu powiedzie się.
  
 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_1.cs)]  

 W poniższym przykładzie przedstawiono metodę, `start_Click`, który ma wiele zduplikowanych rzutowań jawne, który narusza reguły i metody, `reset_Click`, które spełniają reguły, przechowując rzutowanie w zmiennej lokalnej.  
  
 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/VisualBasic/ca1800-do-not-cast-unnecessarily_2.vb)]
 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_2.cs)]  
  
## <a name="see-also"></a>Zobacz też  
[jako (odwołanie w C#)](/dotnet/csharp/language-reference/keywords/as)   
[jest (odwołanie w C#)](/dotnet/csharp/language-reference/keywords/is)