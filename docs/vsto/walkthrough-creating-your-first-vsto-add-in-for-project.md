---
title: 'Wskazówki: Tworzenie pierwszego VSTO dodatek dla projektu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- Project [Office development in Visual Studio], creating your first project
- add-ins [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 671ea761588cc56437334e8a7b8b7c58a2061970
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34845785"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-project"></a>Wskazówki: Tworzenie pierwszego VSTO dodatek dla projektu
  W tym przewodniku przedstawiono sposób tworzenia dodatku VSTO dla programu Microsoft Office Project. Funkcje, które możesz utworzyć w tego rodzaju rozwiązania są dostępne dla aplikacji, niezależnie od tego, które projekty są otwarte. Aby uzyskać więcej informacji, zobacz [rozwój rozwiązań Office ― omówienie &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Tworzenie projektów dodatku VSTO projektu.  
  
-   Pisanie kodu, który korzysta z modelu obiektu projektu można dodać zadania do nowego projektu.  
  
-   Tworzenie i uruchamianie projektu, aby przetestować go.  
  
-   Czyszczenie projektu ukończone, aby dodatku VSTO już nie uruchamia automatycznie na komputerze deweloperskim.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Project_15_short](../vsto/includes/project-15-short-md.md)] lub [!INCLUDE[Project_14_short](../vsto/includes/project-14-short-md.md)].  
  
## <a name="create-the-project"></a>Utwórz projekt  
  
### <a name="to-create-a-new-project-in-visual-studio"></a>Aby utworzyć nowy projekt w programie Visual Studio  
  
1.  Uruchom [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Na **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu**.  
  
3.  W okienku szablonów rozwiń **Visual C#** lub **Visual Basic**, a następnie rozwiń węzeł **Office i SharePoint**.  
  
4.  Pod rozwiniętym **Office i SharePoint** węzła, wybierz opcję **dodatków pakietu Office** węzła.  
  
5.  Na liście szablony projektów, wybierz **dodatek 2010 projektu** lub **dodatku 2013 projektu**.  
  
6.  W **nazwa** wpisz **FirstProjectAddIn**.  
  
7.  Kliknij przycisk **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Tworzy **FirstProjectAddIn** projektu i otwiera **thisaddin —** pliku kodu w edytorze.  
  
## <a name="write-code-that-adds-a-new-task-to-a-project"></a>Pisanie kodu, który dodaje nowe zadanie do projektu  
 Następnie dodaj kod do klasy ThisAddIn pliku kodu. Nowy kod korzysta z modelu obiektu projektu, aby dodać nowe zadanie do projektu. Domyślnie plik kodu klasy ThisAddIn zawiera następujące wygenerowanego kodu:  
  
-   Częściową definicją `ThisAddIn` klasy. Ta klasa udostępnia punkt wejścia dla kodu i zapewnia dostęp do modelu obiektowego projektu. Aby uzyskać więcej informacji, zobacz [dodatków VSTO programu](../vsto/programming-vsto-add-ins.md). W pozostałej części `ThisAddIn` klasa jest zdefiniowana w pliku ukryty kod, który nie należy modyfikować.  
  
-   `ThisAddIn_Startup` i `ThisAddIn_Shutdown` procedury obsługi zdarzeń. Te programy obsługi zdarzeń są wywoływane, gdy projekt ładuje i zwalnia z dodatku VSTO. Użyj tych programów obsługi zdarzeń zainicjować dodatku VSTO z po załadowaniu go, a także aby wyczyścić zasoby używane przez dodatek VSTO, gdy jest zwolniony. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).  
  
### <a name="to-add-a-task-to-a-new-project"></a>Aby dodać zadanie do nowego projektu  
  
