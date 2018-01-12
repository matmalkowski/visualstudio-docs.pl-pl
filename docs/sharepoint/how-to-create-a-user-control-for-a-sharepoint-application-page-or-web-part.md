---
title: "Porady: Tworzenie formantu użytkownika dla strony aplikacji SharePoint lub składnik Web Part | Dokumentacja firmy Microsoft"
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
- user controls [SharePoint development in Visual Studio], creating
- user controls [SharePoint development in Visual Studio], adding
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 7fc51bae65f67a3810c6db208e5f7c6f04183c22
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part"></a>Porady: tworzenie formantu użytkownika dla części sieciowej lub strony aplikacji SharePoint
  Można tworzyć niestandardowe kontrolki użytkownika, które dostarczają niestandardowych funkcjonalności dla rozwiązania SharePoint oraz można używać tych funkcjonalności ponownie w obrębie projektu. Można dołączyć kontrolki użytkownika do części sieci lub strony aplikacji, dodać inne kontrolki ASP.NET oraz SharePoint oraz zdefiniować właściwości o metody dla kontrolki. Aby uzyskać więcej informacji na temat kontrolek użytkownika, zobacz [tworzenia kontrolki do ponownego użycia dla części sieciowych lub stron aplikacji](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md) i [kontrolek użytkownika i kontrolek serwera w programie SharePoint](http://blogs.msdn.com/b/kaevans/archive/2011/04/28/user-controls-and-server-controls-in-sharepoint.aspx).  
  
### <a name="to-create-a-user-control-for-sharepoint"></a>Aby utworzyć kontrolkę użytkownika dla programu SharePoint  
  
1.  W programie Visual Studio otwórz lub utwórz projekt programu SharePoint.  
  
     Zobacz [szablonów elementu projektu SharePoint i projektu](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  W **Eksploratora rozwiązań**, wybierz węzeł projektu.  
  
3.  Na pasku menu wybierz **projektu**, **Dodaj nowy element**.  
  
     **Dodaj nowy element** zostanie otwarte okno dialogowe.  
  
4.  W **zainstalowana** okienku wybierz **Office i SharePoint** węzła.  
  
5.  Na liście szablonów programu SharePoint, wybierz **kontrolki użytkownika (farmy rozwiązania tylko)**.  
  
    > [!NOTE]  
    >  Kontrolki użytkownika działają tylko w rozwiązaniach farmy.  
  
6.  W **nazwa** polu, określ nazwę dla formantu użytkownika, a następnie wybierz **Dodaj** przycisku.  
  
     Program Visual Studio dodaje kilka folderów i plików do projektu. Aby uzyskać więcej informacji o tych plikach, zobacz [tworzenia kontrolki do ponownego użycia dla części sieciowych lub stron aplikacji](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).  
  
     Domyślnie plik formantu użytkownika pojawia się w **źródła** Widok projektanta Visual Web Developer. W tym widoku można edytować znaczniki XML kontrolki. Możesz przełączyć się do **projekt** przejrzeć wizualne projektowanie formantu przeciągając formantów z **przybornika**. Zobacz [widoku Projekt, Projektant strony Web](http://msdn.microsoft.com/en-us/d8f2270a-357d-40a4-9b39-1a3f2366216d).  
  
7.  Aby obsługiwać zdarzenia występujące w kontrolce, należy dodać kod do pliku kodu kontrolki użytkownika.  
  
     Ten plik zostanie wyświetlony w **Eksploratora rozwiązań** w pliku sterowania użytkownika i ma rozszerzenie .cs lub .vb, w zależności od język projektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie formantów wielokrotnych dla części sieciowych lub stron aplikacji](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)   
 [Tworzenie stron aplikacji dla SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Tworzenie części sieciowych dla SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)  
  
  