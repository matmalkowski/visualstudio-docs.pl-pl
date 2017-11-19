---
title: "CA1008: Wyliczenia powinny mieć wartości zerowej | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1008
- EnumsShouldHaveZeroValue
helpviewer_keywords:
- CA1008
- EnumsShouldHaveZeroValue
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 84c43a95cd607a13a302e2247cacb091a39a3070
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008: Wyliczenia powinny mieć wartość zero
|||  
|-|-|  
|TypeName|EnumsShouldHaveZeroValue|  
|CheckId|CA1008|  
|Kategoria|Microsoft.Design|  
|Zmiana kluczowa|Dzielenie non - po wyświetleniu monitu o dodanie **Brak** wartości wyliczenia bez flagi. Przerywanie — po wyświetleniu monitu, aby zmienić nazwę lub Usuń wszystkie wartości wyliczenia.|  
  
## <a name="cause"></a>Przyczyna  
 Wyliczenia bez zastosowanych <xref:System.FlagsAttribute?displayProperty=fullName> nie zawiera definicji elementu członkowskiego, który ma wartość zero; lub ma zastosowane wyliczenie <xref:System.FlagsAttribute> definiuje element członkowski z wartością zero, ale jego nazwa nie jest "None" lub wyliczenia definiuje wiele wartości zero elementy członkowskie.  
  
## <a name="rule-description"></a>Opis reguły  
 Wartość domyślna niezainicjowanej wyliczenia, podobnie jak inne typy wartości to zero. Wyliczenie atrybut flagi należy zdefiniować elementu członkowskiego, który ma wartość zero, wartością domyślną jest prawidłową wartością wyliczenia. W razie potrzeby, nazwa elementu członkowskiego "Brak". W przeciwnym razie przypisać zero do najczęściej używanych elementów członkowskich. Należy pamiętać, że domyślnie, jeśli nie ustawiono wartość pierwszego elementu członkowskiego wyliczenia w deklaracji, jego wartość wynosi zero.  
  
 Jeśli wyliczenie ma <xref:System.FlagsAttribute> stosowane definiuje element członkowski o wartości zero, jego nazwa powinna być "None", aby wskazać, że w wyliczeniu nie ustawiono żadnych wartości. Przy użyciu elementu członkowskiego wartości zero dla innych celów jest sprzecznie stosowania <xref:System.FlagsAttribute> , AND i operatory bitowe są bezużyteczne z elementem członkowskim. Oznacza to, że tylko jeden element członkowski należy przypisać wartość zero. Należy pamiętać, że jeśli wiele elementów członkowskich, które mają wartość zero, wystąpią w przypisanych flagi wyliczenia, `Enum.ToString()` zwraca niepoprawne wyniki dla elementów członkowskich, które nie są zero.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby rozwiązać naruszenie tej reguły dla wyliczenia atrybut flagi, zdefiniować elementu członkowskiego, który ma wartość zero; jest to zmiana nierozdzielające. Dla przypisanych flagi wyliczenia definiujące element członkowski o wartości zero nazwa tego elementu członkowskiego "Brak" i Usuń o innych elementach członkowskich, które mają wartość zero; jest to istotne zmiany.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżenia od tej reguły, z wyjątkiem atrybut flagi wyliczenia, które wcześniej zostały dostarczone.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia dwa wyliczenia, które spełniają reguły i wyliczenia `BadTraceOptions`, który narusza zasady.  
  
 [!code-cpp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CPP/ca1008-enums-should-have-zero-value_1.cpp)]
 [!code-csharp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CSharp/ca1008-enums-should-have-zero-value_1.cs)]
 [!code-vb[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/VisualBasic/ca1008-enums-should-have-zero-value_1.vb)]  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA2217: Nie oznaczaj typów wyliczeniowych atrybutem FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
 [CA1700: Nie nadawać wartościom enum oznaczenia "Reserved"](../code-quality/ca1700-do-not-name-enum-values-reserved.md)  
  
 [CA1712: Nie dodawaj prefiksu wartości enum nazwą typu](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)  
  
 [CA1028: Pamięć wyliczenia powinna być Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)  
  
 [CA1027: Oznaczaj wyliczenia za pomocą FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Enum?displayProperty=fullName>