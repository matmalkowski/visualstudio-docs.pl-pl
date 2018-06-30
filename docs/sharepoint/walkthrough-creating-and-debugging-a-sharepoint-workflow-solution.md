---
title: 'Wskazówki: Tworzenie i debugowanie rozwiązania przepływu pracy programu SharePoint | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Workflow.WorkflowConditions
- VS.SharePointTools.Workflow.WorkflowList
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6035b8ceb693434e2e8bc652b91ee31ceb3ebe02
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120314"
---
# <a name="walkthrough-create-and-debug-a-sharepoint-workflow-solution"></a>Wskazówki: Tworzenie i debugowanie rozwiązania przepływu pracy SharePoint
  W tym przewodniku pokazano, jak utworzyć szablon podstawowy sekwencyjnego przepływu pracy. Właściwości biblioteki dokumentów udostępnionych w celu określenia, czy dokumentu została przejrzana sprawdza, czy przepływ pracy. Jeśli dokumentu została przejrzana, zakończeniu przepływu pracy.  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Tworzenie projektu SharePoint listy definicji sekwencyjnego przepływu pracy w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   Tworzenie działań przepływu pracy.  
  
-   Obsługa zdarzeń działania przepływu pracy.  
  
> [!NOTE]  
>  Mimo że w tym przewodniku zastosowano projektu sekwencyjnego przepływu pracy, ten proces jest takie samo dla projektu przepływu pracy stan maszyny.  
>   
>  Ponadto komputer mogą być wyświetlane inne nazwy i lokalizacje niektórych użytkownika programu Visual Studio interfejsu elementów w poniższych instrukcjach. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   Obsługiwane wersje systemu Microsoft Windows i programu SharePoint. Aby uzyskać więcej informacji, zobacz [wymagania związane z opracowywaniem rozwiązań SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Program Visual Studio.  
  
## <a name="add-properties-to-the-sharepoint-shared-documents-library"></a>Dodawanie właściwości do biblioteki udostępnionych dokumentów programu SharePoint
 Aby śledzić stan przeglądu dokumentów w **udostępnionych dokumentów** biblioteki, utworzymy trzy nowe właściwości dla udostępnionych dokumentów w naszej witrynie programu SharePoint: `Status`, `Assignee`, i `Review Comments`. Definiujemy tych właściwości w **dokumenty udostępnione** biblioteki.  
  
#### <a name="to-add-properties-to-the-sharepoint-shared-documents-library"></a>Aby dodać właściwości do programu SharePoint udostępnionych dokumentów biblioteki  
  
1.  Otwórz witrynę programu SharePoint, np. http://\<Nazwa systemowa > / SitePages/Home.aspx w przeglądarce sieci Web.  
  
2.  Na pasek szybkiego uruchamiania wybierz **SharedDocuments**.  
  
3.  Wybierz **biblioteki** na **narzędzia biblioteki** wstążki, a następnie wybierz pozycję **Utwórz kolumnę** na Wstążce, aby utworzyć nową kolumnę.  
  
4.  Nazwa kolumny **stan dokumentu**, Ustaw typ **wybór (menu, które można wybierać)**, określ następujące trzy opcje, a następnie wybierz pozycję **OK** przycisk:  
  
    -   **Przejrzyj potrzebne**  
  
    -   **Zakończenie przeglądu**  
  
    -   **Żądanie zmiany**  
  
5.  Utwórz dwie kolumny i nazwij je **ona** i **komentarzy**. Ustaw typ kolumny ona jako pojedynczy wiersz tekstu i typ kolumny komentarzy jako wiele wierszy tekstu.  
  
## <a name="enable-documents-to-be-edited-without-requiring-a-check-out"></a>Włącz dokumentów do edycji bez konieczności wyewidencjonowanie
 Jest łatwiejsze testowanie szablonu przepływu pracy, gdy dokumenty można edytować, bez konieczności ich wyewidencjonować. Witryna programu SharePoint, aby włączyć, który skonfigurujesz w następnej procedurze.  
  
#### <a name="to-enable-documents-to-be-edited-without-checking-them-out"></a>Aby włączyć dokumentów do edycji bez wyewidencjonowania ich  
  
1.  Na pasek szybkiego uruchamiania wybierz **dokumenty udostępnione** łącza.  
  
2.  Na **narzędzia biblioteki** wstążki, wybierz **biblioteki** karcie, a następnie wybierz pozycję **ustawienia biblioteki** przycisk, aby wyświetlić **ustawienia biblioteki dokumentów** strony.  
  
3.  W **ustawienia ogólne** wybierz **ustawienia przechowywania wersji** łącze, aby wyświetlić **ustawienia przechowywania wersji** strony.  
  
4.  Sprawdź, czy ustawienie **wymagają dokumentów, aby zostać wyewidencjonowany zanim mogą je edytować** jest **nr**. Jeśli nie, zmień jej **nr** , a następnie wybierz **OK** przycisku.  
  
5.  Zamknij przeglądarkę.  
  
## <a name="create-a-sharepoint-sequential-workflow-project"></a>Tworzenie projektu sekwencyjnego przepływu pracy programu SharePoint
 Sekwencyjny przepływ pracy jest zestaw kroków wykonuje w kolejności, dopóki nie zakończy się ostatnie działanie. W tej procedurze utworzymy sekwencyjnego przepływu pracy, które będą stosowane do naszej listy Dokumenty udostępnione. Kreator przepływu pracy można skojarzyć przepływu pracy z definicji witryny lub definicji listy i pozwala określić, gdy zostanie uruchomiony przepływ pracy.  
  
#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>Aby utworzyć projekt sekwencyjnego przepływu pracy programu SharePoint  
  
1.  Uruchom [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Na pasku menu wybierz **pliku** > **nowy** > **projektu** do wyświetlenia **nowy projekt** okno dialogowe.  
  
3.  Rozwiń węzeł **SharePoint** węźle albo **Visual C#** lub **Visual Basic**, a następnie wybierz pozycję **2010** węzła.  
  
4.  W **szablony** okienku wybierz **projektu programu SharePoint 2010** szablonu.  
  
5.  W **nazwa** wprowadź **MySharePointWorkflow** , a następnie wybierz **OK** przycisku.  
  
     **Kreator dostosowania programu SharePoint** pojawi się.  
  
6.  W **określić poziom lokacji i zabezpieczeń dla debugowania** wybierz pozycję **Wdróż jako rozwiązanie farmy** przycisk opcji, a następnie wybierz pozycję **Zakończ** przycisk, aby zaakceptować poziom i domyślne witryny zaufania.  
  
     Ten krok określa poziom zaufania dla rozwiązania jako rozwiązanie farmy, jedyną dostępną opcją dla projektów przepływu pracy. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące rozwiązania typu piaskownica](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  W **Eksploratora rozwiązań**, wybierz węzeł projektu, a następnie na pasku menu wybierz **projektu** > **Dodaj nowy element**.  
  
8.  Pod **Visual C#** lub **Visual Basic**, rozwiń węzeł **SharePoint** węzeł, a następnie wybierz pozycję **2010** węzła.  
  
9. W **szablony** okienku wybierz **sekwencyjnego przepływu pracy (tylko rozwiązanie farmy)** szablonu, a następnie wybierz pozycję **Dodaj** przycisku.  
  
     **Kreator dostosowania programu SharePoint** pojawi się.  
  
10. W **Określ nazwę przepływu pracy do debugowania** pozycję Zaakceptuj nazwę domyślną (**MySharePointWorkflow - Workflow1**). Należy zachować wartość typu szablonu przepływu pracy domyślne, **przepływu pracy**, a następnie wybierz pozycję **dalej** przycisku.  
  
11. W **czy program Visual Studio ma automatycznie skojarzyć przepływ pracy w sesji debugowania?** wybierz pozycję **dalej** przycisk, aby zaakceptować wszystkie ustawienia domyślne.  
  
     Ten krok automatycznie skojarzy przepływu pracy z biblioteki dokumentów udostępnionych.  
  
12. W **Określ sposób uruchamiania przepływu pracy warunków** pozostaw wartości domyślne wybranym **sposób przepływu pracy, aby uruchomić?** sekcji, a następnie wybierz **Zakończ** przycisku.  
  
     Ta strona umożliwia określenie, po uruchomieniu przepływu pracy. Domyślnie, przepływ pracy jest uruchamiany albo gdy użytkownik ręcznie uruchamia go w SharePoint lub utworzenia elementu, z którym skojarzony jest przepływ pracy.  
  
## <a name="create-workflow-activities"></a>Tworzenie działań przepływu pracy
 Przepływy pracy zawierają jedną lub więcej *działania* reprezentujące akcje do wykonania. Rozmieść działań przepływu pracy za pomocą projektanta przepływu pracy. W tej procedurze dwa działania zostanie dodany do przepływu pracy: działanie HandleExternalEventActivity i OnWorkFlowItemChanged. Te działania monitorowania stanu przeglądu dokumentów w **dokumenty udostępnione** listy  
  
#### <a name="to-create-workflow-activities"></a>Aby utworzyć działań przepływu pracy  
  
1.  Przepływ pracy powinien być wyświetlany w Projektancie przepływów pracy. Jeśli nie, następnie otwórz opcję **Workflow1.cs** lub **Workflow1.vb** w **Eksploratora rozwiązań**.  
  
2.  W projektancie, wybierz **OnWorkflowActivated1** działania.  
  
3.  W **właściwości** okna, wprowadź **ramach działania onWorkflowActivated** obok **Invoked** właściwości, a następnie wybierz klawisz Enter.  
  
     Zostanie otwarty w edytorze kodu i metoda obsługi zdarzeń o nazwie w ramach działania onWorkflowActivated są dodawane do pliku kodu Workflow1.  
  
4.  Wrócić do projektanta przepływów pracy, otwórz przybornika, a następnie rozwiń węzeł **Windows Workflow 3.0** węzła.  
  
5.  W **Windows Workflow 3.0** węzła **przybornika**, wykonaj jedną z następujących zestawów czynności:  
  
    1.  Otwórz menu skrótów **podczas** działania, a następnie wybierz pozycję **kopiowania**. W Projektancie przepływów pracy, otwórz menu skrótów wiersza w obszarze **onWorkflowActivated1** działania, a następnie wybierz pozycję **Wklej**.  
  
    2.  Przeciągnij **podczas** działania z **przybornika** do projektanta przepływów pracy i nawiązanie połączenia linii w obszarze działania **onWorkflowActivated1** działania.  
  
6.  Wybierz **WhileActivity1** działania.  
  
7.  W **właściwości** ustaw **warunku** do kodu stanu.  
  
8.  Rozwiń węzeł **warunku** właściwości, wprowadź **isWorkflowPending** obok elementu podrzędnego **warunku** właściwości, a następnie wybierz klawisz Enter.  
  
     Zostanie otwarty w edytorze kodu i metodę o nazwie isWorkflowPending są dodawane do pliku kodu Workflow1.  
  
9. Wrócić do projektanta przepływów pracy, otwórz przybornika, a następnie rozwiń węzeł **przepływu pracy SharePoint** węzła.  
  
10. W **przepływu pracy SharePoint** węzła **przybornika**, wykonaj jedną z następujących zestawów czynności:  
  
    -   Otwórz menu skrótów **OnWorkflowItemChanged** działania, a następnie wybierz pozycję **kopiowania**. W Projektancie przepływów pracy, otwórz menu skrótów wiersza wewnątrz **whileActivity1** działania, a następnie wybierz pozycję **Wklej**.  
  
    -   Przeciągnij **OnWorkflowItemChanged** działania z **przybornika** do projektanta przepływów pracy i nawiąż połączenie działania wiersz w **whileActivity1** działania.  
  
11. Wybierz **onWorkflowItemChanged1** działania.  
  
12. W **właściwości** okna, ustaw właściwości, jak pokazano w poniższej tabeli.  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |**CorrelationToken**|**workflowToken**|  
    |**Wywołany**|**onWorkflowItemChanged**|  
  
## <a name="handle-activity-events"></a>Obsługa zdarzeń działania
 Na koniec sprawdź stan dokumentu z każdego działania. Jeśli dokumentu została przejrzana, przepływu pracy zostało zakończone.  
  
#### <a name="to-handle-activity-events"></a>Do obsługi zdarzeń działania  
  
1.  W *Workflow1.cs* lub *Workflow1.vb*, Dodaj następujące pole na początku `Workflow1` klasy. To pole jest używane w działaniu, aby określić, czy przepływ pracy został zakończony.  
  
    ```vb  
    Dim workflowPending As Boolean = True  
    ```  
  
    ```csharp  
    Boolean workflowPending = true;  
    ```  
  
2.  Dodaj następującą metodę do `Workflow1` klasy. Ta metoda sprawdza wartość `Document Status` właściwości listy dokumentów, aby ustalić, czy dokumentu została przejrzana. Jeśli `Document Status` właściwość jest ustawiona na `Review Complete`, a następnie `checkStatus` zestawów — metoda `workflowPending` do **false** aby wskazać, że przepływ pracy jest gotowy do zakończenia.  
  
    ```vb  
    Private Sub checkStatus()  
        If CStr(workflowProperties.Item("Document Status")) = "Review Complete" Then  
            workflowPending = False  
        End If  
    End Sub   
    ```  
  
    ```csharp  
    private void checkStatus()  
    {  
        if ((string)workflowProperties.Item["Document Status"] == "Review Complete")  
        workflowPending = false;  
    }  
    ```  
  
3.  Dodaj następujący kod do `onWorkflowActivated` i `onWorkflowItemChanged` metod do wywołania `checkStatus` metody. Po uruchomieniu przepływu pracy, `onWorkflowActivated` wywołania metody `checkStatus` metodę, aby określić, czy dokument już zostały sprawdzone. Jeśli go nie została sprawdzona, przepływ pracy będzie kontynuowana. Po zapisaniu dokumentu `onWorkflowItemChanged` wywołania metody `checkStatus` metody ponownie, aby określić, czy zostały sprawdzone dokumentu. Gdy `workflowPending` pole jest ustawione na **true**, przepływ pracy będzie kontynuował działanie.  
  
    ```vb  
    Private Sub onWorkflowActivated(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ExternalDataEventArgs)  
        checkStatus()  
    End Sub  
  
    Private Sub onWorkflowItemChanged(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ExternalDataEventArgs)  
        checkStatus()  
    End Sub  
    ```  
  
    ```csharp  
    private void onWorkflowActivated(object sender, ExternalDataEventArgs e)  
    {  
        // Check the status.  
        checkStatus();  
    }  
  
    private void onWorkflowItemChanged(object sender, ExternalDataEventArgs e)  
    {  
        // Check the status.  
        checkStatus();  
    }  
    ```  
  
4.  Dodaj następujący kod do `isWorkflowPending` metodę, aby sprawdzić stan `workflowPending` właściwości. Zawsze zapisywaniu dokumentu **whileActivity1** wywołań działania `isWorkflowPending` metody. Ta metoda sprawdza <xref:System.Workflow.Activities.ConditionalEventArgs.Result%2A> właściwość <xref:System.Workflow.Activities.ConditionalEventArgs> obiektem, aby określić czy **WhileActivity1** działania należy kontynuować, lub Zakończ. Jeśli ustawiono właściwość **true**, działanie będzie kontynuowane. W przeciwnym razie zakończy działanie i zakończeniu przepływu pracy.  
  
    ```vb  
    Private Sub isWorkflowPending(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ConditionalEventArgs)  
        e.Result = workflowPending  
    End Sub  
    ```  
  
    ```csharp  
    private void isWorkflowPending(object sender, ConditionalEventArgs e)  
    {  
        e.Result = workflowPending;  
    }  
    ```  
  
5.  Zapisz projekt.  
  
## <a name="test-the-sharepoint-workflow-template"></a>Testowanie szablonu przepływu pracy programu SharePoint
 Po uruchomieniu debugera, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] szablonu przepływu pracy jest wdrażana na serwerze programu SharePoint i kojarzy przepływu pracy z **dokumenty udostępnione** listy. Aby przetestować przepływ pracy, należy uruchomić wystąpienie przepływu pracy z dokumentu **dokumenty udostępnione** listy.  
  
#### <a name="to-test-the-sharepoint-workflow-template"></a>Aby przetestować szablonu przepływu pracy programu SharePoint  
  
1.  W *Workflow1.cs* lub *Workflow1.vb*, dalej, aby ustawić punkt przerwania **ramach działania onWorkflowActivated** metody.  
  
2.  Wybierz **F5** klawisz, aby skompilować i uruchomić rozwiązanie.  
  
     Zostanie wyświetlona witryna programu SharePoint.  
  
3.  W okienku nawigacji w programie SharePoint, wybierz **dokumenty udostępnione** łącza.  
  
4.  W **dokumenty udostępnione** wybierz pozycję **dokumenty** łącze **narzędzia biblioteki** karcie, a następnie wybierz pozycję **przekazywanie dokumentu** przycisku .  
  
5.  W **przekazywanie dokumentu** oknie dialogowym wybierz **Przeglądaj** przycisku, wybierz dowolny plik dokumentu, wybierz polecenie **Otwórz** przycisk, a następnie wybierz pozycję **OK** przycisku.  
  
     Przekazuje to wybrany dokument do **dokumenty udostępnione** listy i uruchamia przepływ pracy.  
  
6.  W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], sprawdź, czy debuger zatrzymuje się na punkt przerwania obok `onWorkflowActivated` metody.  
  
