---
title: "CA1903: Używaj tylko API z frameworku docelowego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UseOnlyAPIFromTargetedFramework
- CA1903
helpviewer_keywords:
- UseOnlyApiFromTargetedFramework
- CA1903
ms.assetid: efdb5cc7-bbd8-4fa7-9fff-02b91e59350e
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7caff553adfd812e671a2d8643b2352d9868ca43
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca1903-use-only-api-from-targeted-framework"></a>CA1903: Używaj tylko API z frameworku docelowego
|||  
|-|-|  
|TypeName|UseOnlyApiFromTargetedFramework|  
|CheckId|CA1903|  
|Kategoria|Microsoft.Portability|  
|Zmiana kluczowa|Przerywanie — po względem podpis widoczne na zewnątrz elementu członkowskiego lub typu.<br /><br /> Bez podziału — po w treści metody.|  
  
## <a name="cause"></a>Przyczyna  
 Element członkowski lub typ używa elementu członkowskiego lub typu, który został wprowadzony w dodatku service pack, który nie był dołączony do platformy docelowej projektu.  
  
## <a name="rule-description"></a>Opis reguły  
 Nowe elementy członkowskie i typy zostały uwzględnione w .NET Framework 2.0 z dodatkiem Service Pack 1 i 2, .NET Framework 3.0 z dodatkiem Service Pack 1 i 2 i .NET Framework 3.5 z dodatkiem Service Pack 1. Projektów przeznaczonych główne wersje programu .NET Framework przypadkowo możliwe jest zależne od tych nowych interfejsów API. Aby zapobiec tej zależności, ta zasada wyzwala na użycia nowe elementy członkowskie i typy, które nie zostały uwzględnione domyślnie z platformy docelowej projektu.  
  
 **Platforma docelowa i zależności pakietu usługi**  
  
|||  
|-|-|  
|Gdy jest platformy docelowej|Uruchamiany na użycia elementów członkowskich wprowadzone w systemie|  
|.NET Framework 2.0|.NET framework 2.0 z dodatkiem SP1, .NET Framework 2.0 z dodatkiem SP2|  
|.NET Framework 3.0|.NET framework 2.0 z dodatkiem SP1, .NET Framework 2.0 z dodatkiem SP2, .NET Framework 3.0 z dodatkiem SP1, .NET Framework 3.0 z dodatkiem SP2|  
|Program .NET Framework 3,5|.NET Framework 3.5 SP1|  
|Program .NET Framework 4|Brak|  
  
 Aby zmienić platformę docelową projektu, zobacz [przeznaczonych dla określonej wersji programu .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby usunąć zależności z dodatkiem Service Pack, należy usunąć wszystkie użycia nowego elementu członkowskiego lub typu. Jeśli jest to zamierzone zależności, pominięcia ostrzeżenia lub wyłącz tę regułę.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżenia od tej reguły, jeśli to nie było zamierzone zależności określonego z dodatkiem Service Pack. W takiej sytuacji aplikacja może zakończyć się niepowodzeniem do uruchomienia w systemach bez tego dodatku service pack, zainstalowane. Pomijaj ostrzeżenia lub wyłącz tę regułę, jeśli to było zamierzone zależności.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono klasę, która używa typu DateTimeOffset, która jest dostępna tylko w .NET 2.0 z dodatkiem Service Pack 1. W tym przykładzie wymaga, aby na liście rozwijanej platformy docelowej we właściwościach projektu wybrano .NET Framework 2.0.  
  
 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_1.cs)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład rozwiązuje opisany wcześniej naruszenie przez zamianę użycia typu DateTimeOffset typu Data/Godzina.  
  
 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_2.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Ostrzeżenia przenośności](../code-quality/portability-warnings.md)   
 [Przeznaczonych dla określonej wersji platformy .NET](../ide/targeting-a-specific-dotnet-framework-version.md)