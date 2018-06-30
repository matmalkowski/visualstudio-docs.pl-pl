---
title: 'Wskazówki: Importowanie przepływu pracy wielokrotnego użytku programu SharePoint Designer do Visual Studio | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.WSPImport.ImportWF
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing reusable workflows
- reusable workflows [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2269beef06f7ca43556c2c00493ac8d7cb1c4ad5
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120329"
---
# <a name="walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio"></a>Wskazówki: Importowanie przepływu pracy wielokrotnego użytku programu SharePoint Designer do Visual Studio
  W tym przewodniku pokazano, jak zaimportować utworzone w programie SharePoint Designer 2010 do przepływu pracy wielokrotnego użytku [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu przepływu pracy programu SharePoint.  
  
 Przepływy pracy utworzone w programie SharePoint Designer lub *deklaratywne przepływy pracy*, składa się z [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] instrukcje zamiast kodu. Wprowadza SharePoint Designer 2010 *wielokrotnych przepływów danych*, portable, deklaratywne przepływów pracy, które mogą być używane przez różne listy w witrynach programu SharePoint, które są.  
  
 Przepływy pracy utworzone w [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)], takich jak maszyny stanu i sekwencyjny przepływów pracy, są nazywane *kodu przepływy pracy*. Przepływy pracy kodu składają się z plików XML i moduły kodu, w których użytkownicy mogą dostosowywać zachowanie przepływu pracy.  
  
 Program Visual Studio umożliwia importowanie wielokrotnego użytku przepływy pracy utworzone w programie SharePoint Designer 2010 i przekonwertować je na przepływy pracy kodu do użycia w witrynach programu SharePoint.  
  
 W tym przewodniku przedstawiono następujące zadania:  
  
-   Tworzenie prostego do ponownego użycia przepływu pracy w programie SharePoint Designer.  
  
-   Eksportowanie przepływu pracy wielokrotnego użytku programu SharePoint Designer do *WSP* pliku i do programu SharePoint.  
  
-   Importowanie *.wsp* pliku do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] przy użyciu projektu przepływu pracy wielokrotnego użytku importowania.  
  
-   Zmiana przepływu pracy przez dodanie kodu.  
  
