---
title: '&lt;customHostSpecified&gt; elementu (Office development w Visual Studio)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <customHostSpecified> element
- <customHostSpecified> element
- customHostSpecified element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d4eaf874a259251c35a6b01c08f544993092ff4d
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34264038"
---
# <a name="ltcustomhostspecifiedgt-element-office-development-in-visual-studio"></a>&lt;customHostSpecified&gt; elementu (Office development w Visual Studio)
  `customHostSpecified` Element wskazuje, że to rozwiązanie nie jest aplikacją samodzielną. Rozwiązania Office zawiera składniki, które są obsługiwane w aplikacjach firmy Microsoft Office.  
  
## <a name="syntax"></a>Składnia  
  
```xml
<customHostSpecified />  
```  
  
## <a name="elements-and-attributes"></a>Elementy i atrybuty  
 `customHostSpecified` Element jest wymagany dla rozwiązań pakietu Office. Tego elementu jest `co.v1` przestrzeni nazw i określa, czy to wdrożenie zawiera składnik, który będzie wdrażany w ramach hosta niestandardowego, a nie jest autonomiczną aplikacją.  
  
 Ten element jest elementem podrzędnym pierwszego `<entrypoint>` elementu w manifeście aplikacji. Nie mogą istnieć żadne inne elementy podrzędne tego `<entrypoint>` element lub [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] zgłosi błąd sprawdzania poprawności podczas instalacji.  
  
 Ten element ma żadnych atrybutów i elementów podrzędnych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje `customHostSpecified` elementu w manifeście aplikacji dla rozwiązań pakietu Office. Ten przykładowy kod jest częścią większego przykładu udostępnionego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).  
  
```xml
<entryPoint>  
    <co.v1:customHostSpecified />  
</entryPoint>  
```  
  
## <a name="see-also"></a>Zobacz także  
 [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  