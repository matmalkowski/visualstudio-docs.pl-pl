---
title: "CA2117: Typy APTCA powinny rozszerzać tylko typy bazowe APTCA | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2117
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
helpviewer_keywords:
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
- CA2117
ms.assetid: c505b586-2f1e-47cb-98ee-a5afcbeda70f
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5619de2512e18cbe9d7dbfb3d992886ae23a25bf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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
 Domyślnie typy publiczne lub chronione w zestawy o silnych nazwach niejawnie są chronione przez [Inheritancedemand](http://msdn.microsoft.com/en-us/28b9adbb-8f08-4f10-b856-dbf59eb932d9) dla pełnego zaufania. Zestawy o silnych nazwach oznaczonych <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybutu (APTCA) nie mają tej ochrony. Atrybut wyłącza żądanie dziedziczenia. Dzięki temu narażonych typy zadeklarowane w zestawie dziedziczne według typów, które nie mają pełnego zaufania.  
  
 Gdy atrybut APTCA jest obecny w pełni zaufanych zestawów, a typ w zestawie dziedziczy z typu, który nie zezwala na częściowo zaufane obiekty wywołujące, możliwe jest zabezpieczeń wykorzystać. Jeśli dwa typy `T1` i `T2` spełniać następujące warunki, złośliwe obiekty wywołujące mogą używać typu `T1` obejść żądanie dziedziczenia niejawne pełnego zaufania, który chroni `T2`:  
  
-   `T1`Typ publiczny jest zadeklarowana w pełni zaufany zestawu, który ma atrybut APTCA.  
  
-   `T1`dziedziczy z typu `T2` spoza jej zestawu.  
  
-   `T2`w zestawie nie ma atrybutu APTCA i, w związku z tym nie powinny być dziedziczone przez typów w zestawach częściowo zaufany.  
  
 Częściowo zaufany typu `X` może dziedziczyć `T1`, który udostępnia ona dziedziczonych elementów członkowskich zadeklarowanych w `T2`. Ponieważ `T2` nie ma atrybutu APTCA, jego natychmiastowego pochodny typ (`T1`) muszą spełniać żądanie dziedziczenia dla pełnego zaufania; `T1` ma pełne zaufanie, w związku z tym spełnia to sprawdzenie. To zagrożenie bezpieczeństwa, ponieważ `X` nie uczestniczy w zaspokojenia potrzeb dziedziczenia, która chroni `T2` z niezaufanych podklasy. Z tego powodu typy z atrybutem APTCA nie musi rozszerzać typów, które nie mają atrybutu.  
  
 Inny problem z zabezpieczeniami i prawdopodobnie częściej co oznacza, że typ pochodny (`T1`) mogą za pośrednictwem błąd programisty uwidaczniać chronionych elementów członkowskich z typu, który wymaga pełnego zaufania (`T2`). W takiej sytuacji niezaufanych obiektów wywołujących uzyskują dostęp do informacji, które powinny być dostępne tylko dla typów w pełni zaufany.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Jeśli typ zgłoszone przez naruszenie zestawu, który nie wymaga atrybutu APTCA, usuń go.  
  
 Jeśli wymagana jest atrybutem APTCA, należy dodać do typu żądanie dziedziczenia dla pełnego zaufania. Chroni to przed dziedziczenie przez typy niezaufanych.  
  
 Istnieje możliwość rozwiązać naruszenie, dodając atrybut APTCA do zestawów z typów podstawowych zgłoszone przez naruszenie. Zrobienie tego bez pierwszy przeprowadzanie przeglądu zabezpieczeń znacznym cały kod w zestawach i całego kodu, która jest zależna od zestawy.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Aby bezpiecznie pominąć ostrzeżenie od tej reguły, pamiętaj, że chronione elementy członkowskie udostępnione przez danego typu nie bezpośrednio lub pośrednio Zezwalaj niezaufanym wywołań dostęp do poufnych informacji, operacji lub zasobów, które mogą być używane w szkodliwy sposób.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto dwóch zestawów i aplikacja testowa ilustrujący wykryte przez tę regułę luki w zabezpieczeniach. Pierwszy zestaw nie ma atrybutu APTCA i nie powinny być dziedziczone przez częściowo zaufany typów (reprezentowane przez `T2` w poprzedniej dyskusji).  
  
 [!code-csharp[FxCop.Security.NoAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_1.cs)]  
  
## <a name="example"></a>Przykład  
 Drugi zestaw, reprezentowany przez `T1` w poprzedniej dyskusji jest w pełni zaufany i zezwala na częściowo zaufane obiekty wywołujące.  
  
 [!code-csharp[FxCop.Security.YesAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_2.cs)]  
  
## <a name="example"></a>Przykład  
 Typ testu, reprezentowany przez `X` w poprzedniej dyskusji znajduje się w częściowo zaufanym zestawie.  
  
 [!code-csharp[FxCop.Security.TestAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_3.cs)]  
  
 W tym przykładzie tworzy następujące dane wyjściowe.  
  
 **Spełnianie na shady glen 22/2/2003 12:00:00 AM!**  
**Testu: Słoneczna łąki**  
**Spełnianie na słoneczna łąki 22/2/2003 12:00:00 AM!**   
## <a name="related-rules"></a>Powiązanych reguł  
 [CA2116: Metody APTCA powinny wywoływać tylko metody APTCA](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Wytyczne dotyczące bezpiecznego programowania](/dotnet/standard/security/secure-coding-guidelines)   
 [Zestawów platformy .NET framework można wywołać częściowo zaufany kod](http://msdn.microsoft.com/en-us/a417fcd4-d3ca-4884-a308-3a1a080eac8d)   
 [Używanie bibliotek pochodzących z częściowo zaufanego kodu](/dotnet/framework/misc/using-libraries-from-partially-trusted-code)   
 [Żądań dziedziczenia](http://msdn.microsoft.com/en-us/28b9adbb-8f08-4f10-b856-dbf59eb932d9)