7.  Wybierz **F5** klawisz, aby kontynuować działanie.  
  
8.  Zmienianie ustawień w tym miejscu dokument, ale pozostaw je w wartości domyślne dla teraz, wybierając **zapisać** przycisku.  
  
     Nastąpi powrót do **dokumenty udostępnione** stronę domyślną witryną sieci Web programu SharePoint.  
  
9. W **dokumenty udostępnione** Sprawdź, czy wartość poniżej **MySharePointWorkflow - Workflow1** kolumny ustawiono **w toku**. Oznacza to, że przepływ pracy jest w toku i że dokument oczekuje przeglądu.  
  
10. W **dokumenty udostępnione** , wybierz dokument, wybierz strzałkę, która jest wyświetlana, a następnie wybierz **Edytuj właściwości** elementu menu.  
  
11. Ustaw **stan dokumentu** do **pełny przegląd**, a następnie wybierz pozycję **zapisać** przycisku.  
  
     Nastąpi powrót do **dokumenty udostępnione** stronę domyślną witryną sieci Web programu SharePoint.  
  
12. W **dokumenty udostępnione** Sprawdź, czy wartość poniżej **stan dokumentu** kolumny ustawiono **pełny przegląd**. Odśwież **dokumenty udostępnione** strony i sprawdź, czy wartość poniżej **MySharePointWorkflow - Workflow1** kolumny ustawiono **Ukończono**. Oznacza to, że przepływ pracy został zakończony i dokumentu została przejrzana.  
  
## <a name="next-steps"></a>Następne kroki
 Można poznać więcej informacji na temat sposobu tworzenia szablonów przepływu pracy z tych tematów:  
  
-   Aby dowiedzieć się więcej na temat działania przepływu pracy programu SharePoint, zobacz [działania przepływu pracy programu SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=178992).  
  
-   Aby dowiedzieć się więcej na temat działania Windows Workflow Foundation, zobacz [Namespace System.Workflow.Activities](http://go.microsoft.com/fwlink/?LinkId=178993).  
  
## <a name="see-also"></a>Zobacz także
 [Tworzenie rozwiązań przepływu pracy programu SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [Projekt SharePoint oraz szablony elementów projektu](../sharepoint/sharepoint-project-and-project-item-templates.md)   
 [Kompilowanie i debugowanie rozwiązań SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
