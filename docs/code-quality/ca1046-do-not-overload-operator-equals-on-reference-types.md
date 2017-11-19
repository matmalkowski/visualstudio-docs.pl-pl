---
title: "CA1046: Nie przeciążaj operatora równości w typach referencyjnych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotOverloadOperatorEqualsOnReferenceTypes
- CA1046
helpviewer_keywords:
- CA1046
- DoNotOverloadOperatorEqualsOnReferenceTypes
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 344dfe7a4e35bf42e9e0a4efb2ca9bdf1b8f5d6b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca1046-do-not-overload-operator-equals-on-reference-types"></a>CA1046: Nie przeciążaj operatora equals w typach referencyjnych
|||  
|-|-|  
|TypeName|DoNotOverloadOperatorEqualsOnReferenceTypes|  
|CheckId|CA1046|  
|Kategoria|Microsoft.Design|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Typ publicznego lub zagnieżdżone odwołanie do publicznego overloads operatora równości.  
  
## <a name="rule-description"></a>Opis reguły  
 Dla typów odwołań domyślna implementacja operatora równości jest prawie zawsze poprawna. Domyślnie dwa odwołania są równe tylko wtedy, gdy wskazują ten sam obiekt.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby rozwiązać naruszenie tej reguły, Usuń implementacji operatora równości.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Jest to bezpieczne Pomiń ostrzeżenie od tej reguły, gdy typ referencyjny zachowuje się jak typ wbudowany wartości. Jeśli jest to przydatne w celu dodawania lub odejmowania na wystąpienie typu, jest prawdopodobnie poprawna wdrożenia operator równości i Pomiń naruszenie.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano domyślne zachowanie podczas porównywania dwóch odwołań.  
  
 [!code-csharp[FxCop.Design.RefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_1.cs)]  
  
## <a name="example"></a>Przykład  
 Następującej aplikacji porównuje niektórych odwołań.  
  
 [!code-csharp[FxCop.Design.TestRefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_2.cs)]  
  
 W tym przykładzie tworzy następujące dane wyjściowe.  
  
 **= Nowy (2,2), b = nowy (2,2) są takie same? Brak**  
**c i są takie same? Tak**  
**b i są ==? Brak**  
**c i czy ==? Tak**   
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1013: Przeciąż operator equals przeciążając operatory add i subtract](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 [Operatory porównania](/dotnet/standard/design-guidelines/equality-operators)