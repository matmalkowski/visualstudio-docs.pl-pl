---
title: 'CA1403: Typy automatycznego układu nie powinny być widoczne dla modelu COM'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AutoLayoutTypesShouldNotBeComVisible
- CA1403
helpviewer_keywords:
- CA1403
- AutoLayoutTypesShouldNotBeComVisible
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: d84fdd4f352a823614832cc8d5d1b9e57c7a9dfb
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37058077"
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403: Typy automatycznego układu nie powinny być widoczne dla modelu COM

|||
|-|-|
|TypeName|AutoLayoutTypesShouldNotBeComVisible|
|CheckId|CA1403|
|Kategoria|Microsoft.Interoperability|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Typ wartości widocznych składnika modelu COM (Object) jest oznaczony atrybutem <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> ustawić atrybutu <xref:System.Runtime.InteropServices.LayoutKind.Auto?displayProperty=fullName>.

## <a name="rule-description"></a>Opis reguły

<xref:System.Runtime.InteropServices.LayoutKind> Układ typy są zarządzane przez środowisko uruchomieniowe języka wspólnego. Układ te typy, można zmienić między wersjami programu .NET Framework, która dzieli klientów modelu COM, w których jest oczekiwany określony układ. Jeśli <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybut nie jest określony, określ Kompilatory języka C#, Visual Basic i C++ [LayoutKind.Auto](<xref:System.Runtime.InteropServices.LayoutKind.Auto>) dla typów wartości.

O ile nie jest oznaczony jako inaczej, wszystkie typy publiczne, nieogólną są widoczne dla modelu COM, a wszystkie typy niepublicznych i rodzajowy nie są widoczne dla modelu COM. Aby ograniczyć liczbę fałszywych alarmów, ta zasada wymaga widoczność modelu COM typu, który ma być jasno określone. Muszą być oznaczone zestawu zawierającego <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> ustawioną `false` i typ musi być oznaczone <xref:System.Runtime.InteropServices.ComVisibleAttribute> ustawioną `true`.

## <a name="how-to-fix-violations"></a>Jak rozwiązać naruszeń

Aby naprawić naruszenie tej reguły, zmień wartość <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybutu [LayoutKind.Explicit](<xref:System.Runtime.InteropServices.LayoutKind.Explicit>) lub [LayoutKind.Sequential](<xref:System.Runtime.InteropServices.LayoutKind.Sequential>), lub ukrywanie typu do modelu COM.

## <a name="when-to-suppress-warnings"></a>Kiedy pomijanie ostrzeżeń

Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono typu, który narusza regułę i typ, który spełnia reguły.

[!code-csharp[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/CSharp/ca1403-auto-layout-types-should-not-be-com-visible_1.cs)]
[!code-vb[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/VisualBasic/ca1403-auto-layout-types-should-not-be-com-visible_1.vb)]

## <a name="related-rules"></a>Powiązanych reguł

[CA1408: Nie używaj wartości ClassInterfaceType dla elementu AutoDual](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Zobacz także

- [Określ kwalifikator typów .NET do międzyoperacyjności](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Współdziałanie z kodem niezarządzanym](/dotnet/framework/interop/index)