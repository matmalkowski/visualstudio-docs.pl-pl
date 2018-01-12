---
title: "Wskazówki: Tworzenie witryny niestandardowego działania przepływu pracy | Dokumentacja firmy Microsoft"
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
- custom workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, custom workflow activities
- site workflows [SharePoint development in Visual Studio]
- workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, site workflows
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: b723635b1baecfec4bddb2339414d57803c76d5d
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-create-a-custom-site-workflow-activity"></a>Wskazówki: tworzenie niestandardowego działania przepływu pracy witryny
  Ten przewodnik przedstawia sposób tworzenia działań niestandardowych do przepływu pracy z poziomu witryny przy użyciu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. (Przepływy pracy poziomie witryny dotyczą całej lokacji, a nie tylko listy w witrynie). Działania niestandardowego tworzy kopię zapasową listy anonsów, a następnie kopiuje zawartość listy anonsów do niego.  
  
 W tym przewodniku przedstawiono następujące zadania:  
  
-   Tworzenie przepływu pracy z poziomu witryny.  
  
-   Tworzenie działania niestandardowego przepływu pracy.  
  
-   Tworzenie i usuwanie listy programu SharePoint.  
  
-   Kopiowanie elementów z listy jeden do innego.  
  
-   Wyświetlanie listy na pasek szybkiego uruchamiania.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   Obsługiwane wersje programu [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] i programu SharePoint. Aby uzyskać więcej informacji, zobacz [wymagania dotyczące opracowywania rozwiązań SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Program Visual Studio.  
  
## <a name="creating-a-site-workflow-custom-activity-project"></a>Tworzenie projektu lokacji niestandardowego działania przepływu pracy  
 Najpierw utwórz projekt do przechowywania i przetestować działania niestandardowego przepływu pracy.  
  
#### <a name="to-create-a-site-workflow-custom-activity-project"></a>Aby utworzyć projekt niestandardowego działania przepływu pracy witryny  
  
1.  Na pasku menu wybierz **pliku**, **nowy**, **projektu** do wyświetlenia **nowy projekt** okno dialogowe.  
  
2.  Rozwiń węzeł **SharePoint** węźle albo **Visual C#** lub **Visual Basic**, a następnie wybierz pozycję **2010** węzła.  
  
3.  W **szablony** okienku wybierz **projektu programu SharePoint 2010** szablonu.  
  
4.  W **nazwa** wprowadź **AnnouncementBackup**, a następnie wybierz pozycję **OK** przycisku.  
  
     **Kreator dostosowania programu SharePoint** pojawi się.  
  
5.  Na **określić poziom lokacji i zabezpieczeń dla debugowania** wybierz pozycję **Wdróż jako rozwiązanie farmy** przycisk opcji, a następnie wybierz pozycję **Zakończ** przycisk, aby zaakceptować poziom i domyślne witryny zaufania.  
  
     Ten krok określa poziom zaufania dla rozwiązania jako rozwiązanie farmy, jedyną dostępną opcją dla projektów przepływu pracy.  
  
6.  W **Eksploratora rozwiązań**, wybierz węzeł projektu, a następnie na pasku menu wybierz **projektu**, **Dodaj nowy element**.  
  
7.  Pod **Visual C#** lub **Visual Basic**, rozwiń węzeł **SharePoint** węzeł, a następnie wybierz pozycję **2010** węzła.  
  
8.  W **szablony** okienku wybierz **sekwencyjnego przepływu pracy (tylko rozwiązanie farmy)** szablonu, a następnie wybierz pozycję **Dodaj** przycisku.  
  
     **Kreator dostosowania programu SharePoint** pojawi się.  
  
9. Na **Określ nazwę przepływu pracy do debugowania** pozycję Zaakceptuj nazwę domyślną (AnnouncementBackup - Workflow1). Zmień typ szablonu przepływu pracy do **przepływu pracy lokacji**, a następnie wybierz pozycję **dalej** przycisku.  
  
10. Wybierz **Zakończ** przycisk, aby zaakceptować pozostałe ustawienia domyślne.  
  
## <a name="adding-a-custom-workflow-activity-class"></a>Dodawanie klasy działania niestandardowego przepływu pracy  
 Następnie Dodaj klasę do projektu, aby zawierają kod dla działania niestandardowego przepływu pracy.  
  
#### <a name="to-add-a-custom-workflow-activity-class"></a>Aby dodać klasę działania niestandardowego przepływu pracy  
  
1.  Na pasku menu wybierz **projektu**, **Dodaj nowy element** do wyświetlenia **Dodaj nowy element** okno dialogowe.  
  
2.  W **zainstalowane szablony** widok drzewa, wybierz **kod** węzeł, a następnie wybierz pozycję **klasy** szablonu na liście szablony elementów projektu. Użyj nazwy domyślnej Class1. Wybierz **Dodaj** przycisku.  
  
3.  Zastąp cały kod w Class1 następujące czynności:  
  
     [!code-csharp[SP_AnnBackup#1](../sharepoint/codesnippet/CSharp/announcementbackup/class1.cs#1)]
     [!code-vb[SP_AnnBackup#1](../sharepoint/codesnippet/VisualBasic/announcementbackupvb/class1.vb#1)]  
  
4.  Zapisz projekt, a następnie na pasku menu wybierz **kompilacji**, **Kompiluj rozwiązanie**.  
  
     Class1 pojawia się jako akcja niestandardowa w **przybornika** na **składniki AnnouncementBackup** kartę.  
  
## <a name="adding-the-custom-activity-to-the-site-workflow"></a>Dodawanie działań niestandardowych do przepływu pracy witryny  
 Następnie Dodaj działanie w przepływie pracy zawiera kod niestandardowy.  
  
#### <a name="to-add-a-custom-activity-to-the-site-workflow"></a>Do dodawania działań niestandardowych do przepływu pracy witryny  
  
1.  Otwórz Workflow1 w Projektancie przepływów pracy w widoku Projekt.  
  
2.  Przeciągnij Class1 z **przybornika** , aby był wyświetlany w obszarze `onWorkflowActivated1` działania lub Otwórz menu skrótów dla Class1, wybierz **kopiowania**, otwórz menu skrótów wiersza w obszarze `onWorkflowActivated1` działanie, a następnie wybierz pozycję **Wklej**.  
  
3.  Zapisz projekt.  
  
## <a name="testing-the-site-workflow-custom-activity"></a>Testowanie niestandardowego działania przepływu pracy witryny  
 Następnie uruchom projekt i uruchomić przepływ pracy witryny. Działań niestandardowych powoduje utworzenie kopii zapasowej listy anonsów i kopiuje zawartość z bieżącej listy anonsów do niego. Kod sprawdza również, czy przed utworzeniem jedną istnieje już listy kopii zapasowych. Jeśli istnieje już listy kopii zapasowych, ich usunięcia. Kod dodaje również link do nowej listy na pasek szybkiego uruchamiania witryny programu SharePoint.  
  
#### <a name="to-test-the-site-workflow-custom-activity"></a>Aby przetestować niestandardowego działania przepływu pracy witryny  
  
1.  Wybierz klawisz F5, aby uruchomić projekt, a następnie wdrożyć go w programie SharePoint.  
  
2.  Na pasek szybkiego uruchamiania wybierz **wymieniono** łącze, aby wyświetlić wszystkie listy, które są dostępne w witrynie programu SharePoint. Zwróć uwagę, istnieje tylko jedna lista dla anonsów o nazwie **anonsów**.  
  
3.  W górnej części strony sieci Web programu SharePoint, wybierz **przepływy pracy witryn** łącza.  
  
4.  W obszarze początku sekcji nowego przepływu pracy, wybierz **AnnouncementBackup - Workflow1** łącza. To uruchamiania przepływów pracy witryny i uruchamia kod w akcji niestandardowej.  
  
5.  Na pasek szybkiego uruchamiania wybierz **kopii zapasowej anonsów** łącza. Zwróć uwagę, że wszystkie anonsy, które są zawarte w **anonsów** listy zostały skopiowane do tej nowej listy.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: tworzenie obsługiwanego odbiornika](../sharepoint/how-to-create-an-event-receiver.md)   
 [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  