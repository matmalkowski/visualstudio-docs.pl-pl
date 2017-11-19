---
title: "CA2122: Nie ujawniaj pośrednio metod żądaniami linkdemand | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2122
- DoNotIndirectlyExposeMethodsWithLinkDemands
helpviewer_keywords:
- DoNotIndirectlyExposeMethodsWithLinkDemands
- CA2122
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 00222c71e537856d420c6472efb104a8c928237e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122: Nie należy pośrednio ujawniać metod w żądaniach konsolidacji
|||  
|-|-|  
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|  
|CheckId|CA2122|  
|Kategoria|Microsoft.Security|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Publiczne lub chronione element członkowski ma [Linkdemand](/dotnet/framework/misc/link-demands) i jest wywoływana przez element członkowski, który nie sprawdza zabezpieczeń.  
  
## <a name="rule-description"></a>Opis reguły  
 Zapotrzebowanie na łącza sprawdza uprawnienia tylko bezpośredniego wywołującego. Jeśli element członkowski `X` sprawia, że nie żądania kontroli zabezpieczeń wywołań i wywołań kodu chroniony przez żądanie łącza obiekt wywołujący bez niezbędnych uprawnień, można użyć `X` uzyskać dostępu do chronionego członka.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Dodawanie zabezpieczeń [dane i modelowanie](/dotnet/framework/data/index) lub łącze żądanie do elementu członkowskiego, dzięki czemu nie jest już zapewnia niezabezpieczona dostęp do elementu członkowskiego chronionego żądanie łącza.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Aby bezpiecznie pominąć ostrzeżenie od tej reguły, powinien upewnić się, że kod nie przyznaje elementy wywołujące pod dostęp do operacji lub zasobów, które mogą być używane w szkodliwy sposób.  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach pokazano biblioteki, która narusza regułę, a aplikacja, która przedstawia osłabienia biblioteki. Biblioteka próbki udostępnia dwie metody, naruszających zasady. `EnvironmentSetting` Metody jest chroniony przez żądanie łącza, aby uzyskać nieograniczony dostęp do zmiennych środowiskowych. `DomainInformation` Metoda pozwala nie wymagania zabezpieczeń elementy wywołujące pod przed wywołaniem `EnvironmentSetting`.  
  
 [!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_1.cs)]  
  
## <a name="example"></a>Przykład  
 Następującej aplikacji wywołuje element członkowski niezabezpieczona biblioteki.  
  
 [!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_2.cs)]  
  
 W tym przykładzie tworzy następujące dane wyjściowe.  
  
 **Wartość z zakresu od niezabezpieczonego elementu członkowskiego: seattle.corp.contoso.com**   
## <a name="see-also"></a>Zobacz też  
 [Wytyczne dotyczące bezpiecznego programowania](/dotnet/standard/security/secure-coding-guidelines)   
 [Żądania łączy](/dotnet/framework/misc/link-demands)   
 [Dane i modelowanie](/dotnet/framework/data/index)