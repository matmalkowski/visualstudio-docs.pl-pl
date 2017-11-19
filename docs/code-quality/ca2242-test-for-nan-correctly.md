---
title: 'CA2242: Testuj liczby (NaN) poprawnie | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TestForNaNCorrectly
- CA2242
helpviewer_keywords: CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: dd7f648880debe4b982d10e97aa7133419e0e840
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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