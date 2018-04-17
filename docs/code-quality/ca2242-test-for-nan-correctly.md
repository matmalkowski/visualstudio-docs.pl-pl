---
title: 'CA2242: Testuj liczby (NaN) poprawnie | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- TestForNaNCorrectly
- CA2242
helpviewer_keywords:
- CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a782c0b3f32c9733b47ded29852e006f8ba7c1aa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242: Testuj poprawnie pod kątem NaN
|||  
|-|-|  
|TypeName|TestForNaNCorrectly|  
|CheckId|CA2242|  
|Kategoria|Microsoft.Usage|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Wyrażenie porównanie wartości ze <xref:System.Single.NaN?displayProperty=fullName> lub <xref:System.Double.NaN?displayProperty=fullName>.  
  
## <a name="rule-description"></a>Opis reguły  
 <xref:System.Double.NaN?displayProperty=fullName>, która reprezentuje nie liczby, gdy operacji arytmetycznej jest niezdefiniowana. Dowolne wyrażenie, który umożliwia sprawdzenie równość wartości i <xref:System.Double.NaN?displayProperty=fullName> zawsze zwraca `false`. Dowolne wyrażenie, który umożliwia sprawdzenie nierówności między wartością i <xref:System.Double.NaN?displayProperty=fullName> zawsze zwraca `true`.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby rozwiązać naruszenie tej reguły i określić dokładnie, czy wartość reprezentuje <xref:System.Double.NaN?displayProperty=fullName>, użyj <xref:System.Single.IsNaN%2A?displayProperty=fullName> lub <xref:System.Double.IsNaN%2A?displayProperty=fullName> do testowania wartości.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono dwóch wyrażeń, które niepoprawnie test wartość względem <xref:System.Double.NaN?displayProperty=fullName> i wyrażenie używające poprawnie <xref:System.Double.IsNaN%2A?displayProperty=fullName> do testowania wartości.  
  
 [!code-vb[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/VisualBasic/ca2242-test-for-nan-correctly_1.vb)]
 [!code-csharp[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/CSharp/ca2242-test-for-nan-correctly_1.cs)]