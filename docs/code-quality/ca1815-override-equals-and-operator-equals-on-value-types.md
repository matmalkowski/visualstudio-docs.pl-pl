---
title: 'CA1815: Przesłoń metodę equals i operator równości w typach wartości | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1815
- OverrideEqualsAndOperatorEqualsOnValueTypes
helpviewer_keywords:
- OverrideEqualsAndOperatorEqualsOnValueTypes
- CA1815
ms.assetid: 0a8ab3a3-ee8e-46f7-985d-dcf00c89363b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c4f5667977ed25da03d5d651e28c5ae3c3f4a3e0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ca1815-override-equals-and-operator-equals-on-value-types"></a>CA1815: Przesłoń metodę equals i operator równości dla typów wartości
|||  
|-|-|  
|TypeName|OverrideEqualsAndOperatorEqualsOnValueTypes|  
|CheckId|CA1815|  
|Kategoria|Microsoft.Performance|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Typ wartości publiczny nie przesłania <xref:System.Object.Equals%2A?displayProperty=fullName>, lub nie implementuje operator równości (==). Ta reguła sprawdza wyliczenia.  
  
## <a name="rule-description"></a>Opis reguły  
 Dla typów wartości, dziedziczone wykonania <xref:System.Object.Equals%2A> używa biblioteki odbić i porównuje wartości wszystkich pól. Odbicie jest obliczeniowo kosztowne, a porównanie równości każdego pola może być niepotrzebne. Jeśli użytkownicy do porównywania lub sortowania wystąpienia lub używać ich jako tabeli klawiszy skrótów, powinien implementować danego typu wartości <xref:System.Object.Equals%2A>. Jeśli język programowania obsługuje przeciążania operatorów, należy również zapewniać implementację elementu Operatory równości i nierówności.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, zapewniać implementację elementu <xref:System.Object.Equals%2A>. Jeśli to możliwe, należy zaimplementować operatora równości.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli wystąpienia typu wartości nie będzie można porównywać ze sobą.  
  
## <a name="example-of-a-violation"></a>Przykładem naruszenia  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie przedstawiono struktury (typ wartości), który narusza tę regułę.  
  
### <a name="code"></a>Kod  
 [!code-csharp[FxCop.Performance.OverrideEqualsViolation#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_1.cs)]  
  
## <a name="example-of-how-to-fix"></a>Przykładem do naprawy  
  
### <a name="description"></a>Opis  
 Poniższy przykład poprawki poprzedniej naruszenie przez zastąpienie <xref:System.ValueType.Equals%2A?displayProperty=fullName> i wdrażanie Operatory równości (==,! =).  
  
### <a name="code"></a>Kod  
 [!code-csharp[FxCop.Performance.OverrideEqualsFixed#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_2.cs)]  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA2224: Przesłaniaj metodę Equals w przypadku przeciążania operacji równości operatorów](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2231: Przeciążaj operator równości w przypadku przesłaniania metody ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)  
  
 [CA2226: Operatory powinny mieć symetryczne przeciążenia](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Object.Equals%2A?displayProperty=fullName>