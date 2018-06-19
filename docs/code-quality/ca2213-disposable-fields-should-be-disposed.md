---
title: 'CA2213: Pola usuwalne powinny zostać usunięte'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DisposableFieldsShouldBeDisposed
- CA2213
helpviewer_keywords:
- CA2213
- DisposableFieldsShouldBeDisposed
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: be4efbd197a8146789b9646f6b5c467cc42815b1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31920488"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: Pola usuwalne powinny zostać usunięte
|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Typ, który implementuje <xref:System.IDisposable?displayProperty=fullName> deklaruje pola, które są typów, które również implementują <xref:System.IDisposable>. <xref:System.IDisposable.Dispose%2A> Metody pola nie jest wywoływany przez <xref:System.IDisposable.Dispose%2A> metody typ deklarujący.

## <a name="rule-description"></a>Opis reguły
 Typ jest odpowiedzialny za usuwanie wszystkich jej zasobów niezarządzanych; jest to osiągane przez wdrożenie <xref:System.IDisposable>. Ta reguła sprawdza, czy typ jednorazowe `T` deklaruje on pole `F` czyli wystąpienia typu jednorazowe `FT`. Dla każdego pola `F`, reguła próbuje zlokalizować wywołania `FT.Dispose`. Reguły będzie przeszukiwana metody wywoływane przez `T.Dispose`, a jeden poziom w dół (metody wywoływane przez metody wywołane `FT.Dispose`).

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby rozwiązać naruszenie tej reguły, należy wywołać <xref:System.IDisposable.Dispose%2A> w polach, które są typów implementujących <xref:System.IDisposable> Jeśli jest odpowiedzialny za przydzielanie i zwalniania niezarządzanych zasobów posiadanych przez pole.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Można bezpiecznie pominąć ostrzeżenie od tej reguły, jeśli nie jesteś odpowiedzialny do zwolnienia zasobu posiadanych przez pole lub wywołanie <xref:System.IDisposable.Dispose%2A> występuje na poziomie wywoływania głębiej niż sprawdza reguły.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono typu `TypeA` implementującej <xref:System.IDisposable> (`FT` w dyskusji previosu).

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono typu `TypeB` co narusza tę regułę przez zadeklarowanie pola `aFieldOfADisposableType` (`F` w poprzedniej dyskusji) jako możliwe do rozporządzania typ (`TypeA`) i nie wywołuje metody <xref:System.IDisposable.Dispose%2A> w tym polu. `TypeB` odpowiada `T` w poprzedniej dyskusji.

 [!code-csharp[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_2.cs)]

## <a name="see-also"></a>Zobacz też
 <xref:System.IDisposable?displayProperty=fullName> [Wzorzec Dispose](/dotnet/standard/design-guidelines/dispose-pattern)