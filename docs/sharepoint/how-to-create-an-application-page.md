---
title: 'Porady: Tworzenie strony aplikacji | Dokumentacja firmy Microsoft'
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
- application pages [SharePoint development in Visual Studio], adding
- application pages [SharePoint development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: eefbb12584cdff2bb32b9d4406c916969ec435c4
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120287"
---
# <a name="how-to-create-an-application-page"></a>Porady: Tworzenie strony aplikacji
  Można utworzyć stronę sieci web ASP.NET dla jednego lub więcej witryn programu SharePoint. W programie SharePoint strony te są nazywane stron aplikacji. W przeciwieństwie do strony strony aplikacji zawiera kod, który jest uruchamiany za strony. Aby uzyskać więcej informacji, zobacz [tworzenie stron aplikacji dla programu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
### <a name="to-create-an-application-page"></a>Aby utworzyć stronę aplikacji  
  
1.  W programie Visual Studio otwórz lub utwórz projekt programu SharePoint.  
  
     Aby uzyskać więcej informacji, zobacz [SharePoint elementu szablonów projektu i projektu](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  W **Eksploratora rozwiązań**, wybierz węzeł projektu.  
  
3.  Na pasku menu wybierz **projektu** > **Dodaj nowy element**.  
  
4.  W **Dodaj nowy element** okna dialogowego rozwiń **SharePoint** węzeł, a następnie wybierz pozycję **2010** elementu.  
  
5.  Na liście szablonów programu SharePoint, wybierz **strony aplikacji**.  
  
6.  W **nazwa** polu, określ nazwę strony aplikacji, a następnie wybierz **Dodaj** przycisku.  
  
     Program Visual Studio dodaje kilka folderów i plików do projektu. Aby uzyskać więcej informacji o tych plikach, zobacz [tworzenie stron aplikacji dla programu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
     W **źródła** zostanie wyświetlony widok projektanta Visual Web Developer pliku strony ASP.NET. Strony można zaprojektować przez dodawanie formantów z **przybornika** i umieszczenie ich w zawartości symbole zastępcze. Aby uzyskać więcej informacji, zobacz [widoku źródła, Projektant strony sieci Web](http://msdn.microsoft.com/en-us/5911396b-fe51-4150-9ff1-b085f812862f).  
  
7.  Do obsługi zdarzeń formantu, należy dodać kod do pliku kodu na stronie aplikacji.  
  
     Plik kodowy pojawia się po rozwinięciu węzła pliku strony ASP.NET i ma *.cs* lub *.vb* rozszerzenia, w zależności od język projektu. Przykład end-to-end Tworzenie strony aplikacji, zobacz [wskazówki: Tworzenie strony aplikacji SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md).  
  
## <a name="see-also"></a>Zobacz także
 [Tworzenie stron aplikacji dla programu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Wskazówki: Tworzenie strony aplikacji SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)  
  
