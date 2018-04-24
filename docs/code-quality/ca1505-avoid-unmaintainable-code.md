---
title: 'CA1505: Unikaj kodu niemożliwego w utrzymaniu'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUnmaintainableCode
- CA1505
helpviewer_keywords:
- AvoidUnmaintainableCode
- CA1505
ms.assetid: 8292b268-5929-4221-b699-f9c414bcec5d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b65e6c8c7826887e411b2210b613633c1e963aaf
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505: Unikaj kodu niemożliwego w utrzymaniu
|||
|-|-|
|TypeName|AvoidUnmantainableCode|
|CheckId|CA1505|
|Kategoria|Microsoft.Maintainability|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Typ lub metoda ma niską wartość indeksu konserwacji.

## <a name="rule-description"></a>Opis reguły
 Indeks łatwości utrzymania jest obliczana przy użyciu następujących metryk: wierszy kodu, program woluminu i złożoność cyklomatyczną. Program wolumin jest miarą trudności zrozumienia typu lub metody, która jest oparta na liczbie operatory i argumenty w kodzie. Złożoność Cyklomatyczną jest miarą strukturalnych złożoność typu lub metody. Dowiedz się więcej o metryk kodu [mierzenie złożoności i łatwości konserwacji zarządzanego kodu](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md).

 Indeks łatwości utrzymania niski wskazuje, że typ lub metoda jest prawdopodobnie trudne w utrzymaniu i będzie odpowiednimi kandydatami do.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić to naruszenie, zmodyfikowanie typu lub metody i spróbuj podzielić go na mniejsze i bardziej ukierunkowaną typach lub metodach.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Wyklucz to ostrzeżenie, gdy typ lub metoda jest nadal łatwy w obsłudze, niezależnie od jego duży rozmiar lub typ lub metoda nie może zostać podzielony.

## <a name="see-also"></a>Zobacz też
 [Ostrzeżenia dotyczące utrzymania](../code-quality/maintainability-warnings.md) [mierzenie złożoności i łatwości konserwacji zarządzanego kodu](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)