-   Za pomocą zaimportowanych przepływu pracy w witrynie programu SharePoint.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   Obsługiwane wersje programu [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] i programu SharePoint. Aby uzyskać więcej informacji, zobacz [wymagania związane z opracowywaniem rozwiązań SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Program Visual Studio.  
  
-   Microsoft [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] SharePoint Designer 2010.  
  
## <a name="create-target-sharepoint-subsites"></a>Utwórz Lokacje podrzędne SharePoint docelowego
 Najpierw należy utworzyć dwa nowe Lokacje podrzędne programu SharePoint: jeden do obsługi wielokrotnych przepływów pracy z programu SharePoint Designer do obsługi przekonwertowanego przepływów pracy.  
  
#### <a name="to-create-sharepoint-subsites"></a>Aby utworzyć podwitrynę programu SharePoint  
  
1.  W programie SharePoint Designer 2010, na pasku menu wybierz **pliku** > **nowa, pusta witryna sieci Web**.  
  
2.  W **nowa, pusta witryna sieci Web** okno dialogowe, przejdź do witryny programu SharePoint, w której chcesz utworzyć przepływ pracy, lub użyj wartości http://*SystemName*/, a następnie wybierz **OK** przycisk.  
  
     Zostanie wyświetlona strona główna.  
  
3.  W **Lokacje podrzędne** wybierz **nowy** przycisku.  
  
4.  W **nowy** oknie dialogowym wybierz **szablonów programu SharePoint** na liście w okienku po lewej stronie i wybierz polecenie **witryny zespołu** na liście w okienku po prawej stronie.  
  
5.  W **Określ lokalizację witryny sieci Web** pozycję zamienić słowo **podwitryny** w adresie URL z **SPD1**, a następnie wybierz pozycję **OK** przycisku.  
  
     Spowoduje to otwarcie nowej witryny podrzędnej w programie SharePoint Designer. Zamknij to wystąpienie programu SharePoint Designer i wróć do pierwszego wystąpienia (lokacja najwyższego poziomu).  
  
6.  Powtórz kroki 3-5, aby utworzyć drugi witryny podrzędnej, teraz zastępowanie wyraz **podwitryny** w [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] z **SPD2**.  
  
## <a name="create-a-sharepoint-designer-reusable-workflow"></a>Tworzenie przepływu pracy wielokrotnego użytku programu SharePoint Designer
 Ponieważ SharePoint obejmuje wielokrotnego użytku przepływy pracy, które można użyć w tym przykładzie, można będzie utworzyć. W tym przepływie pracy proste gdy użytkownik wprowadza nowe zadanie na liście zadań, która ma określonego tytułu zadania jest przypisany do tego użytkownika.  
  
#### <a name="to-create-a-sharepoint-designer-reusable-workflow"></a>Aby utworzyć wielokrotny przepływ danych programu SharePoint Designer
  
1.  W **Lokacje podrzędne** wybierz **SPD1** witryny do zmodyfikowania go.  
  
2.  Na Wstążce wybierz **przepływu pracy wielokrotnego użytku z wersji** przycisku.  
  
     Zostanie wyświetlony Kreator tworzenia przepływu pracy wielokrotnego użytku.  
  
3.  W **nazwa** wprowadź **przepływu pracy zadań SPD**.  
  
4.  W **typu zawartości** wybierz **zadań**, a następnie wybierz pozycję **OK** przycisku.  
  
     Przepływ pracy zostanie otwarty w Projektancie przepływów pracy programu SharePoint Designer.  
  
5.  W Projektancie przepływów pracy, wybierz kroku 1, a następnie na Wstążce wybierz **warunku** przycisku.  
  
6.  Na liście warunki, wybierz **Jeśli wartość jest równa pola bieżącego elementu**.  
  
     Ten krok powoduje dodanie warunek o nazwie **Jeśli wartość jest równa pola**.  
  
7.  W **Jeśli wartość jest równa pola** warunku, wybierz **pola** łącza.  
  
8.  Na liście wartości, wybierz **tytuł**.  
  
9. W **Jeśli wartość jest równa pola** warunku, wybierz **wartość** łącza.  
  
10. W polu wprowadź **nowe zadanie**.  
  
     Instrukcja warunku teraz odczytuje **Jeśli bieżący element: tytuł jest równe nowe zadanie**.  
  
11. Wybierz wiersz w obszarze instrukcja warunku, a następnie na Wstążce wybierz **akcji** przycisku.  
  
12. Na liście akcji wybierz **zestaw pola w bieżącym elemencie**.  
  
13. W **pola Set wartość** akcji, wybierz **pola** połączyć, a następnie na liście, wybierz pozycję **przypisane do**.  
  
14. W **pola Set wartość** akcji, wybierz **wartość** łącza, a następnie na liście istniejących użytkowników i grup wybierz **użytkownika, który utworzył element**.  
  
15. Wybierz **Dodaj** przycisk, a następnie wybierz pozycję **OK** przycisku.  
  
     Wykonywanie instrukcji akcji odczytuje **ustawić przypisany do do bieżącego elementu: recenzowania utworzone przez**.  
  
## <a name="save-and-deploy-the-reusable-workflow"></a>Zapisz i wdróż przepływu pracy wielokrotnego użytku
 Ponieważ [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] można importować tylko *.wsp* plików, należy zapisać przepływu pracy wielokrotnego użytku jako *.wsp* pliku, a następnie wdrożyć go w programie SharePoint, przed zaimportowaniem go do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
> [!IMPORTANT]  
>  Jeśli wystąpi błąd wykonania wykonaniem tej procedury należy wykonać procedury na komputerze, który ma dostęp do witryny programu SharePoint.  
  
#### <a name="to-save-and-deploy-the-reusable-workflow"></a>Aby zapisać i wdrożyć wielokrotny przepływ danych  
  
1.  W górnej części programu SharePoint Designer, wybierz **zapisać** przycisk, aby zapisać postęp, a następnie wybierz pozycję **publikowania** przycisk, aby wdrożyć przepływu pracy **SPD1** witryny programu SharePoint .  
  
2.  W okienku nawigacji wybierz **przepływy pracy** obiektu.  
  
3.  W obszarze **przepływu pracy wielokrotnego użytku z wersji**, wybierz **przepływu pracy zadań SPD**.  
  
4.  Na Wstążce wybierz **Zapisz jako szablon** przycisk, aby zapisać ten przepływ pracy jako *WSP* pliku.  
  
5.  Otwórz **SPD1** witryny programu SharePoint w przeglądarce, aby wyświetlić *WSP* plik w programie SharePoint.  
  
6.  Na pasek szybkiego uruchamiania wybierz **biblioteki** łącza.  
  
7.  W **biblioteki dokumentów** wybierz **zasobów witryny** łącza.  
  
     **Przepływu pracy zadań SPD** pliku znajduje się zasoby innych lokacji.  
  
8.  Na liście plików wybierz nazwę tego pliku  
  
9. W **pobieranie pliku** oknie dialogowym wybierz **zapisać** przycisk, aby zapisać *WSP* pliku w systemie lokalnym.  
  
## <a name="import-the-wsp-file-into-visual-studio"></a>Zaimportuj plik wsp do programu Visual Studio
 Import *.wsp* pliku do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] przy użyciu projektu przepływu pracy wielokrotnego użytku importowania. Ten projekt konwertuje przepływu pracy z przepływu pracy wielokrotnego użytku, deklaratywne kodu przepływu pracy. Po przekonwertowaniu przepływu pracy, użyje kodu zmodyfikowania jego działania.  
  
