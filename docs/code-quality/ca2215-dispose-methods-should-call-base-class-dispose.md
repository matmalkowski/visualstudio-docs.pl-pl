---
title: 'CA2215: Metody Dispose powinny wywoływać operację usuwania klasy bazowej'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2215
- DisposeMethodsShouldCallBaseClassDispose
- Dispose methods should call base class dispose
helpviewer_keywords:
- DisposeMethodsShouldCallBaseClassDispose
- CA2215
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0ce7e5de528e8b0c0a6f128fa9f7d68c1b9f385c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31919807"
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215: Metody Dispose powinny wywoływać operację usuwania klasy bazowej
|||
|-|-|
|TypeName|DisposeMethodsShouldCallBaseClassDispose|
|CheckId|CA2215|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Typ, który implementuje <xref:System.IDisposable?displayProperty=fullName> dziedziczy po typie, który też implementuje <xref:System.IDisposable>. <xref:System.IDisposable.Dispose%2A> Nie wywołuje metody typu dziedziczących <xref:System.IDisposable.Dispose%2A> metody typu nadrzędnego.

## <a name="rule-description"></a>Opis reguły
 Jeśli typ dziedziczy z typu możliwego do likwidacji, musi wywoływać <xref:System.IDisposable.Dispose%2A> metody typu podstawowego z wewnątrz własnego <xref:System.IDisposable.Dispose%2A> metody. Wywołanie metody typu podstawowego Dispose zapewnia zwolnienie wszystkich zasobów tworzone przez typ podstawowy.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby rozwiązać naruszenie tej reguły, należy wywołać `base`.<xref:System.IDisposable.Dispose%2A> w Twojej <xref:System.IDisposable.Dispose%2A> metody.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Można bezpiecznie pominąć ostrzeżenie od tej reguły, jeśli wywołanie `base`.<xref:System.IDisposable.Dispose%2A> występuje na poziomie wywoływania głębiej niż sprawdza reguły.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono typu `TypeA` implementującej <xref:System.IDisposable>.

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2215-dispose-methods-should-call-base-class-dispose_1.cs)]

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono typu `TypeB` który dziedziczy z typu `TypeA` i prawidłowo wywołuje jego <xref:System.IDisposable.Dispose%2A> metody.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2215-dispose-methods-should-call-base-class-dispose_2.vb)]

## <a name="see-also"></a>Zobacz też
 <xref:System.IDisposable?displayProperty=fullName> [Wzorzec Dispose](/dotnet/standard/design-guidelines/dispose-pattern)