---
title: 'CA1804: Usuń nieużywane zmienne lokalne | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1804
- RemoveUnusedLocals
helpviewer_keywords:
- RemoveUnusedLocals
- CA1804
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: cc9e9765e0dc1240d6255301c0c87c8986ff6579
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42633027"
---
# <a name="ca1804-remove-unused-locals"></a>CA1804: Usuń nieużywane zmienne lokalne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA1804: Usuń nieużywane zmienne lokalne](https://docs.microsoft.com/visualstudio/code-quality/ca1804-remove-unused-locals).  
  
Element TypeName | RemoveUnusedLocals |  
| CheckId | CA1804 |  
| Kategoria | Microsoft.Performance|  
| Zmiana powodująca niezgodność | Bez podziału |  
  
## <a name="cause"></a>Przyczyna  
 Metoda deklaruje zmienną lokalną, ale nie używa prawdopodobnie zmiennej, z wyjątkiem jako adresata w instrukcji przypisania. Do analizy przez tę regułę przetestowane zestawu muszą zostać skompilowane przy użyciu informacji o debugowaniu i plik bazy danych (PDB) programu skojarzone muszą być dostępne.  
  
## <a name="rule-description"></a>Opis reguły  
 Nieużywane zmienne lokalne i niepotrzebne przydziały zwiększają rozmiar zestawu i zmniejszają wydajność.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej zasady, usuń lub użyć zmiennej lokalnej. Należy pamiętać, że kompilator języka C#, dołączone [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] Usuwa nieużywane zmienne lokalne podczas `optimize` opcja jest włączona.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Pomijaj ostrzeżeń dla tej reguły, jeśli zmienna kompilatora emitowane. Bezpieczne jest również Pomijaj ostrzeżeń dla tej reguły lub wyłączyć regułę, jeśli wydajność i konserwacja kodu nie są podstawowe kwestie.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje nieużywane zmienne lokalne.  
  
 [!code-csharp[FxCop.Performance.UnusedLocals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals/cs/FxCop.Performance.UnusedLocals.cs#1)]
 [!code-vb[FxCop.Performance.UnusedLocals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals/vb/FxCop.Performance.UnusedLocals.vb#1)]  
  
## <a name="related-rules"></a>Powiązane reguły  
 [CA1809: Unikaj zbyt wielu zmiennych lokalnych](../code-quality/ca1809-avoid-excessive-locals.md)  
  
 [CA1811: Unikaj niewywoływanego kodu prywatnego](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812: Unikaj klas wewnętrznych bez wystąpień](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1801: Przejrzyj nieużywane parametry](../code-quality/ca1801-review-unused-parameters.md)