1.  W pliku kodu klasy ThisAddIn, Dodaj następujący kod do `ThisAddIn` klasy. Ten kod definiuje programu obsługi zdarzeń dla `NewProject` zdarzenie `Microsoft.Office.Interop.MSProject.Application` klasy.  
  
     Gdy użytkownik tworzy nowy projekt, ten program obsługi zdarzeń dodaje zadanie do projektu.  
  
     [!code-vb[Trin_ProjectAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ProjectAddInTutorial/ThisAddIn.vb#1)]
     [!code-csharp[Trin_ProjectAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs#1)]  
  
 Aby zmodyfikować projektu, w tym przykładzie kodu za pomocą następujących obiektów:  
  
-   `Application` Pole `ThisAddIn` klasy. `Application` Pola zwraca `Microsoft.Office.Interop.MSProject.Application` obiektu, który reprezentuje wystąpienie bieżącego projektu.  
  
-   `pj` Parametr obsługi zdarzeń dla zdarzenia NewProject. `pj` Parametr jest `Microsoft.Office.Interop.MSProject.Project` obiektu, który reprezentuje projektu. Aby uzyskać więcej informacji, zobacz [projektu rozwiązania](../vsto/project-solutions.md).  
  
1.  Jeśli używasz języka C#, Dodaj następujący kod do `ThisAddIn_Startup` obsługi zdarzeń. Ten kod łączy `Application_Newproject` obsługi zdarzenia ze zdarzeniem NewProject.  
  
     [!code-csharp[Trin_ProjectAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs#2)]  
  
  
## <a name="test-the-project"></a>Projekt testowy  
 Gdy skompilować i uruchomić projekt, sprawdź, czy nowe zadanie jest wyświetlany w nowym projekcie wynikowym.  
  
### <a name="to-test-the-project"></a>Aby przetestować projekt  
  
1.  Naciśnij klawisz **F5** Aby skompilować i uruchomić projekt. Program Microsoft Project uruchamia i automatycznie otwiera nowy pusty projekt.  
  
     Podczas kompilowania projektu kod jest kompilowany do zestawu, który znajduje się w folderze wyjściowym kompilacji dla projektu. Program Visual Studio tworzy również zbiór wpisów rejestru, które umożliwiają projektu odnaleźć i załadować dodatku VSTO i konfiguruje ustawienia zabezpieczeń na komputerze dewelopera, aby włączyć dodatku VSTO do uruchomienia. Aby uzyskać więcej informacji, zobacz [Omówienie procesu kompilacji rozwiązania pakietu Office](http://msdn.microsoft.com/en-us/a9d12e4f-c9ea-4a62-a841-c42b91f831ee).  
  
2.  Sprawdź, czy nowe zadanie jest dodane do pustego projektu.  
  
3.  Sprawdź, czy następujący tekst jest wyświetlany w **Nazwa zadania** pole zadania.  
  
     **Ten tekst został dodany przy użyciu kodu.**  
  
4.  Zamknij program Microsoft Project.  
  
## <a name="clean-up-the-project"></a>Czyszczenie projektu  
 Po zakończeniu tworzenia projektu, Usuń dodatku VSTO zestaw, wpisy rejestru i ustawienia zabezpieczeń na komputerze projektowym. W przeciwnym razie dodatku VSTO uruchomi każdym otwarciu programu Microsoft Project na komputerze dewelopera.  
  
### <a name="to-clean-up-your-project"></a>Aby wyczyścić projektu  
  
1.  W programie Visual Studio na **kompilacji** menu, kliknij przycisk **czystą rozwiązania**.  
  
## <a name="next-steps"></a>Następne kroki  
 Teraz, gdy utworzono podstawowe VSTO dodatku dla projektu, można dowiedzieć się więcej o umożliwiające tworzenie dodatków narzędzi VSTO z tych tematów:  
  
-   Ogólne zadania programowania, które można wykonywać w dodatkach VSTO dla projektu: [dodatków VSTO programu](../vsto/programming-vsto-add-ins.md).  
  
-   Za pomocą modelu obiektów programu Project: [projektu rozwiązania](../vsto/project-solutions.md).  
  
-   Kompilowanie i debugowanie dodatków narzędzi VSTO dla projektu: [rozwiązań Office kompilacji](../vsto/building-office-solutions.md).  
  
-   Wdrażanie dodatków narzędzi VSTO dla projektu: [wdrażania rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Program dodatków VSTO](../vsto/programming-vsto-add-ins.md)   
 [Rozwiązania projektu](../vsto/project-solutions.md)   
 [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md)   
 [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)   
 [Przegląd szablonów projektu pakietu Office](../vsto/office-project-templates-overview.md)  
  
  