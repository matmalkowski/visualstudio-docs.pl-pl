---
title: 'CA1804: Usuń nieużywane zmienne lokalne | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1804
- RemoveUnusedLocals
helpviewer_keywords:
- RemoveUnusedLocals
- CA1804
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3eb04f7b8e804bc776ee3d8beaf02b65cee75051
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ca1804-remove-unused-locals"></a>CA1804: Usuń nieużywane zmienne lokalne
|||  
|-|-|  
|TypeName|RemoveUnusedLocals|  
|CheckId|CA1804|  
|Kategoria|Microsoft.Performance|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Metoda deklaruje zmienną lokalną, ale nie używa prawdopodobnie zmiennej z wyjątkiem adresata instrukcji przypisania. Do analizy przez tę regułę muszą zostać skompilowane przetestowany zestawu z informacji o debugowaniu i program skojarzony plik bazy danych (.pdb) muszą być dostępne.  
  
## <a name="rule-description"></a>Opis reguły  
 Nieużywane zmienne lokalne i niepotrzebne przydziały zwiększają rozmiar zestawu i zmniejszają wydajność.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, usuń lub użyć zmiennej lokalnej. Należy pamiętać, że kompilator języka C# który dołączone [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] Usuwa nieużywane zmienne lokalne podczas `optimize` opcja jest włączona.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Pomiń ostrzeżenie od tej reguły, jeśli zmienna kompilatora wysyłanego. Istnieje również bezpieczne, aby pominąć ostrzeżenie od tej reguły, lub można wyłączyć reguły, jeśli wydajność i konserwacja kodu nie są główne obawy.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano kilka nieużywane zmienne lokalne.  
  
 [!code-vb[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/VisualBasic/ca1804-remove-unused-locals_1.vb)]
 [!code-csharp[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/CSharp/ca1804-remove-unused-locals_1.cs)]  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1809: Unikaj zbyt wielu zmiennych lokalnych](../code-quality/ca1809-avoid-excessive-locals.md)  
  
 [CA1811: Unikaj niewywoływanego kodu prywatnego](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812: Unikaj klas wewnętrznych bez wystąpień](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1801: Przejrzyj nieużywane parametry](../code-quality/ca1801-review-unused-parameters.md)