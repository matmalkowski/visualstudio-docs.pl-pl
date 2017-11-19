---
title: "CA2224: Przesłoń metodę equals przeciążając operator equals | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2224
- OverrideEqualsOnOverloadingOperatorEquals
- OverrideEqualsOnOverridingOperatorEquals
helpviewer_keywords:
- OverrideEqualsOnOverloadingOperatorEquals
- CA2224
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 44ba1c444d9348babcf07bfd807d6b0767bf3de9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca2224-override-equals-on-overloading-operator-equals"></a>CA2224: Przesłoń metodę equals, przeciążając operator equals
|||  
|-|-|  
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|  
|CheckId|CA2224|  
|Kategoria|Microsoft.Usage|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Publiczny typ implementuje operator równości, ale nie przesłania <xref:System.Object.Equals%2A?displayProperty=fullName>.  
  
## <a name="rule-description"></a>Opis reguły  
 Operator równości ma być składniowo wygodny sposób uzyskać dostęp do funkcji <xref:System.Object.Equals%2A> metody. W przypadku zastosowania operatora równości, swojej logiki muszą być identyczne z <xref:System.Object.Equals%2A>.  
  
 Kompilator języka C# wygeneruje ostrzeżenie, jeśli kod narusza tę regułę.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Ustalenie naruszenie tej reguły, należy albo usunąć implementacji operator równości, lub zastąpienie <xref:System.Object.Equals%2A> i ma dwie metody zwracają takie same wartości. Jeśli operator równości nie wprowadza niespójne działanie, można naprawić naruszenie, dostarczając implementację <xref:System.Object.Equals%2A> wywołującym <xref:System.Object.Equals%2A> metody w klasie podstawowej.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Można bezpiecznie pominąć ostrzeżenie od tej reguły, jeśli taką samą wartość jak dziedziczone implementacja zwraca operator równości <xref:System.Object.Equals%2A>. Przykład zawiera typ, którego można bezpiecznie pominąć ostrzeżenie od tej reguły.  
  
## <a name="examples-of-inconsistent-equality-definitions"></a>Przykładowe definicje niespójne równości  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie przedstawiono typu z definicjami niespójne równości. `BadPoint`zmienia znaczenie równości, zapewniając implementacja niestandardowa operatora równości, ale nie przesłania <xref:System.Object.Equals%2A> tak, aby zachowuje się tak samo.  
  
### <a name="code"></a>Kod  
 [!code-csharp[FxCop.Usage.OperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_1.cs)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod testów zachowanie `BadPoint`.  
  
 [!code-csharp[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_2.cs)]  
  
 W tym przykładzie tworzy następujące dane wyjściowe.  
  
 **= (1,1 [0]) i b = (2,2 [1]) są takie same? Brak**  
**== b? Brak**  
**a1 i są takie same? Tak**  
**a1 ==? Tak**  
**b i bcopy są takie same? Brak**  
**b == bcopy? Tak**   
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia typu, który technicznie narusza tę regułę, ale nie działają w sposób niezgodny.  
  
 [!code-csharp[FxCop.Usage.ValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_3.cs)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod testów zachowanie `GoodPoint`.  
  
 [!code-csharp[FxCop.Usage.TestValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_4.cs)]  
  
 W tym przykładzie tworzy następujące dane wyjściowe.  
  
 **= (1,1) i b = (2,2) są takie same? Brak**  
**== b? Brak**  
**a1 i są takie same? Tak**  
**a1 ==? Tak**  
**b i bcopy są takie same? Tak**  
**b == bcopy? Tak**   
## <a name="class-example"></a>Przykład klasy  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie przedstawiono klasę (typ odwołania), która narusza tę regułę.  
  
### <a name="code"></a>Kod  
 [!code-csharp[FxCop.Usage.OverrideEqualsClassViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_5.cs)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład poprawia naruszenie przez zastąpienie <xref:System.Object.Equals%2A?displayProperty=fullName>.  
  
 [!code-csharp[FxCop.Usage.OverrideEqualsClassFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_6.cs)]  
  
## <a name="structure-example"></a>Przykład struktury  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie przedstawiono struktury (typ wartości), który narusza tę regułę.  
  
### <a name="code"></a>Kod  
 [!code-csharp[FxCop.Usage.OverrideEqualsStructViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_7.cs)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład poprawia naruszenie przez zastąpienie <xref:System.ValueType.Equals%2A?displayProperty=fullName>.  
  
 [!code-csharp[FxCop.Usage.OverrideEqualsStructFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_8.cs)]  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1046: Nie przeciążaj operatora równości w typach referencyjnych](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225: Operator overloads ma nazwanych zastępców](../code-quality/ca2225-operator-overloads-have-named-alternates.md)  
  
 [CA2226: Operatory powinny mieć symetryczne przeciążenia](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2218: Zastąp GetHashCode przy zastępowaniu Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
 [CA2231: Przeciąż operator equals przy zastępowaniu ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)