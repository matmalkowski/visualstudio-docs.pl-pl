---
title: 'CA2225: Operator overloads ma nazwanych zastępców | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
helpviewer_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
ms.assetid: af8f7ab1-63ad-4861-afb9-b7a7a2be15e1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a46b2d7a158fb340f56f6f38c2889fa2696c6cf0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225: Operator overloads ma nazwanych zastępców
|||  
|-|-|  
|TypeName|OperatorOverloadsHaveNamedAlternates|  
|CheckId|CA2225|  
|Kategoria|Microsoft.Usage|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Wykryto przeciążony operator i nie znaleziono metody alternatywnej o oczekiwanej nazwie.  
  
## <a name="rule-description"></a>Opis reguły  
 Przeładowanie operatora umożliwia korzystanie z symboli do reprezentowania obliczenia dla typu. Na przykład typ, który overloads znak plus (+) do dodania zwykle mają inny członek o nazwie "Dodaj". Nazwane alternatywnego element członkowski zapewnia dostęp do funkcji operatora i jest dostępne dla deweloperów, którzy programów w językach, które nie obsługują operatory przeciążone.  
  
 Ta reguła sprawdza, czy operatory wymienione w poniższej tabeli.  
  
|C#|Visual Basic|C++|Alternatywna nazwa|  
|---------|------------------|-----------|--------------------|  
|+ (plik binarny)|+|+ (plik binarny)|Dodaj|  
|+=|+=|+=|Dodaj|  
|&|I|&|BitwiseAnd|  
|&=|I =|&=|BitwiseAnd|  
|&#124;|Lub|&#124;|BitwiseOr|  
|&#124;=|Lub =|&#124;=|BitwiseOr|  
|--|Brak|--|Dekrementacji|  
|/|/|/|Podziel|  
|/=|/=|/=|Podziel|  
|==|=|==|równa się|  
|^|XOR|^|XOR|  
|^=|XOR =|^=|XOR|  
|>|>|>|{1&gt;Compare&lt;1}|  
|>=|>=|>=|{1&gt;Compare&lt;1}|  
|++|Brak|++|Przyrost|  
|<>|!=|równa się|  
|<<|<<|<<|LeftShift|  
|<<=|<<=|<<=|LeftShift|  
|<|<|<|{1&gt;Compare&lt;1}|  
|<=|<=|\<=|{1&gt;Compare&lt;1}|  
|&&|Brak|&&|LogicalAnd|  
|&#124;&#124;|Brak|&#124;&#124;|LogicalOr|  
|!|Brak|!|LogicalNot|  
|%|Mod|%|Mod lub pozostałej|  
|%=|Brak|%=|Mod|  
|* (binary)|*|*|Mnożenia|  
|*=|Brak|*=|Mnożenia|  
|~|nie|~|OnesComplement|  
|>>|>>|>>|RightShift|  
=|Brak|>>=|RightShift|  
|-(plik binarny)|-(plik binarny)|-(plik binarny)|Odejmowanie|  
|-=|Brak|-=|Odejmowanie|  
|true|IsTrue|Brak|IsTrue (właściwość)|  
|-(jednoargumentowy)|Brak|-|Negate —|  
|+ (jednoargumentowy)|Brak|+|plus|  
|false|IsFalse|False|IsTrue (właściwość)|  
  
 Brak == nie może zostać przeciążony w wybranym języku.  
  
 Reguła sprawdza również operatory rzutowania jawne i niejawne w typie (`SomeType`) przez skontrolowanie metody o nazwie `ToSomeType` i `FromSomeType`.  
  
 W języku C# Jeśli jest przeciążony operator binarny, odpowiedniego operatora przypisania, jest również niejawnie przeciążona.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby rozwiązać naruszenie tej reguły, zaimplementuj alternatywną metodą dla operatora; Nazwa przy użyciu zalecanych alternatywnej nazwy.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżenia od tej reguły, w przypadku wdrażania biblioteki udostępnionej. Aplikacje można zignorować ostrzeżenie od tej reguły.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano strukturę, która narusza tę regułę. Aby rozwiązać problem w przykładzie, Dodaj publiczną `Add(int x, int y)` metody w strukturze.  
  
 [!code-csharp[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../code-quality/codesnippet/CSharp/ca2225-operator-overloads-have-named-alternates_1.cs)]  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1046: Nie przeciążaj operatora równości w typach referencyjnych](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2226: Operatory powinny mieć symetryczne przeciążenia](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2224: Przesłaniaj metodę Equals w przypadku przeciążania operacji równości operatorów](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2218: Przesłoń metodę GetHashCode przy przesłanianiu metody Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
 [CA2231: Przeciążaj operator równości w przypadku przesłaniania metody ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)