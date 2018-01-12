---
title: "Porady: Dodawanie odwołania wyjścia projektu | Dokumentacja firmy Microsoft"
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
- VB
- CSharp
helpviewer_keywords:
- project output references [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, project output references
- SharePoint development in Visual Studio, advanced packaging tools
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 0114971baa164858add68f2f1d6f571407ba5320
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-a-project-output-reference"></a>Porady: dodawanie odwołania wyjścia projektu
  Aby wdrożyć zestawy projektu programu SharePoint (lub pliki XAP w projekty Silverlight) w programie SharePoint, należy dodać je jako odwołania wyjścia projektu.  
  
 Ten proces tworzy zależność kompilacji rozwiązania między dwa projekty. Projekty skojarzone z odwołania do danych wyjściowych projektu są skompilowane zanim projekt SharePoint jest skompilowany i wdrożone.  
  
### <a name="to-add-a-project-output-reference"></a>Aby dodać odwołanie do danych wyjściowych projektu  
  
1.  Załadowanie rozwiązania, które zawiera co najmniej jeden projekt programu SharePoint i jeden projekt programu SharePoint.  
  
2.  W **Eksploratora rozwiązań**, wybierz element węzła projektu programu SharePoint.  
  
3.  W **właściwości** okna, wybierz **preferencje danych wyjściowych projektu** właściwości, a następnie wybierz przycisk wielokropka (![elipsy ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "ASP. Projektant Mobile NET elipsy")) przycisk obok niej.  
  
4.  W **preferencje danych wyjściowych projektu** oknie dialogowym wybierz **Dodaj** przycisku.  
  
5.  W okienku właściwości wybierz strzałkę **typu wdrożenia** właściwości, a następnie wybierz odpowiednią wartość dla elementu programu SharePoint odwołujesz się do, takich jak **ElementFile**.  
  
6.  Wybierz strzałkę obok pozycji **Nazwa projektu**, wybierz nazwę elementu projektu programu SharePoint, a następnie wybierz **OK** przycisku.  
  
## <a name="see-also"></a>Zobacz też  
 [Opakowanie i informacje o wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Porady: oznaczanie kontrolek pojęciem bezpiecznych kontrolek](../sharepoint/how-to-mark-controls-as-safe-controls.md)   
 [Rozwiązania pakowania i wdrażania SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  