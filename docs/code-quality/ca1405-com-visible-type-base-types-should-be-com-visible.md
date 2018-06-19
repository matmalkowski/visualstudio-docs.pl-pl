---
title: 'CA1405: Typy podstawowe typu widocznego dla modelu COM powinny być widoczne dla modelu COM'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
helpviewer_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1eefb3fdb207ecacca4998168509e8c5b9b1a2f1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31898840"
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405: Typy podstawowe typu widocznego dla modelu COM powinny być widoczne dla modelu COM
|||
|-|-|
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|
|CheckId|CA1405|
|Kategoria|Microsoft.Interoperability|
|Zmiana kluczowa|DependsOnFix|

## <a name="cause"></a>Przyczyna
 Składnik modelu COM (Object) typu widoczne pochodzi z typu, który nie jest widoczne dla modelu COM.

## <a name="rule-description"></a>Opis reguły
 Gdy typem widoczne COM elementy członkowskie są dodawane w nowej wersji, należy przestrzegać strict wytyczne, aby uniknąć dzielenia klientów modelu COM, które wiążą się z wersją. Typ, który jest niewidoczny dla modelu COM zakłada się, że nie ma do wykonania tych reguły kontroli wersji modelu COM. w przypadku dodaje nowe elementy członkowskie. Jednak jeśli widoczne dla modelu COM typu pochodzącego od typu niewidoczne COM i ujawnia interfejsu klasy <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> lub <xref:System.Runtime.InteropServices.ClassInterfaceType> (wartość domyślna) wszystkie publiczne elementy członkowskie typu podstawowego (o ile są specjalnie oznaczone jako COM niewidoczne, który jest zbyteczna) są widoczne dla modelu COM. Jeśli typ podstawowy dodaje nowe elementy członkowskie w kolejnych wersjach, wszelkie klientów modelu COM interfejsu klasy pochodnej typu mogą przestać działać. Typy widoczne dla modelu COM powinny pochodzić tylko od typy widoczne dla modelu COM Aby zmniejszyć prawdopodobieństwo złamanie klientów modelu COM.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, niewidoczna podstawowe typy widoczne dla modelu COM lub typu pochodnego COM.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia typu, który narusza zasady.

 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1405-com-visible-type-base-types-should-be-com-visible_1.vb)]
 [!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/CSharp/ca1405-com-visible-type-base-types-should-be-com-visible_1.cs)]

## <a name="see-also"></a>Zobacz też
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName> [Współdziałanie z kodem niezarządzanym](/dotnet/framework/interop/index)