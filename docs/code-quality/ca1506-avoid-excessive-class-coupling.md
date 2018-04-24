---
title: 'CA1506: Unikaj nadmiernego sprzężenia klas'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidExcessiveClassCoupling
- CA1506
helpviewer_keywords:
- AvoidExcessiveClassCoupling
- CA1506
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 156e3ba4cdf31c587bb526eb40630e8f865f7cb4
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506: Unikaj nadmiernego sprzężenia klas
|||
|-|-|
|TypeName|AvoidExcessiveClassCoupling|
|CheckId|CA1506|
|Kategoria|Microsoft.Maintainability|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ lub metoda jest sprzężona z wieloma innymi typami.

## <a name="rule-description"></a>Opis reguły
 Ta reguła mierzy sprzęgnięcie klasy przez liczenie unikatowych odwołań typów, które zawiera typ lub metoda.

 Typy i metody, które mają wysokim stopniu sprzężenia klas mogą być trudne w utrzymaniu. Jest dobrym rozwiązaniem, typy i metody, które wykazują spójność wysoki i niski sprzężenia.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby rozwiązać to naruszenie, spróbuj zmienić układ typu lub metody, aby zmniejszyć liczbę typów, do których jest sprzężona.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Typ lub metoda jest nadal rozpatrywane w utrzymaniu niezależnie od jego dużej liczby zależne od innych typów, należy wyłączyć to ostrzeżenie.

## <a name="see-also"></a>Zobacz też
 [Ostrzeżenia dotyczące utrzymania](../code-quality/maintainability-warnings.md) [mierzenie złożoności i łatwości konserwacji zarządzanego kodu](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)