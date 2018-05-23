---
title: 'Wskazówki: Tworzenie przepływu pracy z formularzami inicjacji i skojarzenia | Dokumentacja firmy Microsoft'
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
- SharePoint development in Visual Studio, workflows
- SharePoint development in Visual Studio, workflow association forms
- workflows [SharePoint development in Visual Studio]
- association forms [SharePoint development in Visual Studio]
- initiation forms [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, workflow initiation forms
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0c232d541e985944fe64d9eb40da7e344b32c0cc
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
---
# <a name="walkthrough-creating-a-workflow-with-association-and-initiation-forms"></a>Wskazówki: tworzenie i przepływu pracy z formularzami inicjacji i skojarzenia
  Ten przewodnik przedstawia sposób tworzenia podstawowych sekwencyjnego przepływu pracy, uwzględniająca stosowanie formularzy skojarzenia i inicjowania. Są to formularzy ASPX, umożliwiających parametrów, które mają zostać dodane do przepływu pracy, gdy najpierw została skojarzona przez administratora programu SharePoint (formularz skojarzenia), a po uruchomieniu przepływu pracy przez użytkownika (formularza inicjowania).  
  
 W tym przewodniku opisano scenariusz, w których użytkownik chce, aby utworzyć przepływ zatwierdzenia w raportach wydatków, który ma następujące wymagania:  
  
-   Gdy przepływ pracy jest skojarzony z listy, administrator zostanie poproszony o formularz skojarzenia, w którym oni wprowadzić limit dolara w raportach wydatków.  
  
-   Pracownicy przekazać swoje raporty wydatków do listy Dokumenty udostępnione, uruchomić przepływ pracy, a następnie wprowadź koszt całkowity w formularza inicjowania przepływu pracy.  
  
-   Jeśli raport wydatków pracownika całkowitej przekracza limit wstępnie zdefiniowanych administratora, zadanie jest tworzone dla Menedżera pracownika do zatwierdzenia raportu wydatków. Jednak jeśli całkowita liczba raportów wydatków pracownika jest mniejsze niż lub równe limit wydatków, na liście historii przepływu pracy jest zapisywany komunikat automatycznie zatwierdzone.  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Tworzenie projektu SharePoint listy definicji sekwencyjnego przepływu pracy w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   Tworzenie harmonogramu przepływu pracy.  
  
-   Obsługa zdarzeń działania przepływu pracy.  
  
-   Tworzenie formularzy skojarzenia i inicjowania przepływu pracy.  
  
-   Kojarzenie przepływu pracy.  
  
-   Ręczne uruchamianie przepływu pracy.  
  
> [!NOTE]  
>  Mimo że w tym przewodniku zastosowano projektu sekwencyjnego przepływu pracy, proces jest taka sama dla przepływów pracy komputera stanu.  
>   
>  Ponadto komputer mogą być wyświetlane inne nazwy i lokalizacje niektórych [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] elementy interfejsu użytkownika w poniższych instrukcjach. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Te elementy są określane w wersji i ustawienia, których używasz. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   Obsługiwane wersje programu [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] i programu SharePoint. Aby uzyskać więcej informacji, zobacz [wymagania dotyczące opracowywania rozwiązań SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Program Visual Studio.  
  
## <a name="creating-a-sharepoint-sequential-workflow-project"></a>Tworzenie projektu sekwencyjnego przepływu pracy programu SharePoint  
 Najpierw utwórz projekt sekwencyjnego przepływu pracy w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Sekwencyjny przepływ pracy jest pewne czynności wykonywane w kolejności Zakończenie ostatniej aktywności. W tej procedurze utworzysz sekwencyjnego przepływu pracy, która ma zastosowanie do listy dokumentów udostępnionych w programie SharePoint. Kreator przepływu pracy można skojarzyć przepływu pracy z poziomu lokacji lub definicji listy i pozwala określić, gdy zostanie uruchomiony przepływ pracy.  
  
#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>Aby utworzyć projekt sekwencyjnego przepływu pracy programu SharePoint  
  
1.  Na pasku menu wybierz **pliku**, **nowy**, **projektu** do wyświetlenia **nowy projekt** okno dialogowe.  
  
2.  Rozwiń węzeł **SharePoint** węźle albo **Visual C#** lub **Visual Basic**, a następnie wybierz pozycję **2010** węzła.  
  
3.  W **szablony** okienku wybierz **projektu programu SharePoint 2010** szablonu projektu.  
  
4.  W **nazwa** wprowadź **ExpenseReport** , a następnie wybierz **OK** przycisku.  
  
     **Kreator dostosowania programu SharePoint** pojawi się.  
  
5.  W **określić poziom lokacji i zabezpieczeń dla debugowania** wybierz pozycję **Wdróż jako rozwiązanie farmy** przycisk opcji, a następnie wybierz pozycję **Zakończ** przycisk, aby zaakceptować poziom i domyślne witryny zaufania.  
  
     Ten krok ustawi poziom zaufania dla rozwiązania farmy rozwiązania, które jest jedyną dostępną opcją dla projektów przepływu pracy.  
  
6.  W **Eksploratora rozwiązań**, wybierz węzeł projektu.  
  
7.  Na pasku menu wybierz **projektu**, **Dodaj nowy element**.  
  
8.  Pod **Visual C#** lub **Visual Basic**, rozwiń węzeł **SharePoint** węzeł, a następnie wybierz pozycję **2010** węzła.  
  
9. W **szablony** okienku wybierz **sekwencyjnego przepływu pracy (tylko rozwiązanie farmy)** szablonu, a następnie wybierz pozycję **Dodaj** przycisku.  
  
     **Kreator dostosowania programu SharePoint** pojawi się.  
  
10. W **Określ nazwę przepływu pracy do debugowania** pozycję Zaakceptuj nazwę domyślną (**ExpenseReport - Workflow1**). Należy zachować wartość typu szablonu domyślnego przepływu pracy (**przepływu pracy)**. Wybierz **dalej** przycisku.  
  
11. W **czy program Visual Studio ma automatycznie skojarzyć przepływ pracy w sesji debugowania?** Usuń zaznaczenie pola, które automatycznie kojarzy szablonu przepływu pracy, jeżeli jest ono zaznaczone.  
  
     Ten krok pozwala ręcznie skojarzenia przepływu pracy z później na liście dokumenty udostępnione, które wyświetla formularz skojarzenia.  
  
12. Wybierz **Zakończ** przycisku.  
  
## <a name="adding-an-association-form-to-the-workflow"></a>Dodawanie formularz skojarzenia przepływu pracy  
 Następnie należy utworzyć. Formularz skojarzenia ASPX, który jest wyświetlany, gdy administrator programu SharePoint najpierw kojarzy przepływu pracy z dokumentu raportu wydatków.  
  
#### <a name="to-add-an-association-form-to-the-workflow"></a>Aby dodać formularz skojarzenia przepływu pracy  
  
1.  Wybierz **Workflow1** w węźle **Eksploratora rozwiązań**.  
  
2.  Na pasku menu wybierz **projektu**, **Dodaj nowy element** do wyświetlenia **Dodaj nowy element** okno dialogowe.  
  
3.  W widoku drzewa — okno dialogowe, rozwiń **Visual C#** lub **Visual Basic** (w zależności od język projektu), rozwiń węzeł **SharePoint** węzeł, a następnie wybierz pozycję **2010** węzła.  
  
4.  Na liście szablonów wybierz **formularz skojarzenia przepływu pracy** szablonu.  
  
5.  W **nazwa** tekst wprowadź **ExpenseReportAssocForm.aspx**.  
  
6.  Wybierz **Dodaj** przycisk, aby dodać formularza do projektu.  
  
## <a name="designing-and-coding-the-association-form"></a>Projektowanie i kodowania formularz skojarzenia  
 W tej procedurze funkcji formularza skojarzenia wprowadzania przez dodanie do niej formanty i kod.  
  
#### <a name="to-design-and-code-the-association-form"></a>Do projektu i kodu formularz skojarzenia  
  
1.  Formularz skojarzenia (ExpenseReportAssocForm.aspx), odszukaj `asp:Content` element, który ma `ID="Main"`.  
  
2.  Bezpośrednio po pierwszym wierszu w tym elemencie content, Dodaj następujący kod do tworzenia etykiety i pola tekstowego, który wyświetla monit o zatwierdzenie limit wydatków (*AutoApproveLimit*):  
  
    ```aspx-csharp  
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />  
  
    <asp:TextBox ID="AutoApproveLimit" runat="server" />  
    <br /><br />  
    ```  
  
3.  Rozwiń węzeł **ExpenseReportAssocForm.aspx** w pliku **Eksploratora rozwiązań** Aby wyświetlić jego plików zależnych.  
  
    > [!NOTE]  
    >  Jeśli Twój projekt jest w [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)], musisz wybrać **widoku wszystkie pliki** przycisk, aby wykonać ten krok.  
  
4.  Otwórz plik ExpenseReportAssocForm.aspx menu skrótów i wybierz polecenie **kod widoku**.  
  
5.  Zastąp `GetAssociationData` metody za pomocą:  
  
    ```vb  
    Private Function GetAssociationData() As String  
        ' TODO: Return a string that contains the association data that   
        ' will be passed to the workflow. Typically, this is in XML   
        ' format.  
        Return Me.AutoApproveLimit.Text  
    End Function  
    ```  
  
    ```csharp  
    private string GetAssociationData()  
    {  
        // TODO: Return a string that contains the association data that   
        // will be passed to the workflow. Typically, this is in XML   
        // format.  
        return this.AutoApproveLimit.Text;  
    }  
    ```  
  
## <a name="adding-an-initiation-form-to-the-workflow"></a>Dodawanie formularza inicjowania przepływu pracy  
 Następnie należy utworzyć formularza inicjowania wyświetlany, jeśli użytkownicy uruchamiają przepływ pracy przed ich raporty wydatków.  
  
#### <a name="to-create-an-initiation-form"></a>Aby utworzyć formularza inicjowania  
  
1.  Wybierz **Workflow1** w węźle **Eksploratora rozwiązań**.  
  
2.  Na pasku menu wybierz **projektu**, **Dodaj nowy element** wyświetlić **Dodaj nowy element** okno dialogowe.  
  
3.  W widoku drzewa — okno dialogowe, rozwiń **Visual C#** lub **Visual Basic** (w zależności od język projektu), rozwiń węzeł **SharePoint** węzeł, a następnie wybierz pozycję **2010** węzła.  
  
4.  Na liście szablonów wybierz **formularza inicjowania przepływu pracy** szablonu.  
  
5.  W **nazwa** tekst wprowadź **ExpenseReportInitForm.aspx**.  
  
6.  Wybierz **Dodaj** przycisk, aby dodać formularza do projektu.  
  
## <a name="designing-and-coding-the-initiation-form"></a>Projektowanie i kodowania formularza inicjowania  
 Następnie wprowadzić funkcje do formularza inicjowania przez dodanie do niej formanty i kod.  
  
#### <a name="to-code-the-initiation-form"></a>Do kodu formularza inicjowania  
  
1.  Formularz inicjowania (ExpenseReportInitForm.aspx), odszukaj `asp:Content` element, który zawiera `ID="Main"`.  
  
2.  Bezpośrednio po pierwszym wierszu w tym elemencie content, Dodaj następujący kod do tworzenia etykiety i pola tekstowego, wyświetlająca limit wydatków zatwierdzenia (*AutoApproveLimit*) wprowadzone w formularzu skojarzenia i inną etykietę i pole tekstowe z monitem o łączny koszt (*ExpenseTotal*):  
  
    ```aspx-csharp  
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />  
  
    <asp:TextBox ID="AutoApproveLimit" ReadOnly="true" runat="server" />  
    <br /><br />  
    <asp:Label ID="lblExpenseTotal" Text="Expense Total:" runat="server" />  
  
    <asp:TextBox ID="ExpenseTotal" runat="server" />  
    <br /><br />  
    ```  
  
3.  Rozwiń węzeł **ExpenseReportInitForm.aspx** w pliku **Eksploratora rozwiązań** Aby wyświetlić jego plików zależnych.  
  
4.  Otwórz plik ExpenseReportInitForm.aspx menu skrótów i wybierz polecenie **kod widoku**.  
  
5.  Zastąp `Page_Load` metodę z następującym przykładzie:  
  
    ```vb  
    Protected Sub Page_Load(ByVal sender As Object, ByVal e As   
      EventArgs) Handles Me.Load  
        InitializeParams()  
        Me.AutoApproveLimit.Text = workflowList.WorkflowAssociations(New   
          Guid(associationGuid)).AssociationData  
        ' Optionally, add code here to pre-populate your form fields.  
    End Sub  
    ```  
  
    ```csharp  
    protected void Page_Load(object sender, EventArgs e)  
    {  
        InitializeParams();  
        this.AutoApproveLimit.Text =   
          workflowList.WorkflowAssociations[new   
          Guid(associationGuid)].AssociationData;  
    }  
    ```  
  
6.  Zastąp `GetInitiationData` metodę z następującym przykładzie:  
  
    ```vb  
    ' This method is called when the user clicks the button to start the workflow.  
    Private Function GetInitiationData() As String  
        Return Me.ExpenseTotal.Text  
        ' TODO: Return a string that contains the initiation data that   
        ' will be passed to the workflow. Typically, this is in XML   
        ' format.  
        Return String.Empty  
    End Function  
    ```  
  
    ```csharp  
    // This method is called when the user clicks the button to start the workflow.          
    private string GetInitiationData()  
    {  
        // TODO: Return a string that contains the initiation data that   
        // will be passed to the workflow. Typically, this is in XML   
        // format.  
        return this.ExpenseTotal.Text;  
    }  
    ```  
  
## <a name="customizing-the-workflow"></a>Dostosowywanie przepływu pracy  
 Następnie można dostosować przepływ pracy. Później zostanie skojarzony dwa formularze do przepływu pracy.  
  
#### <a name="to-customize-the-workflow"></a>Aby dostosować przepływu pracy  
  
1.  Wyświetlanie przepływu pracy w Projektancie przepływów pracy, otwierając Workflow1 w projekcie.  
  
2.  W **przybornika**, rozwiń węzeł **Windows Workflow 3.0** węzła i Znajdź **Jeślilub** działania.  
  
3.  Dodaj to działanie w przepływie pracy, wykonując jedną z następujących czynności:  
  
    -   Otwórz menu skrótów **Jeślilub** działania, wybierz **kopiowania**, otwórz menu skrótów wiersza w obszarze **onWorkflowActivated1** działania w Projektancie przepływów pracy a następnie wybierz **Wklej**.  
  
    -   Przeciągnij **Jeślilub** działania z **przybornika**i podłącz go do nowego wiersza w obszarze **onWorkflowActiviated1** działania w Projektancie przepływów pracy.  
  
4.  W przyborniku rozwiń **przepływu pracy SharePoint** węzła i Znajdź **CreateTask** działania.  
  
5.  Dodaj to działanie w przepływie pracy, wykonując jedną z następujących czynności:  
  
    -   Otwórz menu skrótów **CreateTask** działania, wybierz **kopiowania**, otwórz menu skrótów dla jednej z dwóch **Upuść działania w tym miejscu** obszarów  **IfElseActivity1** w Projektancie przepływów pracy, a następnie wybierz pozycję **Wklej**.  
  
    -   Przeciągnij **CreateTask** działania z **przybornika** na jedną z dwóch **Upuść działania w tym miejscu** obszarów **IfElseActivity1**.  
  
6.  W **właściwości** okna, wprowadź wartość właściwości *taskToken* dla **CorrelationToken** właściwości.  
  
7.  Rozwiń węzeł **CorrelationToken** właściwości, wybierając znak plus (![TreeView plus](../sharepoint/media/plus.gif "TreeView plus")) obok niej.  
  
8.  Wybierz strzałkę listy rozwijanej na **OwnerActivityName** sub właściwości i ustaw *Workflow1* wartości.  
  
9. Wybierz **TaskId** właściwości, a następnie wybierz przycisk wielokropka (![elipsy ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "elipsy ASP.NET Mobile Designer")) przycisk, aby wyświetlić **Powiązać właściwość** okno dialogowe.  
  
10. Wybierz **Dowiąż do nowego członka** , wybierz pozycję **utworzyć pole** przycisk opcji, a następnie wybierz pozycję **OK** przycisku.  
  
11. Wybierz **TaskProperties** właściwości, a następnie wybierz przycisk wielokropka (![elipsy ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "elipsy ASP.NET Mobile Designer")) przycisk, aby wyświetlić  **Dowiąż właściwość** okno dialogowe.  
  
12. Wybierz **Dowiąż do nowego członka** , wybierz pozycję **utworzyć pole** przycisk opcji, a następnie wybierz pozycję **OK** przycisku.  
  
13. W **przybornika**, rozwiń węzeł **przepływu pracy programu SharePoint** węzła, a następnie zlokalizuj **LogToHistoryListActivity** działania.  
  
14. Dodaj to działanie w przepływie pracy, wykonując jedną z następujących czynności:  
  
    -   Otwórz menu skrótów **LogToHistoryListActivity** działania, wybierz **kopiowania**, otwórz menu skrótów dla siebie **Upuść działania w tym miejscu** obszar wewnątrz **IfElseActivity1** w Projektancie przepływów pracy, a następnie wybierz pozycję **Wklej**.  
  
    -   Przeciągnij **LogToHistoryListActivity** działania z **przybornika**i upuść ją na innych **Upuść działania w tym miejscu** obszar wewnątrz **IfElseActivity1** .  
  
## <a name="adding-code-to-the-workflow"></a>Dodawanie kodu do przepływu pracy  
 Następnie dodaj kod do przepływu pracy, aby nadać jej funkcji.  
  
#### <a name="to-add-code-to-the-workflow"></a>Aby dodać kod do przepływu pracy  
  
1.  Otwórz menu skrótów **createTask1** działania w Projektancie przepływów pracy, a następnie wybierz pozycję **kod widoku**.  
  
2.  Dodaj następującą metodę:  
  
    ```vb  
    Private Sub createTask1_MethodInvoking(ByVal sender As   
      System.Object, ByVal e As System.EventArgs)  
        createTask1_TaskId1 = Guid.NewGuid  
        createTask1_TaskProperties1.AssignedTo = "somedomain\\someuser"  
        createTask1_TaskProperties1.Description = "Please approve the   
          expense report"  
        createTask1_TaskProperties1.Title = "Expense Report Approval   
          Needed"  
    End Sub   
    ```  
  
    ```csharp  
    private void createTask1_MethodInvoking(object sender, EventArgs e)  
    {  
        createTask1_TaskId1 = Guid.NewGuid();  
        createTask1_TaskProperties1.AssignedTo = "somedomain\\someuser";  
        createTask1_TaskProperties1.Description = "Please approve the   
          expense report";  
        createTask1_TaskProperties1.Title = "Expense Report Approval   
          Needed";  
    }   
    ```  
  
    > [!NOTE]  
    >  W kodzie, Zastąp `somedomain\\someuser` z nazwą domeny i użytkownika, dla której zostanie utworzone zadanie, takie jak "`Office\\JoeSch`". Do testowania najłatwiej pod kątem używania konta, które tworzysz z.  
  
3.  Poniżej `MethodInvoking` metody, Dodaj następujący przykład:  
  
    ```vb  
    Private Sub checkApprovalNeeded(ByVal sender As Object, ByVal e As   
      ConditionalEventArgs)  
        Dim approval As Boolean = False  
        If (Convert.ToInt32(workflowProperties.InitiationData) >   
          Convert.ToInt32(workflowProperties.AssociationData)) Then  
            approval = True  
        End If  
        e.Result = approval  
    End Sub   
    ```  
  
    ```csharp  
    private void checkApprovalNeeded(object sender, ConditionalEventArgs   
      e)  
    {  
        bool approval = false;  
        if (Convert.ToInt32(workflowProperties.InitiationData) >   
          Convert.ToInt32(workflowProperties.AssociationData))  
        {  
            approval = true;  
        }  
        e.Result = approval;  
    }   
    ```  
  
4.  W Projektancie przepływów pracy, wybierz **ifElseBranchActivity1** działania.  
  
5.  W **właściwości** okna, wybierz strzałkę listy rozwijanej **warunku** właściwości, a następnie ustawić *kodu warunku* wartość.  
  
6.  Rozwiń węzeł **warunku** właściwości, wybierając znak plus (![TreeView plus](../sharepoint/media/plus.gif "TreeView plus")) obok niej, a następnie ustaw dla niego wartość *checkApprovalNeeded* .  
  
7.  W Projektancie przepływów pracy, otwórz menu skrótów **logToHistoryListActivity1** działania, a następnie wybierz **Generowanie obsługi** do generowania pustą metodę `MethodInvoking` zdarzeń.  
  
8.  Zastąp `MethodInvoking` kod następującym kodem:  
  
    ```vb  
    Private Sub logToHistoryListActivity1_MethodInvoking(ByVal sender As   
      System.Object, ByVal e As System.EventArgs)  
        Me.logToHistoryListActivity1.HistoryOutcome = ("Expense was auto   
          approved for " + workflowProperties.InitiationData)  
    End Sub   
    ```  
  
    ```csharp  
    private void logToHistoryListActivity1_MethodInvoking(object sender,   
      EventArgs e)  
    {  
        this.logToHistoryListActivity1.HistoryOutcome = "Expense was   
          auto approved for " + workflowProperties.InitiationData;  
    }   
    ```  
  
9. Wybierz klawisz F5, aby zdebugować program.  
  
     Kompiluje aplikacji, pakietów go, wdraża ją, aktywuje jej funkcje, jest odtwarzana [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] puli aplikacji, a następnie uruchamia przeglądarki w lokalizacji określonej w **adres Url witryny** właściwości.  
  
## <a name="associating-the-workflow-to-the-documents-list"></a>Kojarzenie przepływu pracy do listy dokumentów  
 Następnie Wyświetl formularz skojarzenia przepływu pracy można skojarzyć przepływu pracy z **SharedDocuments** listy w witrynie programu SharePoint.  
  
#### <a name="to-associate-the-workflow"></a>Aby skojarzyć przepływu pracy  
  
1.  Wybierz **dokumenty udostępnione** łącze na pasek szybkiego uruchamiania.  
  
2.  Wybierz **biblioteki** łącze **narzędzia biblioteki** karcie, a następnie wybierz pozycję **ustawienia biblioteki** przycisk wstążki.  
  
3.  W **uprawnienia i zarządzanie** wybierz **ustawienia przepływu pracy** łącza, a następnie wybierz pozycję **Dodaj przepływ pracy** łącze **przepływypracy** strony.  
  
4.  Górnej liście na stronie ustawień przepływu pracy, wybierz **ExpenseReport - Workflow1** szablonu.  
  
5.  Wprowadź w polu dalej **ExpenseReportWorkflow** , a następnie wybierz **dalej** przycisku.  
  
     Skojarzenie przepływu pracy z **dokumenty udostępnione** listy i wyświetla formularz skojarzenia przepływu pracy.  
  
6.  W **automatycznego zatwierdzania Limit** tekst wprowadź **1200** , a następnie wybierz **skojarzenia przepływu pracy** przycisku.  
  
## <a name="starting-the-workflow"></a>Uruchamianie przepływu pracy  
 Następnie skojarzenia przepływu pracy do jednego z dokumentów w **dokumenty udostępnione** listy, aby wyświetlić formularza inicjowania przepływu pracy.  
  
#### <a name="to-start-the-workflow"></a>Aby uruchomić przepływ pracy  
  
1.  Na stronie programu SharePoint, wybierz **Home** przycisku.  
  
2.  Wybierz **dokumenty udostępnione** łącze na pasek szybkiego uruchamiania, aby wyświetlić **dokumenty udostępnione** listy.  
  
3.  Wybierz **dokumenty** łącze **narzędzia biblioteki** w górnej części strony, a następnie wybierz pozycję **przekazywanie dokumentu** na Wstążce, aby przekazać nowy dokument do **Dokumenty udostępnione** listy.  
  
4.  W **przekazywanie dokumentu** oknie dialogowym wybierz **Przeglądaj** przycisku, wybierz dowolny plik dokumentu, wybierz polecenie **Otwórz** przycisk, a następnie wybierz pozycję **OK** przycisku.  
  
     Zmień ustawienia dla dokumentu w tym oknie dialogowym, ale pozostaw je na wartości domyślne, wybierając **zapisać** przycisku.  
  
5.  Wybieranie przekazanego dokumentu, strzałkę listy rozwijanej, która jest wyświetlana, a następnie wybierz **przepływy pracy** elementu.  
  
6.  Wybierz obraz obok ExpenseReportWorkflow.  
  
     Spowoduje to wyświetlenie formularza inicjowania przepływu pracy. (Należy pamiętać, że wartość wyświetlana w **automatycznego zatwierdzania Limit** pole jest tylko do odczytu, ponieważ został wprowadzony w formularzu skojarzenia.)  
  
7.  W **całkowity koszt** tekst wprowadź **1600**, a następnie wybierz pozycję **Uruchom przepływ pracy** przycisku.  
  
     Spowoduje to wyświetlenie **dokumenty udostępnione** ponownie. Nową kolumnę o nazwie **ExpenseReportWorkflow** z wartością **Ukończono** zostanie dodany do elementu właśnie został uruchomiony przepływ pracy.  
  
8.  Wybierz strzałkę listy rozwijanej obok przekazanego dokumentu, a następnie wybierz **przepływy pracy** element, aby wyświetlić na stronie stanu przepływu pracy. Wybierz **Ukończono** wartości w obszarze **ukończone przepływy pracy**. Zadanie jest wyświetlana w obszarze **zadania** sekcji.  
  
9. Wybierz tytuł zadanie, aby wyświetlić jego szczegóły zadania.  
  
10. Wróć do **SharedDocuments** listę i ponownie uruchomić przepływ pracy, przy użyciu tego samego dokumentu lub innej.  
  
11. Wprowadź kwotę na stronie inicjowania, która jest mniejsza niż wielkość wprowadzone na stronie skojarzenia (**1200**).  
  
     W takim przypadku wpis na liście historii jest tworzony zamiast zadania. Wyświetla wpis **historii przepływu pracy** części strony stanu przepływu pracy. Należy pamiętać, wiadomości w **wynik** kolumny zdarzenia historii. Zawiera on tekst wprowadzony w `logToHistoryListActivity1.MethodInvoking` zdarzeń, która zawiera wartość, które zostało automatycznie zatwierdzone.  
  
## <a name="next-steps"></a>Następne kroki  
 Można poznać więcej informacji na temat sposobu tworzenia szablonów przepływu pracy z tych tematów:  
  
-   Aby dowiedzieć się więcej na temat przepływów pracy programu SharePoint, zobacz [przepływów pracy programu Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkID=166275).  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie rozwiązań przepływu pracy programu SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [Przewodnik: Dodawanie strony aplikacji do przepływu pracy](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)  
  
  