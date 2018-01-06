---
title: '&lt;postAction&gt; elementu (Office Development w Visual Studio) | Dokumentacja firmy Microsoft'
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
- application manifests [Office development in Visual Studio], <postAction> element
- <postAction> element
- postAction element
ms.assetid: a047e2e2-9732-4140-b8bd-bc5bd1b84291
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 4d42476d7298025fb18a703f027a2a870faf204a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltpostactiongt-element-office-development-in-visual-studio"></a>&lt;postAction&gt; elementu (Office Development w Visual Studio)
  `postAction` Elementu `vstav3` przestrzeń nazw zawiera `entrypoint` elementów i wszystkie `postActionData` elementy, które są powiązane z akcjami po wdrożeniu, które uruchamiane po zainstalowaniu rozwiązań pakietu Office.  
  
## <a name="syntax"></a>Składnia  
  
```  
<postAction>  
  <entryPoint>  
  </entryPoint>  
  <postActionData>  
  </postActionData>  
</postAction>  
```  
  
## <a name="elements-and-attributes"></a>Elementy i atrybuty  
 `postAction` Element jest opcjonalny i jest on `vstav3` przestrzeni nazw. Istnieje `postAction` element zdefiniowany w manifeście aplikacji dla każdej akcji po wdrożeniu.  
  
 `postAction` Element nie ma żadnych atrybutów.  
  
 `postAction`zawiera następujące elementy.  
  
### <a name="entrypoint"></a>Punkt wejścia  
 Opcjonalny. Rola `entryPoint` element `vstav3` przestrzeni nazw jest zdefiniowany w [&#60; punkty wejścia &#62; Element &#40; programowanie Office w Visual Studio &#41; ](../vsto/entrypoints-element-office-development-in-visual-studio.md).  
  
### <a name="postactiondata"></a>postactiondata —  
 Opcjonalny. Rola `postActionData` element `vstav3` przestrzeni nazw jest zdefiniowany w [&#60; postactiondata — &#62; Element &#40; programowanie Office w Visual Studio &#41; ](../vsto/postactiondata-element-office-development-in-visual-studio.md).  
  
## <a name="post-deployment-action-example"></a>Przykład akcji po wdrożeniu  
  
### <a name="description"></a>Opis  
 Poniższy przykład kodu pokazuje `postAction` elementu w manifeście aplikacji dla rozwiązań pakietu Office, które zostało wdrożone przy użyciu [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Ten przykładowy kod jest częścią większego przykładu udostępnionego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Kod  
  
```  
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
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  