---
title: '&lt;customHostSpecified&gt; elementu (Office Development w Visual Studio) | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <customHostSpecified> element
- <customHostSpecified> element
- customHostSpecified element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 80007310f5556bcc8c67b61e7ff41953cc7c900e
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="ltcustomhostspecifiedgt-element-office-development-in-visual-studio"></a>&lt;customHostSpecified&gt; elementu (Office Development w Visual Studio)
  `customHostSpecified` Element wskazuje, że to rozwiązanie nie jest aplikacją samodzielną. Rozwiązania Office zawiera składniki, które są obsługiwane w aplikacjach firmy Microsoft Office.  
  
## <a name="syntax"></a>Składnia  
  
```  
<customHostSpecified />  
```  
  
## <a name="elements-and-attributes"></a>Elementy i atrybuty  
 `customHostSpecified` Element jest wymagany dla rozwiązań pakietu Office. Tego elementu jest `co.v1` przestrzeni nazw i określa, czy to wdrożenie zawiera składnik, który będzie wdrażany w ramach hosta niestandardowego, a nie jest autonomiczną aplikacją.  
  
 Ten element jest elementem podrzędnym pierwszego `<entrypoint>` elementu w manifeście aplikacji. Nie mogą istnieć żadne inne elementy podrzędne tego `<entrypoint>` element lub [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] zgłosi błąd sprawdzania poprawności podczas instalacji.  
  
 Ten element ma żadnych atrybutów i elementów podrzędnych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje `customHostSpecified` elementu w manifeście aplikacji dla rozwiązań pakietu Office. Ten przykładowy kod jest częścią większego przykładu udostępnionego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).  
  
```  
<entryPoint>  
    <co.v1:customHostSpecified />  
</entryPoint>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  