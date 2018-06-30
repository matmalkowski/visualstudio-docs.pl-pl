---
title: 'Porady: tworzenie części sieci Web programu SharePoint | Dokumentacja firmy Microsoft'
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
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6437620b4215726ba48ea3234e37c76e77d21ebe
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120582"
---
# <a name="how-to-create-a-sharepoint-web-part"></a>Porady: Tworzenie składnika web part programu SharePoint
  Można tworzyć i dostosowywać części sieci web, dodając **składnika Web Part** elementu do żadnego projektu programu SharePoint, a następnie edytując plik kodu części sieci web lub za pomocą projektanta. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie składnika web part programu SharePoint za pomocą projektanta](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).  
  
### <a name="to-create-a-sharepoint-web-part"></a>Aby utworzyć składnika web part programu SharePoint
  
1.  Utwórz lub Otwórz projekt programu SharePoint.  
  
     Aby uzyskać więcej informacji, zobacz [SharePoint elementu szablonów projektu i projektu](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Wybierz węzeł projektu programu SharePoint w **Eksploratora rozwiązań** , a następnie wybierz **projektu** > **Dodaj nowy element**.  
  
3.  W **Dodaj nowy element** okna dialogowego rozwiń **SharePoint** węzeł, a następnie wybierz pozycję **2010** węzła.  
  
4.  Na liście szablonów programu SharePoint, wybierz **składnika Web Part**.  
  
5.  W **nazwa** polu, określ nazwę dla składnika web part, a następnie wybierz **Dodaj** przycisku.  
  
     Składnik web part jest wyświetlana w **Eksploratora rozwiązań**. Aby uzyskać więcej informacji o plikach, które zawiera składnik web part, zobacz [tworzenia składników web Part dla SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).  
  
6.  W **Eksploratora rozwiązań**, otwórz plik kodu dla składnika web part, który został właśnie utworzony.  
  
     Na przykład, jeśli nazwa składnika web part jest *WebPart1*, otwórz *WebPart1.vb* (w języku Visual Basic) lub *WebPart1.cs* (w języku C#).  
  
7.  W pliku kodu, Dodaj formanty do <xref:System.Web.UI.Control.CreateChildControls%2A> metody.  
  
     Na przykład zobacz [wskazówki: Tworzenie składnika web part dla SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md).  
  
## <a name="see-also"></a>Zobacz także
 [Tworzenie składników web Part dla SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Porady: Tworzenie składnika web part programu SharePoint za pomocą projektanta](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [Wskazówki: Tworzenie składnika web part dla SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)   
 [Wskazówki: Tworzenie składnika web part dla SharePoint za pomocą projektanta](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)  
  
  
