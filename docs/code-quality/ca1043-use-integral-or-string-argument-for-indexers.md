---
title: "CA1043: Należy użyć argumentu typu całkowitego lub ciąg dla indeksatorów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
helpviewer_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
ms.assetid: d7f14b9e-2220-4f80-b6b8-48c655a05701
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: aeaaf07dd3590e4dd703cfa239c48cb7e86b7f43
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca1043-use-integral-or-string-argument-for-indexers"></a>CA1043: Dla indeksatorów używaj argumentów integral lub string
|||  
|-|-|  
|TypeName|UseIntegralOrStringArgumentForIndexers|  
|CheckId|CA1043|  
|Kategoria|Microsoft.Design|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Typu publiczne lub chronione zawiera publiczne lub chronione indeksatora, który używa innego niż typ indeksu <xref:System.Int32?displayProperty=fullName>, <xref:System.Int64?displayProperty=fullName>, <xref:System.Object?displayProperty=fullName>, lub <xref:System.String?displayProperty=fullName>.  
  
## <a name="rule-description"></a>Opis reguły  
 Indeksatory, oznacza to, że właściwości indeksowanych powinny używać integer lub string dla indeksu. Te typy są zwykle używane do indeksowania struktur danych i zwiększyć użyteczność biblioteki. Użycie <xref:System.Object> typu powinny być ograniczone do tych przypadków, w którym określonego typu integer lub string nie można określić w czasie projektowania. Jeśli projekt wymaga innych typów dla indeksu, rozważenia, czy typ reprezentuje magazynu danych logicznych. Jeśli nie reprezentuje magazynu danych logicznych, należy użyć metody.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, Zmień indeks do typu integer lub string, lub użyj metody zamiast indeksatora.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Pomiń ostrzeżenie od tej zasady tylko po dokładnie biorąc pod uwagę konieczność niestandardowe indeksatora.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono indeksatorze, który używa <xref:System.Int32> indeksu.  
  
 [!code-csharp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CSharp/ca1043-use-integral-or-string-argument-for-indexers_1.cs)]
 [!code-cpp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CPP/ca1043-use-integral-or-string-argument-for-indexers_1.cpp)]
 [!code-vb[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/VisualBasic/ca1043-use-integral-or-string-argument-for-indexers_1.vb)]  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1023: Indeksatory nie powinny być wielowymiarowe](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)  
  
 [CA1024: Używaj właściwości wszędzie, gdzie jest to odpowiednie](../code-quality/ca1024-use-properties-where-appropriate.md)