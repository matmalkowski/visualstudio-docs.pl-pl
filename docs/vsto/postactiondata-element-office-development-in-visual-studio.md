---
title: "&lt;postactiondata —&gt; — Element (Office Development w Visual Studio) | Dokumentacja firmy Microsoft"
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
- <postActionData> element
- application manifests [Office development in Visual Studio], <postActionData> element
- postActionData element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: ea65f8789e3106abe8da46ae0302cdf0f4f47ef7
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="ltpostactiondatagt-element-office-development-in-visual-studio"></a>&lt;postactiondata —&gt; — Element (Office Development w Visual Studio)
  `postActionData` Elementu `vstav3` przestrzeń nazw określa dane skojarzone z dowolną akcję po wdrożeniu, która jest uruchamiana po zainstalowaniu rozwiązań pakietu Office.  
  
## <a name="syntax"></a>Składnia  
  
```  
<postActionData>  
</postActionData>  
```  
  
## <a name="elements-and-attributes"></a>Elementy i atrybuty  
 `postActionData` Element jest opcjonalny i znajduje się w `vstav3` przestrzeni nazw. Istnieje `postActionData` element zdefiniowany w manifeście aplikacji dla każdej akcji po wdrożeniu.  
  
 `postActions` Element nie ma żadnych atrybutów.  
  
 `postActions`nie ma elementów podrzędnych.  
  
## <a name="post-deployment-action-example"></a>Przykład akcji po wdrożeniu  
  
### <a name="description"></a>Opis  
 Poniższy przykład kodu pokazuje `postAction` elementu w manifeście aplikacji dla rozwiązań pakietu Office wdrożone za pomocą [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Ten przykładowy kod jest częścią większego przykładu udostępnionego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Kod  
  
```  
<vstav3:postActionData>  
  data in any format  
</vstav3:postActionData>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  