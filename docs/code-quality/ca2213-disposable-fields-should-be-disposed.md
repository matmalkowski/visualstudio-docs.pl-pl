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
ms.openlocfilehash: 143a094375871bf8073999f89d7fac5d6df01b4f
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551863"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: Pola usuwalne powinny zostać usunięte

|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Typ, który implementuje <xref:System.IDisposable?displayProperty=fullName> deklaruje pola, które są typami, które implementują także <xref:System.IDisposable>. <xref:System.IDisposable.Dispose%2A> Metody pól nie jest wywoływany przez <xref:System.IDisposable.Dispose%2A> metody typu deklarującego.

## <a name="rule-description"></a>Opis reguły
 Typ jest odpowiedzialny za usuwanie wszystkich jej zasobów niezarządzanych; jest to realizowane poprzez implementację <xref:System.IDisposable>. Ta reguła sprawdza, czy typu usuwalnego `T` deklaruje pole `F` oznacza to wystąpienie typu usuwalnego `FT`. Dla każdego pola `F`, reguła próbuje zlokalizować wywołanie `FT.Dispose`. Reguła wyszukuje metody wywoływane przez `T.Dispose`, a jeden poziom w dół (metody wywoływane przez metody wywołane `FT.Dispose`).

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy wywołać <xref:System.IDisposable.Dispose%2A> w polach, które są typami, które implementują <xref:System.IDisposable> Jeżeli jesteś odpowiedzialny za przydzielanie i zwalniania niezarządzanych zasobów przechowywanych przez pole.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Bezpiecznie Pomijaj ostrzeżeń dla tej reguły, jeśli nie jesteś odpowiedzialny dla przy zwalnianiu zasobów przechowywanych przez pole lub jeśli wywołanie <xref:System.IDisposable.Dispose%2A> występuje dokładniejsze wywoływania niż sprawdzanie reguły.

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano typu `TypeA` implementującej <xref:System.IDisposable> (`FT` w dyskusji previosu).

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano typu `TypeB` który narusza tę regułę przez zadeklarowanie pola `aFieldOfADisposableType` (`F` w poprzednim dyskusji) jako możliwe do rozporządzania typ (`TypeA`) i nie wywołuje metody <xref:System.IDisposable.Dispose%2A> pola. `TypeB` odnosi się do `T` w poprzednim dyskusji.

 [!code-csharp[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_2.cs)]

## <a name="see-also"></a>Zobacz także

- <xref:System.IDisposable?displayProperty=fullName>
- [Wzorzec Dispose](/dotnet/standard/design-guidelines/dispose-pattern)