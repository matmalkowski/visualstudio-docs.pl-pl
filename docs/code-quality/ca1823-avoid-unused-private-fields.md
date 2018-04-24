---
title: 'CA1823: Unikaj nieużywanych pól prywatnych'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUnusedPrivateFields
- CA1823
helpviewer_keywords:
- AvoidUnusedPrivateFields
- CA1823
ms.assetid: 614f94f6-0dc7-430f-8124-cb889a4a720f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1b8d3e1738b217d836bd0e4ca60178d2d65ac686
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca1823-avoid-unused-private-fields"></a>CA1823: Unikaj nieużywanych pól prywatnych
|||
|-|-|
|TypeName|AvoidUnusedPrivateFields|
|CheckId|CA1823|
|Kategoria|Microsoft.Performance|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Ta reguła jest zgłaszany, gdy pole prywatne w kodzie istnieje, ale nie jest używany przez wszystkie ścieżki kodu.

## <a name="rule-description"></a>Opis reguły
 Zostały wykryte pola prywatne, które w zestawie nie są widoczne jako dostępne.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby rozwiązać naruszenie tej reguły, Usuń to pole lub Dodaj kod, który korzysta z niego.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły.

## <a name="related-rules"></a>Powiązanych reguł
 [CA1812: Unikaj klas wewnętrznych bez wystąpień](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: Przejrzyj nieużywane parametry](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: Usuń nieużywane zmienne lokalne](../code-quality/ca1804-remove-unused-locals.md)

 [CA1811: Unikaj niewywoływanego kodu prywatnego](../code-quality/ca1811-avoid-uncalled-private-code.md)