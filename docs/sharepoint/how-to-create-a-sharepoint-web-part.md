---
title: "Porady: tworzenie części sieci Web programu SharePoint | Dokumentacja firmy Microsoft"
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
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
ms.assetid: 0d037522-c25e-4c24-93b7-518db0f791b7
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: f5d4f06b13c1c27c9f4b5e245e73929596dcf423
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-sharepoint-web-part"></a>Porady: tworzenie SharePoint Web Part
  Można tworzyć i dostosowywać części sieci web, dodając **składnika Web Part** elementu do żadnego projektu programu SharePoint, a następnie edytując plik kodu części sieci web lub za pomocą projektanta. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie składnika Web Part programu SharePoint za pomocą projektanta](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).  
  
### <a name="to-create-a-sharepoint-web-part"></a>Aby utworzyć składnika Web Part programu SharePoint  
  
1.  Utwórz lub Otwórz projekt programu SharePoint.  
  
     Aby uzyskać więcej informacji, zobacz [projekt SharePoint oraz szablony elementów projektu](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Wybierz węzeł projektu programu SharePoint w **Eksploratora rozwiązań** , a następnie wybierz **projektu**, **Dodaj nowy element**.  
  
3.  W **Dodaj nowy element** okna dialogowego rozwiń **SharePoint** węzeł, a następnie wybierz pozycję **2010** węzła.  
  
4.  Na liście szablonów programu SharePoint, wybierz **składnika Web Part**.  
  
5.  W **nazwa** polu, określ nazwę dla składnika web part, a następnie wybierz **Dodaj** przycisku.  
  
     Składnik web part jest wyświetlana w **Eksploratora rozwiązań**. Aby uzyskać więcej informacji o plikach, które zawiera składnik web part, zobacz [tworzenia składników Web Part dla SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).  
  
6.  W **Eksploratora rozwiązań**, otwórz plik kodu dla składnika web part, który został właśnie utworzony.  
  
     Na przykład jeśli nazwa składnika web part jest WebPart1, otwórz WebPart1.vb (w języku Visual Basic) lub WebPart1.cs (w języku C#).  
  
7.  W pliku kodu, Dodaj formanty do <xref:System.Web.UI.Control.CreateChildControls%2A> metody.  
  
     Na przykład zobacz [wskazówki: Tworzenie składnika Web Part dla SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie składników Web Part dla SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Porady: tworzenie SharePoint Web Part za pomocą projektanta](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [Wskazówki: Tworzenie składnika Web Part dla SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)   
 [Przewodnik: Tworzenie składnika Web part dla SharePoint za pomocą Projektanta](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)  
  
  