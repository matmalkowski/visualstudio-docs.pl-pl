---
title: "&lt;postactions —&gt; — Element (Office Development w Visual Studio) | Dokumentacja firmy Microsoft"
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
- application manifests [Office development in Visual Studio], <postActions> element
- postActions element
- <postActions> element
ms.assetid: 6e487549-fdd6-49bd-be7a-b91f1f964594
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 282a1bff821ee032d0d08038858c3a04fc7796ba
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ltpostactionsgt-element-office-development-in-visual-studio"></a>&lt;postactions —&gt; — Element (Office Development w Visual Studio)
  `postActions` Elementu `vstav3` przestrzeń nazw zawiera wszystkie `postAction` elementy, które opisują akcje po wdrożeniu, co uruchomić po zainstalowaniu rozwiązań pakietu Office.  
  
## <a name="syntax"></a>Składnia  
  
```  
<postActions>  
  <postAction>  
    <entryPoint>  
    </entryPoint>  
    <postActionData>  
    </postActionData>  
  </postAction>  
</postActions>  
```  
  
## <a name="elements-and-attributes"></a>Elementy i atrybuty  
 `postActions` Element jest opcjonalny i jest on `vstav3` przestrzeni nazw. Istnieje tylko jeden `postActions` zdefiniowany w manifeście aplikacji element.  
  
 `postActions` Element nie ma żadnych atrybutów.  
  
 `postActions`ma następujący element.  
  
### <a name="postaction"></a>postAction  
 Opcjonalny. Rola `postAction` element `vstav3` przestrzeni nazw jest zdefiniowany w [&#60; postAction &#62; Element &#40; programowanie Office w Visual Studio &#41; ](../vsto/postaction-element-office-development-in-visual-studio.md).  
  
## <a name="post-deployment-action-example"></a>Przykład akcji po wdrożeniu  
  
### <a name="description"></a>Opis  
 Poniższy przykład kodu pokazuje `postActions` elementu w manifeście aplikacji dla rozwiązań pakietu Office wdrożone za pomocą [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Ten przykładowy kod jest częścią większego przykładu udostępnionego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Kod  
  
```  
<vstav3:postActions>  
  <vstav3:postAction>  
    <vstav3:entryPoint   
      class="PostDeploymentAction.PostDeploymentActionSample">  
      <assemblyIdentity   
        name="PostDeploymentAction"   
        version="1.0.0.0"   
        language="neutral"   
        processorArchitecture="msil" />  
    </vstav3:entryPoint>  
    <vstav3:postActionData>  
    </vstav3:postActionData>  
  </vstav3:postAction>  
</vstav3:postActions>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  