#### <a name="to-import-a-workflow-from-a-wsp-file-and-modify-it"></a>Aby zaimportować przepływu danych z pliku .wsp, a następnie go zmodyfikować  
  
1.  W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], na pasku menu wybierz **pliku** > **nowy** > **projektu**.  
  
2.  W **nowy projekt** okna dialogowego rozwiń **SharePoint** węźle albo **Visual C#** lub **Visual Basic**, a następnie wybierz pozycję **2010** węzła.  
  
3.  W **szablony** okienku wybierz **przepływu pracy importowania wielokrotnego użytku z wersji programu SharePoint 2010** szablonu, pozostaw nazwę projektu jako **WorkflowImportProject1**, a następnie wybierz pozycję **OK** przycisku.  
  
     Zostanie wyświetlony Kreator dostosowania programu SharePoint.  
  
4.  Na **określić poziom lokacji i zabezpieczeń dla debugowania** wprowadź [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] dla drugiej witryny programu SharePoint podrzędnej, utworzony wcześniej: http://*Nazwa systemowa*/SPD2.  
  
5.  W **co to jest poziom zaufania dla tego rozwiązania programu SharePoint?** wybierz **Wdróż jako rozwiązanie farmy** przycisk opcji, a następnie wybierz pozycję **dalej** przycisku.  
  
     Aby uzyskać więcej informacji o trybie piaskownicy porównaniu z rozwiązaniami farmy, zobacz [zagadnienia dotyczące rozwiązania typu piaskownica](../sharepoint/sandboxed-solution-considerations.md).  
  
6.  W **określ nowe źródło projektu** strony, przejdź do lokalizacji w systemie, w której uprzednio zapisano *.wsp* pliku, otwórz plik, a następnie wybierz **dalej** przycisk.  
  
    > [!NOTE]  
    >  Wybierz **Zakończ** przycisk, aby zaimportować wszystkie dostępne elementy *WSP* pliku.  
  
     Spowoduje to wyświetlenie listy dostępnych do importowania wielokrotnych przepływów danych.  
  
7.  W **wybierz elementy do zaimportowania** wybierz **przepływu pracy zadań SPD** przepływu pracy, a następnie wybierz pozycję **Zakończ** przycisku.  
  
     Po zakończeniu operacji importu projektu o nazwie **WorkflowImportProject1** utworzeniu zawierającego przepływu pracy o nazwie **SPD_Workflow_TestFT**. W tym folderze jest plik definicji przepływu pracy *Elements.xml* i pliku projektanta przepływu pracy (*xoml*). Projektant zawiera dwa pliki: plik reguły (Rules) i plik CodeBehind (albo *.cs* lub *.vb*, w zależności od języka programowania projektu).  
  
8.  W **Eksploratora rozwiązań**, Usuń **inne pliki zaimportowane** folderu.  
  
9. W *Elements.xml* pliku, Usuń `InstantiationURL="_layouts/IniErkflIP.sspx"`.  
  
10. W **Eksploratora rozwiązań**, wybierz **WorkflowImportProject1**, a następnie na pasku menu wybierz **projektu** > **Ustaw jako projekt startowy**  można ustawić **WorkflowImportProject1** jako element startowy.  
  
     Wyświetla listę, natychmiast, podczas debugowania projektu.  
  
11. Ponieważ **importowanie wielokrotnego użytku z wersji 2010 przepływu pracy SharePoint** szablonu nie importuje wartości właściwości skojarzenia importowanych przepływu pracy, należy wprowadzić je. W tym celu:  
  
    1.  W **Eksploratora rozwiązań**, wybierz **SPD_Workflow_TestFT** węzła.  
  
    2.  Wybierz wielokropek (![elipsy ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "elipsy ASP.NET Mobile Designer")) przycisk Dalej, aby jedna z właściwości listy, takich jak **listy docelowej** właściwości.  
  
    3.  Uzupełnij brakujące wartości w Kreatorze dostosowania programu SharePoint, a następnie wybierz pozycję **Zakończ** przycisku.  
  
12. Wybierz Plik xoml, a następnie na pasku menu wybierz **widoku** > **projektanta** Aby wyświetlić zaimportowane przepływu pracy w Projektancie przepływów pracy.  
  
