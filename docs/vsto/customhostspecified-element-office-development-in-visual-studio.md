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
ms.assetid: 2212b7eb-bf94-4398-b9ea-0ab00203203b
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c7ad3bb1e62e2ea98f5afe1de5cc9eb49f711234
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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
  
  