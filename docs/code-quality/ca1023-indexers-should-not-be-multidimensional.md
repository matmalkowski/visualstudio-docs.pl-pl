---
title: "CA1023: Indeksatory nie powinny być wielowymiarowe | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IndexersShouldNotBeMultidimensional
- CA1023
helpviewer_keywords:
- CA1023
- IndexersShouldNotBeMultidimensional
ms.assetid: ae499879-97f6-434e-a61d-1fedd231d2fb
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2a3cf9ecfc25fc14fafceb1f36d8a02756e739b8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca1023-indexers-should-not-be-multidimensional"></a>CA1023: Indeksatory nie powinny być wielowymiarowe
|||  
|-|-|  
|TypeName|IndexersShouldNotBeMultidimensional|  
|CheckId|CA1023|  
|Kategoria|Microsoft.Design|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Typu publiczne lub chronione zawiera publiczne lub chronione indeksatora, który używa więcej niż jednego indeksu.  
  
## <a name="rule-description"></a>Opis reguły  
 Indeksatory, oznacza to, że właściwości indeksowanych powinny używać jednego indeksu. Wielowymiarowe indeksatory mogą znacznie ograniczyć użyteczność biblioteki. Jeśli projekt wymaga wiele indeksów, rozważenia, czy typ reprezentuje magazynu danych logicznych. Jeśli nie, należy użyć metody.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, zmianę projektu do użycia pojedynczy całkowitą lub indeksu ciągu lub użyć metody zamiast indeksatora.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Pomiń ostrzeżenie od tej zasady tylko po dokładnie biorąc pod uwagę konieczność niestandardowe indeksatora.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono typu `DayOfWeek03`, z wielowymiarowym indeksatora, który narusza zasady. Indeksator może być traktowany jako typ konwersji i w związku z tym lepiej jest udostępniany jako metodę. Typ jest przeprojektowany w `RedesignedDayOfWeek03` do zaspokojenia reguły.  
  
 [!code-vb[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/VisualBasic/ca1023-indexers-should-not-be-multidimensional_1.vb)]
 [!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CPP/ca1023-indexers-should-not-be-multidimensional_1.cpp)]
 [!code-csharp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CSharp/ca1023-indexers-should-not-be-multidimensional_1.cs)]  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1043: Używaj argumentu integral lub string dla indeksatorów](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)  
  
 [CA1024: Używaj właściwości wszędzie tam, gdzie jest to odpowiednie](../code-quality/ca1024-use-properties-where-appropriate.md)