13. W **Windows Workflow 3.0** węzła **przybornika**, wykonaj jedną z następujących czynności:  
  
    -   Otwórz menu skrótów **kod** działania, a następnie wybierz pozycję **kopiowania**. W Projektancie przepływów pracy, otwórz menu skrótów wiersza w obszarze **SequenceActivity1** działania, a następnie wybierz pozycję **Wklej**.  
  
    -   Przeciągnij **kod** działania z **przybornika** do projektanta przepływów pracy i podłącz go do nowego wiersza w obszarze **SequenceActivity1** działania.  
  
     Działanie to dodaje do projektanta przepływów pracy, o nazwie **CodeActivity1**. W przypadku tego działania spowoduje dodanie Akcja kodu, która tworzy anons listy anonsów, gdy użytkownik uruchamia przepływ pracy.  
  
14. Wykonaj jeden z następujących zestawów czynności:  
  
    -   Kliknij dwukrotnie **CodeActivity1** do generowania program obsługi zdarzeń i wyświetlenia kodu.  
  
    -   W **właściwości** w oknie **CodeActivity1**, ustaw wartość **ExecuteCode** właściwości **codeActivity_ExecuteCode**.  
  
15. Dodaj następujący kod w istniejących **przy użyciu** lub **importów** instrukcji:  
  
     [!code-csharp[SP_SPDWFImport#1](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#1)]
     [!code-vb[SP_SPDWFImport#1](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#1)]  
  
16. Zastąp `codeActivity1_ExecuteCode` następującym kodem:  
  
     [!code-csharp[SP_SPDWFImport#2](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#2)]
     [!code-vb[SP_SPDWFImport#2](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#2)]  
  
## <a name="deploy-the-project-and-associate-the-workflow"></a>Wdrażanie projektu i skojarzenia przepływu pracy
 Następnie uruchom WorkflowImportProject1 wdrożyć ją w witrynie programu SharePoint, a następnie skojarzenia przepływu pracy z listą zadań do wyświetlenia i testowania zmodyfikowane, konwersji przepływu pracy.  
  
#### <a name="to-deploy-the-project-and-associate-the-workflow"></a>Aby wdrożyć projekt i skojarzyć przepływ danych  
  
1.  W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], wybierz **F5** klawisz, aby uruchomić i Wdróż projekt przekonwertowanego przepływu pracy.  
  
2.  Na pasek szybkiego uruchamiania wybierz **zadania** łącze, aby wyświetlić listę zadań.  
  
3.  Na **narzędzia listy** , wybierz pozycję **elementów** przycisk, a następnie wybierz pozycję **nowy element** przycisku.  
  
     **Zadania — nowy element** zostanie otwarte okno dialogowe.  
  
4.  W **tytuł** wprowadź **nowe zadanie**, a następnie wybierz pozycję **zapisać** przycisku.  
  
5.  Na **narzędzia listy** , wybierz pozycję **listy** przycisk, a następnie wybierz pozycję **ustawień listy** przycisku.  
  
     **Ustawień listy** zostanie wyświetlona strona.  
  
6.  W **uprawnienia i zarządzanie** wybierz **ustawienia przepływu pracy** łącza.  
  
     **Ustawienia przepływu pracy** zostanie wyświetlona strona.  
  
7.  Wybierz **Dodaj przepływ pracy** łącza.  
  
8.  W **przepływu pracy** wybierz **WorkflowImportProject1 - SPD przepływu pracy Test**.  
  
9. W **nazwa** wprowadź **SPD przepływu pracy Test**, a następnie wybierz pozycję **OK** przycisku.  
  
10. Na pasku szybkiego uruchamiania wybierz **zadania** listy.  
  
11. Wybierz strzałkę obok pozycji **nowe zadanie**, a następnie na liście, wybierz **przepływy pracy**.  
  
12. W **uruchomić nowego przepływu pracy** wybierz link do **SPD przepływu pracy Test**, a następnie wybierz pozycję **Start** przycisk, aby inicjować przepływ pracy.  
  
    > [!NOTE]  
    >  Alternatywnie możesz można automatycznie skojarzenia przepływu pracy z listą przez uruchomienie Kreatora ustawień przepływu pracy i ustawienia przepływu pracy do kojarzenia automatycznie.  
  
     Zwróć uwagę, że dwie akcje są wykonywane przez przepływ pracy: Twoja nazwa wyświetlana w zadania **przypisane do** kolumny i anons pojawia się w **anonsów** listy.  
  
## <a name="see-also"></a>Zobacz także
 [Importowanie elementów z istniejącej witryny SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Tworzenie rozwiązań programu SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Tworzenie formantów wielokrotnych dla części sieciowych lub stron aplikacji](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
