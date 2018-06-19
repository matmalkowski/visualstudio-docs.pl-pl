---
title: 'CA1816: Wywołaj poprawnie GC.SuppressFinalize'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1816
- DisposeMethodsShouldCallSuppressFinalize
helpviewer_keywords:
- DisposeMethodsShouldCallSuppressFinalize
- CA1816
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e3c3b7a7dd5e7c9ed8e5b713578dd682384dbf30
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31916119"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816: Wywołaj poprawnie GC.SuppressFinalize
|||
|-|-|
|TypeName|CallGCSuppressFinalizeCorrectly|
|CheckId|CA1816|
|Kategoria|Firmy Microsoft. Użycie|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

-   Metody, która jest implementacją <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> nie wywołuje <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

-   Metody, która nie jest implementacją <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> wywołania <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

-   Wywołuje metodę <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> i przekazuje inną niż ta (Me w języku Visual Basic).

## <a name="rule-description"></a>Opis reguły
 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> Metody umożliwia użytkownikom zwolnić zasoby w dowolnym momencie przed obiektu stać się dostępne dla wyrzucanie elementów bezużytecznych. Jeśli <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> metoda jest wywoływana, on zwalniają zasoby obiektu. Dzięki temu finalizacji niepotrzebne. <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> powinny wywoływać <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> , moduł zbierający elementy bezużyteczne nie wywołuje finalizatora obiektu.

 Aby zapobiec konieczności ponownego zaimplementowania typów pochodnych z finalizatory <xref:System.IDisposable> i wywołać go, niezapieczętowane typy bez finalizatory powinny wywoływać nadal <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły:

 Jeśli metoda jest implementacją <xref:System.IDisposable.Dispose%2A>, dodaj wywołanie do <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

 Jeśli metoda nie jest implementacją <xref:System.IDisposable.Dispose%2A>, albo Usuń wywołanie <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> lub przenieś go na typ <xref:System.IDisposable.Dispose%2A> implementacji.

 Zmień wszystkie wywołania <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> do przekazania tej (Me w języku Visual Basic).

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Tylko pominąć ostrzeżenie od tej reguły, jeśli są deliberating przy użyciu <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> do kontrolowania okres istnienia innych obiektów. Nie pomijaj ostrzeżenia od tej reguły, jeśli implementacja <xref:System.IDisposable.Dispose%2A> nie wywołuje <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>. W takiej sytuacji można wstrzymać finalizację powoduje spadek wydajności oraz nie korzyści.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono metodę to niepoprawnie wywołania <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_1.vb)]
 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_1.cs)]

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono metodę to poprawnie wywołania <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_2.vb)]
 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_2.cs)]

## <a name="related-rules"></a>Powiązanych reguł
 [CA2215: Metody Dispose powinny wywoływać metodę Dispose klasy podstawowej](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA2216: Typy możliwe do likwidacji powinny deklarować finalizator](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>Zobacz też
 [Wzorzec Dispose](/dotnet/standard/design-guidelines/dispose-pattern)