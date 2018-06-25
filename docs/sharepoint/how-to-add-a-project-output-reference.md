---
title: 'Porady: Dodawanie odwołania wyjścia projektu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- project output references [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, project output references
- SharePoint development in Visual Studio, advanced packaging tools
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 47b6a3d164bbe1ddcda6d131275427fb1f815198
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755480"
---
# <a name="how-to-add-a-project-output-reference"></a>Porady: Dodawanie odwołania wyjścia projektu
  Aby wdrożyć zestawy projektu programu SharePoint (lub pliki XAP w projekty Silverlight) w programie SharePoint, należy dodać je jako odwołania wyjścia projektu.  
  
 Ten proces tworzy zależność kompilacji rozwiązania między dwa projekty. Projekty skojarzone z odwołania do danych wyjściowych projektu są skompilowane zanim projekt SharePoint jest skompilowany i wdrożone.  
  
### <a name="to-add-a-project-output-reference"></a>Aby dodać odwołanie do danych wyjściowych projektu
  
1.  Załadowanie rozwiązania, które zawiera co najmniej jeden projekt programu SharePoint i jeden projekt programu SharePoint.  
  
2.  W **Eksploratora rozwiązań**, wybierz element węzła projektu programu SharePoint.  
  
3.  W **właściwości** okna, wybierz **preferencje danych wyjściowych projektu** właściwości, a następnie wybierz przycisk wielokropka (![elipsy ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "ASP. Projektant Mobile NET elipsy")) przycisk obok niej.  
  
4.  W **preferencje danych wyjściowych projektu** oknie dialogowym wybierz **Dodaj** przycisku.  
  
5.  W okienku właściwości wybierz strzałkę **typu wdrożenia** właściwości, a następnie wybierz odpowiednią wartość dla elementu programu SharePoint odwołujesz się do, takich jak **ElementFile**.  
  
6.  Wybierz strzałkę obok pozycji **Nazwa projektu**, wybierz nazwę elementu projektu programu SharePoint, a następnie wybierz **OK** przycisku.  
  
## <a name="see-also"></a>Zobacz także
 [Podaj informacje pakowania i wdrażania w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Porady: oznaczanie kontrolek pojęciem bezpiecznych kontrolek](../sharepoint/how-to-mark-controls-as-safe-controls.md)   
 [Pakiet i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  
