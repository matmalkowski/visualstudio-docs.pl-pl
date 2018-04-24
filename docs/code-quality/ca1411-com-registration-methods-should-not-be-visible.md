---
title: 'CA1411: Metody rejestracji modelu COM nie powinny być widoczne'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1411
- ComRegistrationMethodsShouldNotBeVisible
helpviewer_keywords:
- ComRegistrationMethodsShouldNotBeVisible
- CA1411
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1fbb8a3f9dd442e26ee18abd345d92be3f650c67
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca1411-com-registration-methods-should-not-be-visible"></a>CA1411: Metody rejestracji modelu COM nie powinny być widoczne
|||
|-|-|
|TypeName|ComRegistrationMethodsShouldNotBeVisible|
|CheckId|CA1411|
|Kategoria|Microsoft.Interoperability|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metody, która jest oznaczony atrybutem <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> lub <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> atrybutu jest widoczna zewnętrznie.

## <a name="rule-description"></a>Opis reguły
 Po zarejestrowaniu zestawu z składnik modelu COM. wpisy są dodawane do rejestru dla każdego typu widoczny dla modelu COM w zestawie. Metody, które są oznaczone ikoną z <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> i <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> atrybuty wywoływane podczas procesu rejestrowania i wyrejestrowania odpowiednio do uruchomienia kodu użytkownika, specyficzne dla rejestracji/wyrejestrowanie tych typów. Ten kod nie powinna być wywoływana poza tych procesów.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, zmień dostępność metody `private` lub `internal` (`Friend` w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono dwie metody, które naruszają zasady.

 [!code-csharp[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/CSharp/ca1411-com-registration-methods-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/VisualBasic/ca1411-com-registration-methods-should-not-be-visible_1.vb)]

## <a name="related-rules"></a>Powiązanych reguł
 [CA1410: Metody rejestracji modelu COM powinny być dopasowane](../code-quality/ca1410-com-registration-methods-should-be-matched.md)

## <a name="see-also"></a>Zobacz też
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName> [Rejestrowanie zestawów w modelu COM](/dotnet/framework/interop/registering-assemblies-with-com) [Regasm.exe (narzędzie rejestracji zestawów)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)