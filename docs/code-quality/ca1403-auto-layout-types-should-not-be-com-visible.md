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
ms.workload:
- multiple
ms.openlocfilehash: 056b1d254b8544f9a1f0abe364bcb40f15235e64
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403: Typy automatycznego układu nie powinny być widoczne dla modelu COM
|||
|-|-|
|TypeName|AutoLayoutTypesShouldNotBeComVisible|
|CheckId|CA1403|
|Kategoria|Microsoft.Interoperability|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ wartości widocznych składnika modelu COM (Object) jest oznaczony atrybutem <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> ustawić atrybutu <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName>.

## <a name="rule-description"></a>Opis reguły
 <xref:System.Runtime.InteropServices.LayoutKind> Układ typy są zarządzane przez środowisko uruchomieniowe języka wspólnego. Układ te typy, można zmienić między wersjami programu .NET Framework, która spowoduje zerwanie klientów modelu COM, w których jest oczekiwany określony układ. Należy pamiętać, że jeśli <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybut nie jest określony, C#, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], i określ kompilatory C++ <xref:System.Runtime.InteropServices.LayoutKind> układu dla typów wartości.

 O ile nie jest oznaczony jako inaczej, wszystkie typy nierodzajowe publiczne są widoczne dla modelu COM; wszystkie typy niepubliczne i rodzajowy nie są widoczne dla modelu COM. Aby ograniczyć liczbę fałszywych alarmów, ta zasada wymaga jednak widoczność modelu COM typu, który ma być jawnie podanym; muszą być oznaczone zestawu zawierającego <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> ustawioną `false` i typ musi być oznaczone <xref:System.Runtime.InteropServices.ComVisibleAttribute> ustawioną `true`.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, zmień wartość <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybutu <xref:System.Runtime.InteropServices.LayoutKind> lub <xref:System.Runtime.InteropServices.LayoutKind>, lub ukrywanie typu do modelu COM.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono typu, który narusza regułę i typ, który spełnia reguły.

 [!code-csharp[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/CSharp/ca1403-auto-layout-types-should-not-be-com-visible_1.cs)]
 [!code-vb[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/VisualBasic/ca1403-auto-layout-types-should-not-be-com-visible_1.vb)]

## <a name="related-rules"></a>Powiązanych reguł
 [CA1408: Nie używaj wartości ClassInterfaceType dla elementu AutoDual](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Zobacz też
 [Kwalifikowanie typów .NET do międzyoperacyjności](/dotnet/framework/interop/qualifying-net-types-for-interoperation) [współpracy z niezarządzany kod](/dotnet/framework/interop/index)