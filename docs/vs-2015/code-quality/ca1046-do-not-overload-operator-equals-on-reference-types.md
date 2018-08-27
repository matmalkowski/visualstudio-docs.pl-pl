---
title: 'CA1046: Nie przeciążaj operatora równości w typach referencyjnych | Dokumentacja firmy Microsoft'
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
- DoNotOverloadOperatorEqualsOnReferenceTypes
- CA1046
helpviewer_keywords:
- CA1046
- DoNotOverloadOperatorEqualsOnReferenceTypes
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1f4f37f6d4c2662ca0b053e6737c57ba222b0b5e
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2018
ms.locfileid: "42900955"
---
# <a name="ca1046-do-not-overload-operator-equals-on-reference-types"></a>CA1046: Nie przeciążaj operatora equals w typach referencyjnych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA1046: nie przeciążaj operatora równości w typach referencyjnych](https://docs.microsoft.com/visualstudio/code-quality/ca1046-do-not-overload-operator-equals-on-reference-types).

|||
|-|-|
|TypeName|DoNotOverloadOperatorEqualsOnReferenceTypes|
|CheckId|CA1046|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Odwołanie do publicznego lub publiczny zagnieżdżony typ przeciążenia operatora równości.

## <a name="rule-description"></a>Opis reguły
 Dla typów odwołań domyślna implementacja operatora równości jest prawie zawsze poprawna. Domyślnie dwa odwołania są równe tylko wtedy, gdy wskazują ten sam obiekt.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, Usuń implementacja operatora równości.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, gdy typ odwołania, który zachowuje się jak określonym wbudowanym typie wartości. Jeśli jest to istotne w celu dodawania lub odejmowania na wystąpienia typu, jest prawdopodobnie poprawna, implementuje operatora równości i pominąć naruszenia.

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano domyślne zachowanie podczas porównywania dwóch odwołań.

 [!code-csharp[FxCop.Design.RefTypesNoEqualityOp#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RefTypesNoEqualityOp/cs/FxCop.Design.RefTypesNoEqualityOp.cs#1)]

## <a name="example"></a>Przykład
 Następująca aplikacja porównuje niektórych odwołań.

 [!code-csharp[FxCop.Design.TestRefTypesNoEqualityOp#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestRefTypesNoEqualityOp/cs/FxCop.Design.TestRefTypesNoEqualityOp.cs#1)]

 Ten przykład generuje następujące dane wyjściowe.

 **= Nowy (2,2) i b = nowy (2,2) są takie same? Nie**
**c i są równe? Tak**
**b i są ==? Nie**
**c i czy ==? Tak**
## <a name="related-rules"></a>Powiązane reguły
 [CA1013: Dokonaj przeciążenia operatora równości przy przeciążaniu operatorów dodawania i odejmowania](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)

## <a name="see-also"></a>Zobacz też
 <xref:System.Object.Equals%2A?displayProperty=fullName> [Operatory równości](http://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)



