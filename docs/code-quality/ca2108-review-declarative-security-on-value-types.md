---
title: "Ca2108: należy Przeglądnąć zabezpieczenia deklaratywne typów wartościowych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
helpviewer_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
ms.assetid: d62bffdd-3826-4d52-a708-1c646c5d48c2
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a2d7ecd899b4da51e6ff200f1e18b00366db6669
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca2108-review-declarative-security-on-value-types"></a>CA2108: Należy przejrzeć zabezpieczenia deklaratywne typów wartościowych
|||  
|-|-|  
|TypeName|ReviewDeclarativeSecurityOnValueTypes|  
|CheckId|CA2108|  
|Kategoria|Microsoft.Security|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Typ wartości public lub protected jest chroniony przez [dane i modelowanie](/dotnet/framework/data/index) lub [Linkdemand](/dotnet/framework/misc/link-demands).  
  
## <a name="rule-description"></a>Opis reguły  
 Typy wartości są przydzielone i zainicjowane przez ich konstruktory domyślne przed innymi konstruktorów. Jeśli typ wartości jest zabezpieczone żądania Demand lub LinkDemand, a obiekt wywołujący nie ma uprawnienia, które spełniają kontrola zabezpieczeń, wszelkie konstruktora innego niż domyślny zakończy się niepowodzeniem, i zabezpieczeń wyjątek. Typ wartości nie cofnięciu przydziału; zostanie pozostawiony w stanie ustawiona przez jego domyślny konstruktor. Zakłada się, że obiekt wywołujący, która przekazuje wystąpienie typu wartości ma uprawnienia do tworzenia lub dostępu do wystąpienia.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Nie można naprawić naruszenie tej reguły, o ile nie usuniesz kontrola zabezpieczeń z typu i zabezpieczeń na poziomie metody użycia sprawdza się w tym miejscu. Należy pamiętać, że ustalania naruszenie w ten sposób nie zapobiega wywołań z nieodpowiednich uprawnień uzyskanie wystąpienia typu wartości. Należy zapewnić, że wystąpienia typu wartości w stanie domyślnym nie ujawnia poufne informacje i nie można używać w szkodliwy sposób.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Ostrzeżenie od tej reguły można pominąć, jeśli wszystkie wywołujący może uzyskać wystąpienia typu wartości w stanie domyślnym bez stwarza zagrożenie dla bezpieczeństwa.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono biblioteką typu wartości, który narusza tę regułę. Należy pamiętać, że `StructureManager` typu przyjęto założenie, że obiekt wywołujący, która przekazuje wystąpienie typu wartości ma uprawnienia do tworzenia lub dostępu do wystąpienia.  
  
 [!code-csharp[FxCop.Security.DemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_1.cs)]  
  
## <a name="example"></a>Przykład  
 Następującej aplikacji pokazuje osłabienia biblioteki.  
  
 [!code-csharp[FxCop.Security.TestDemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_2.cs)]  
  
 W tym przykładzie tworzy następujące dane wyjściowe.  
  
 **Niestandardowe konstruktora struktury: żądanie nie powiodło się.**  
**Nowe wartości SecuredTypeStructure 100 100**  
**Nowe wartości SecuredTypeStructure 200 200**   
## <a name="see-also"></a>Zobacz też  
 [Żądania łączy](/dotnet/framework/misc/link-demands)   
 [Dane i modelowanie](/dotnet/framework/data/index)