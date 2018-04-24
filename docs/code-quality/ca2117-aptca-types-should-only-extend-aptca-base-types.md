---
title: 'CA2117: Typy APTCA powinny rozszerzać tylko typy bazowe APTCA'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2117
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
helpviewer_keywords:
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
- CA2117
ms.assetid: c505b586-2f1e-47cb-98ee-a5afcbeda70f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5d8b313f0e1c33eb5c17a291995956e62d8c597e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca2117-aptca-types-should-only-extend-aptca-base-types"></a>CA2117: Typy APTCA powinny rozszerzać tylko typy bazowe APTCA

|||
|-|-|
|TypeName|AptcaTypesShouldOnlyExtendAptcaBaseTypes|
|CheckId|CA2117|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Typu publiczne lub chronione na zestaw o <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> atrybutu dziedziczy z typu zadeklarowany w zestawie, do którego nie ma atrybutu.

## <a name="rule-description"></a>Opis reguły

Domyślnie typy publiczne lub chronione w zestawy o silnych nazwach niejawnie są chronione przez [InheritanceDemand](xref:System.Security.Permissions.SecurityAction#System_Security_Permissions_SecurityAction_InheritanceDemand) dla pełnego zaufania. Zestawy o silnych nazwach oznaczonych <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybutu (APTCA) nie mają tej ochrony. Atrybut wyłącza żądanie dziedziczenia. Typy narażonych zadeklarowany w zestawie bez żądanie dziedziczenia są dziedziczone przez typy, które nie mają pełnego zaufania.

Gdy atrybut APTCA jest obecny w pełni zaufanych zestawów, a typ w zestawie dziedziczy z typu, który nie zezwala na częściowo zaufane obiekty wywołujące, możliwe jest zabezpieczeń wykorzystać. Jeśli dwa typy `T1` i `T2` spełniać następujące warunki, złośliwe obiekty wywołujące mogą używać typu `T1` obejść żądanie dziedziczenia niejawne pełnego zaufania, który chroni `T2`:

- `T1` Typ publiczny jest zadeklarowana w pełni zaufany zestawu, który ma atrybut APTCA.

- `T1` dziedziczy z typu `T2` spoza jej zestawu.

- `T2`w zestawie nie ma atrybutu APTCA i, w związku z tym nie powinny być dziedziczone przez typów w zestawach częściowo zaufany.

Częściowo zaufany typu `X` może dziedziczyć `T1`, który udostępnia ona dziedziczonych elementów członkowskich zadeklarowanych w `T2`. Ponieważ `T2` nie ma atrybutu APTCA, jego natychmiastowego pochodny typ (`T1`) muszą spełniać żądanie dziedziczenia dla pełnego zaufania; `T1` ma pełne zaufanie, w związku z tym spełnia to sprawdzenie. To zagrożenie bezpieczeństwa, ponieważ `X` nie uczestniczy w zaspokojenia potrzeb dziedziczenia, która chroni `T2` z niezaufanych podklasy. Z tego powodu typy z atrybutem APTCA nie musi rozszerzać typów, które nie mają atrybutu.

Inny problem z zabezpieczeniami i prawdopodobnie częściej co oznacza, że typ pochodny (`T1`) mogą za pośrednictwem błąd programisty uwidaczniać chronionych elementów członkowskich z typu, który wymaga pełnego zaufania (`T2`). W przypadku wystąpienia tego narażenia niezaufanych obiektów wywołujących dostęp do informacji, które powinny być dostępne tylko dla typów w pełni zaufany.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Jeśli typ zgłoszone przez naruszenie zestawu, który nie wymaga atrybutu APTCA, usuń go.

Jeśli wymagana jest atrybutem APTCA, należy dodać do typu żądanie dziedziczenia dla pełnego zaufania. Żądanie dziedziczenia chroni przed dziedziczenie przez typy niezaufanych.

Istnieje możliwość rozwiązać naruszenie, dodając atrybut APTCA do zestawów z typów podstawowych zgłoszone przez naruszenie. Zrobienie tego bez pierwszy przeprowadzanie przeglądu zabezpieczeń znacznym cały kod w zestawach i całego kodu, która jest zależna od zestawy.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Aby bezpiecznie pominąć ostrzeżenie od tej reguły, pamiętaj, że chronione elementy członkowskie udostępnione przez danego typu nie bezpośrednio lub pośrednio Zezwalaj niezaufanym wywołań dostęp do poufnych informacji, operacji lub zasobów, które mogą być używane w szkodliwy sposób.

## <a name="example"></a>Przykład

W poniższym przykładzie użyto dwóch zestawów i aplikacja testowa ilustrujący wykryte przez tę regułę luki w zabezpieczeniach. Pierwszy zestaw nie ma atrybutu APTCA i nie powinny być dziedziczone przez częściowo zaufany typów (reprezentowane przez `T2` w poprzedniej dyskusji).

[!code-csharp[FxCop.Security.NoAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_1.cs)]

Drugi zestaw, reprezentowany przez `T1` w poprzedniej dyskusji jest w pełni zaufany i zezwala na częściowo zaufane obiekty wywołujące.

[!code-csharp[FxCop.Security.YesAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_2.cs)]

Typ testu, reprezentowany przez `X` w poprzedniej dyskusji znajduje się w częściowo zaufanym zestawie.

[!code-csharp[FxCop.Security.TestAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_3.cs)]

Ten przykład generuje następujące wyniki:

**Spełnianie na shady glen 22/2/2003 12:00:00 AM!**

**Testu: Słoneczna łąki**

**Spełnianie na słoneczna łąki 22/2/2003 12:00:00 AM!**

## <a name="related-rules"></a>Powiązanych reguł

[CA2116: Metody z atrybutem APTCA powinny wywoływać tylko metody z atrybutem APTCA](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)

## <a name="see-also"></a>Zobacz także

- [Wytyczne dotyczące bezpiecznego programowania](/dotnet/standard/security/secure-coding-guidelines)
- [Używanie bibliotek pochodzących z częściowo zaufanego kodu](/dotnet/framework/misc/using-libraries-from-partially-trusted-code)
