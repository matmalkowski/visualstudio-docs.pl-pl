---
title: 'CA1008: Wyliczenia powinny mieć wartość zero | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1008
- EnumsShouldHaveZeroValue
helpviewer_keywords:
- CA1008
- EnumsShouldHaveZeroValue
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8c9b64126973f82ede6ca6a9399c70a8a80e9d5f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42685951"
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008: Wyliczenia powinny mieć wartość zero
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA1008: wyliczenia powinny mieć wartość zero](https://docs.microsoft.com/visualstudio/code-quality/ca1008-enums-should-have-zero-value).  
  
Element TypeName | EnumsShouldHaveZeroValue |  
| CheckId | CA1008 |  
| Kategoria | Microsoft.Design|  
| Zmiana powodująca niezgodność | Dzielenie non - po wyświetleniu monitu o dodanie **Brak** wartość wyliczenia bez flagi. Istotne — po wyświetleniu monitu, aby zmienić nazwę lub Usuń wszystkie wartości wyliczenia. |  
  
## <a name="cause"></a>Przyczyna  
 Wyliczenia bez zastosowanych <xref:System.FlagsAttribute?displayProperty=fullName> nie definiuje element członkowski, który ma wartość zero; lub wyliczeniem, który został zastosowany <xref:System.FlagsAttribute> definiuje składową z wartością zero, ale jego nazwa nie jest "None" lub wyliczenie definiuje wiele wartości zero elementy członkowskie.  
  
## <a name="rule-description"></a>Opis reguły  
 Wartość domyślna niezainicjowanego typu wyliczeniowego, podobnie jak inne typy wartości, wynosi zero. Wyliczenie flags−attributed nie powinna definiować element członkowski, który ma wartość zero, więc wartość domyślna jest prawidłową wartością wyliczenia. Jeśli to stosowne, nazwa elementu członkowskiego "None". W przeciwnym razie przypisać zero do najczęściej używanych elementu członkowskiego. Należy pamiętać, że domyślnie, jeśli wartość pierwszego elementu członkowskiego wyliczenia nie jest ustawiona w deklaracji, jego wartość wynosi zero.  
  
 Jeśli wyliczenie, które ma <xref:System.FlagsAttribute> stosowane definiuje składową o wartości zero, powinno być nazwane "Brak", aby wskazać, że żadne wartości nie zostały ustawione w wyliczeniu. Za pomocą elementu członkowskiego o wartości zero dla żadnych innych celów jest sprzeczne z użytkowania <xref:System.FlagsAttribute> , AND i operatory bitowe są bezużyteczne z elementem członkowskim. Oznacza to, że można przypisać tylko jednego członka wartości zero. Należy pamiętać, że jeśli wiele elementów członkowskich, które mają wartość zero, wystąpią w wyliczania opartego na atrybutach flagi, `Enum.ToString()` zwraca niepoprawne wyniki dla elementów członkowskich, które nie mają wartość zero.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej zasady dla wyliczenia bez flags−attributed, należy zdefiniować elementu członkowskiego, który ma wartość zero. jest to zmian niepowodujących niezgodności. W przypadku opartego na atrybutach flagi wyliczeń, które definiują elementu członkowskiego o wartości zero nadaj nazwę tego elementu członkowskiego "None", a następnie usunąć innych elementów członkowskich, które mają wartość zero. jest to istotnej zmiany.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły, z wyjątkiem wyliczenia przypisywane flag, które wcześniej zostały wprowadzone do użytku.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano dwa wyliczenia, które spełniają reguły i wyliczenia `BadTraceOptions`, który narusza regułę.  
  
 [!code-cpp[FxCop.Design.EnumsZeroValue#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/cpp/FxCop.Design.EnumsZeroValue.cpp#1)]
 [!code-csharp[FxCop.Design.EnumsZeroValue#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/cs/FxCop.Design.EnumsZeroValue.cs#1)]
 [!code-vb[FxCop.Design.EnumsZeroValue#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/vb/FxCop.Design.EnumsZeroValue.vb#1)]  
  
## <a name="related-rules"></a>Powiązane reguły  
 [CA2217: Nie oznaczaj wyliczeń za pomocą atrybutu FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
 [CA1700: Nie nadawaj wartościom wyliczenia nazwy „Reserved”](../code-quality/ca1700-do-not-name-enum-values-reserved.md)  
  
 [CA1712: Nie poprzedzaj wartości wyliczenia nazwą typu](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)  
  
 [CA1028: Magazyn typu wyliczeniowego powinien być typu Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)  
  
 [CA1027: Oznacz typy wyliczeniowe atrybutem Flags](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Enum?displayProperty=fullName>



