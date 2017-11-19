---
title: "CA2116: Metody APTCA powinny wywoływać tylko metody APTCA | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
helpviewer_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
ms.assetid: 8b91637e-891f-4dde-857b-bf8012270ec4
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 92c6a91cffc3ce388a3dfb9000b9f432672018f4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca2116-aptca-methods-should-only-call-aptca-methods"></a>CA2116: Metody APTCA powinny wywoływać tylko metody APTCA
|||  
|-|-|  
|TypeName|AptcaMethodsShouldOnlyCallAptcaMethods|  
|CheckId|CA2116|  
|Kategoria|Microsoft.Security|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Metody w zestawie z <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> atrybutu wywołuje metodę w zestawie, który nie ma atrybutu.  
  
## <a name="rule-description"></a>Opis reguły  
 Domyślnie publiczne lub chronione metody w zestawy o silnych nazwach niejawnie są chronione przez [Linkdemand](/dotnet/framework/misc/link-demands) dla pełnego zaufania, tylko w pełni zaufane obiekty wywołujące mogą uzyskiwać dostęp do zestawu z silną nazwą. Zestawy o silnych nazwach oznaczonych <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybutu (APTCA) nie mają tej ochrony. Atrybut wyłącza linkdemand udostępnienie zestawu dla kodu wywołującego, które nie mają pełnego zaufania, takie jak kod wykonywany w intranecie lub Internecie.  
  
 Gdy atrybut APTCA jest obecny w pełni zaufanych zestawów i zestawu wykonuje kod w innym zestawie, który nie zezwala na częściowo zaufane obiekty wywołujące, możliwe jest zabezpieczeń wykorzystać. Jeśli dwie metody `M1` i `M2` spełniać następujące warunki, złośliwe obiekty wywołujące za pomocą metody `M1` obejść linkdemand niejawne pełne zaufanie, chroniącego `M2`:  
  
-   `M1`Metoda publiczna jest zadeklarowany w pełni zaufany zestawu, który ma atrybut APTCA.  
  
-   `M1`wywołuje metodę `M2` poza `M1`w zestawie.  
  
-   `M2`w zestawie nie ma atrybutu APTCA i, w związku z tym nie powinien być wykonywany przez lub w imieniu wywołań, które są częściowo zaufany.  
  
 Obiekt wywołujący częściowo zaufany `X` można wywołać metody `M1`, powodując `M1` do wywołania `M2`. Ponieważ `M2` nie ma atrybutu APTCA, jego bezpośredniego obiektu wywołującego (`M1`) muszą spełniać żądanie łącza do pełnego zaufania; `M1` ma pełne zaufanie, w związku z tym spełnia to sprawdzenie. To zagrożenie bezpieczeństwa, ponieważ `X` nie uczestniczy w zaspokojenia potrzeb link, który chroni `M2` z niezaufanych obiekty wywołujące. W związku z tym metody z atrybutem APTCA nie mogą wywoływać metod, które nie mają atrybutu.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Jeśli atrybut APCTA jest wymagana, należy użyć żądanie do ochrony metodę, która wywołuje całkowicie zaufany zestaw. Dokładne uprawnienia, możesz żądanie będzie zależeć od funkcji udostępnianych przez metodę. Jeśli to możliwe, należy chronić metody zażąda pełnego zaufania upewnić się, że podstawową funkcjonalność nie jest narażony na częściowo zaufane obiekty wywołujące. Jeśli nie jest to możliwe, wybierz zestaw uprawnień skutecznie chroni narażonych funkcji. Aby uzyskać więcej informacji na temat wymagań, zobacz [wymagań](http://msdn.microsoft.com/en-us/e5283e28-2366-4519-b27d-ef5c1ddc1f48).  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Aby bezpiecznie pominąć ostrzeżenie od tej reguły, musi upewnij się, że funkcje udostępniane przez metodę nie bezpośrednio lub pośrednio zezwala elementom wywołującym na dostęp do poufnych informacji, operacji lub zasobów, które mogą być używane w szkodliwy sposób.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto dwóch zestawów i aplikacja testowa ilustrujący wykryte przez tę regułę luki w zabezpieczeniach. Pierwszy zestaw nie ma atrybutu APTCA i nie powinny być dostępne dla częściowo zaufanego kodu wywołującego (reprezentowane przez `M2` w poprzedniej dyskusji).  
  
 [!code-csharp[FxCop.Security.NoAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_1.cs)]  
  
## <a name="example"></a>Przykład  
 Drugi zestaw jest w pełni zaufany i zezwala na częściowo zaufanych wywołań (reprezentowane przez `M1` w poprzedniej dyskusji).  
  
 [!code-csharp[FxCop.Security.YesAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_2.cs)]  
  
## <a name="example"></a>Przykład  
 Aplikacja testowa (reprezentowane przez `X` w poprzedniej dyskusji) jest częściowo zaufany.  
  
 [!code-csharp[FxCop.Security.TestAptcaMethods#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_3.cs)]  
  
 W tym przykładzie tworzy następujące dane wyjściowe.  
  
 **Żądanie dla pełnego zaufania: żądanie nie powiodło się.**  
**ClassRequiringFullTrust.DoWork została wywołana.**   
## <a name="related-rules"></a>Powiązanych reguł  
 [CA2117: Typy APTCA powinny rozszerzać tylko typy bazowe APTCA](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Wytyczne dotyczące bezpiecznego programowania](/dotnet/standard/security/secure-coding-guidelines)   
 [Zestawów platformy .NET framework można wywołać częściowo zaufany kod](http://msdn.microsoft.com/en-us/a417fcd4-d3ca-4884-a308-3a1a080eac8d)   
 [Używanie bibliotek pochodzących z częściowo zaufanego kodu](/dotnet/framework/misc/using-libraries-from-partially-trusted-code)   
 [Wymagania](http://msdn.microsoft.com/en-us/e5283e28-2366-4519-b27d-ef5c1ddc1f48)   
 [Żądania łączy](/dotnet/framework/misc/link-demands)   
 [Dane i modelowanie](/dotnet/framework/data/index)