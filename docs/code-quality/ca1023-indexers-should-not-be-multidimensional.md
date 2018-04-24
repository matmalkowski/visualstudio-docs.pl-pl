---
title: 'CA1023: Indeksatory nie powinny być wielowymiarowe'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IndexersShouldNotBeMultidimensional
- CA1023
helpviewer_keywords:
- CA1023
- IndexersShouldNotBeMultidimensional
ms.assetid: ae499879-97f6-434e-a61d-1fedd231d2fb
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 876eb79237b843721b71a1879cfbb83e7a9918db
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
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