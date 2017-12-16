---
title: 'CA1014: Oznacz zestawy atrybutem CLSCompliant | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
helpviewer_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
ms.assetid: 4fe57449-cf45-4745-bcd2-6345f1ed266d
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 44ce0dc31fc8e1d9acd2a2f93ca53fd1aeca3ee9
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2017
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014: Oznacz zestawy za pomocą CLSCompliantAttribute
|||  
|-|-|  
|TypeName|MarkAssembliesWithClsCompliant|  
|CheckId|CA1014|  
|Kategoria|Microsoft.Design|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Zestaw nie ma <xref:System.CLSCompliantAttribute?displayProperty=fullName> atrybut zastosowany do niego.  
  
## <a name="rule-description"></a>Opis reguły  
 The Common Language Specification (CLS) definiuje ograniczenia nazw, typów danych i reguł, z którymi muszą być zgodne zestawy, jeśli zostaną użyte w językach programowania. Dobry projekt mówią, że wszystkie zestawy jawnie wskazać zgodności ze specyfikacją CLS z <xref:System.CLSCompliantAttribute>. Jeśli ten atrybut nie jest obecny w zestawie, zestaw nie jest zgodne.  
  
 Istnieje możliwość zgodne ze specyfikacją CLS zestaw zawiera typy, lub wpisz elementów członkowskich, które nie są zgodne.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, Dodaj atrybut do zestawu. Zamiast oznaczenie całego zestawu jako niezgodne, należy określić, typu lub elementy członkowskie typu nie są zgodne i Oznacz jako takie tych elementów. Jeśli to możliwe powinno zapewniać alternatywnym, zgodnym ze specyfikacją CLS dla niezgodne elementy członkowskie, umożliwiając najszerszych możliwych odbiorców dostęp do wszystkich funkcji programu zestawu.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły. Jeśli nie chcesz, aby zestawu, aby było zgodne, zastosuj atrybut i ustaw dla niego wartość `false`.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono zestawu, który ma <xref:System.CLSCompliantAttribute?displayProperty=fullName> atrybut zastosowany, który deklaruje element zgodne ze specyfikacją CLS.  
  
 [!code-csharp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CSharp/ca1014-mark-assemblies-with-clscompliantattribute_1.cs)]
 [!code-cpp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CPP/ca1014-mark-assemblies-with-clscompliantattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/VisualBasic/ca1014-mark-assemblies-with-clscompliantattribute_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.CLSCompliantAttribute?displayProperty=fullName>   
 [Niezależność od języka i składniki niezależne od języka](/dotnet/standard/language-independence-and-language-independent-components)