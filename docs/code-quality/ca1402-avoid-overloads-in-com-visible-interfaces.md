---
title: "CA1402: Unikaj przeciążeń w interfejsach widocznych dla modelu COM | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
helpviewer_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
ms.assetid: 2724c1f9-d5d3-4704-b124-21c4d398e5df
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fdba95f57b969173cdcbfecbb8c2d8bcbc298d32
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca1402-avoid-overloads-in-com-visible-interfaces"></a>CA1402: Unikaj przeciążeń w interfejsach widocznych dla modelu COM
|||  
|-|-|  
|TypeName|AvoidOverloadsInComVisibleInterfaces|  
|CheckId|CA1402|  
|Kategoria|Microsoft.Interoperability|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Metody przeciążane modelu obiektu składników (COM) deklaruje widoczne interfejsu.  
  
## <a name="rule-description"></a>Opis reguły  
 Gdy przeciążone metody są udostępniane klientom COM, tylko pierwsze przeciążenie metody zachowuje swoją nazwę. Kolejne przeciążenia jednoznacznie są zmieniane przez dodanie nazwy znakiem podkreślenia "_", a liczba całkowita, która odpowiada na polecenie deklaracji przeciążenia. Na przykład wziąć pod uwagę następujące metody.  
  
```  
void SomeMethod(int valueOne);  
void SomeMethod(int valueOne, int valueTwo, int valueThree);  
void SomeMethod(int valueOne, int valueTwo);  
```  
  
 Te metody są widoczne dla klientów modelu COM w następujący sposób.  
  
```  
void SomeMethod(int valueOne);  
void SomeMethod_2(int valueOne, int valueTwo, int valueThree);  
void SomeMethod_3(int valueOne, int valueTwo);  
```  
  
 Klienci Visual Basic 6 COM nie może implementować metody interfejsu za pomocą znaku podkreślenia w nazwie.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, Zmień nazwę przeciążonej metody tak, że nazwy są unikatowe. Alternatywnie niewidoczna interfejs dla modelu COM, zmieniając ułatwień dostępu do `internal` (`Friend` w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) lub przez zastosowanie <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> ustawić atrybutu `false`.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono interfejs, który narusza regułę i interfejs, który spełnia reguły.  
  
 [!code-vb[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/VisualBasic/ca1402-avoid-overloads-in-com-visible-interfaces_1.vb)]
 [!code-csharp[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/CSharp/ca1402-avoid-overloads-in-com-visible-interfaces_1.cs)]  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1413: Unikaj pól niepublicznych w typach wartości widocznych dla modelu COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)  
  
 [CA1407: Unikaj statycznych elementów członkowskich w typach widocznych dla modelu COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)  
  
 [CA1017: Oznacz zestawy atrybutem ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Współdziałanie z kodem niezarządzanym](/dotnet/framework/interop/index)   
 [Long — typ danych](/dotnet/visual-basic/language-reference/data-types/long-data-type)