---
title: "Wskazówki: Dodawanie strony aplikacji do przepływu pracy | Dokumentacja firmy Microsoft"
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
- SharePoint development in Visual Studio, adding applications page to workflow
- application page [SharePoint development in Visual Studio]
ms.assetid: e4845d07-917b-45cb-a569-4ecdd602fbd9
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 67ee77197493cbba0161a3ee53a0617a58b62522
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-add-an-application-page-to-a-workflow"></a>Wskazówki: dodawanie strony aplikacji do przepływu pracy
  W tym przewodniku przedstawiono sposób dodawania strony aplikacji, który wyświetla dane pochodzące z przepływu pracy do projektu przepływu pracy. Opiera się na projekcie opisane w temacie [wskazówki: Tworzenie przepływu pracy z formularzami inicjacji i skojarzenia](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).  
  
 W tym przewodniku przedstawiono następujące zadania:  
  
-   Dodawanie strony ASPX aplikacji do projektu przepływu pracy programu SharePoint.  
  
-   Uzyskiwanie danych z projektu przepływu pracy i operowanie nimi go.  
  
-   Wyświetlanie danych w tabeli na stronie aplikacji.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   Obsługiwane wersje programu [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] i programu SharePoint. Aby uzyskać więcej informacji, zobacz [wymagania dotyczące opracowywania rozwiązań SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Program Visual Studio.  
  
-   Musisz także wypełnić projektu w temacie [wskazówki: Tworzenie przepływu pracy z formularzami inicjacji i skojarzenia](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).  
  
## <a name="amending-the-workflow-code"></a>Zmieniające kodu przepływu pracy  
 Najpierw dodaj wiersz kodu do przepływu pracy można ustawić wartości w kolumnie Wynik ilości raportu wydatków. Ta wartość jest używana później podczas obliczania podsumowania raportu wydatków.  
  
#### <a name="to-set-the-value-of-the-outcome-column-in-the-workflow"></a>Aby ustawić wartość kolumny wyników w przepływie pracy  
  
1.  Załadowanie projektu zakończone z tematu [wskazówki: Tworzenie przepływu pracy z formularzami inicjacji i skojarzenia](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Otwórz kod Workflow1.cs lub Workflow1.vb (w zależności od języka programowania).  
  
3.  Na koniec `createTask1_MethodInvoking` metody, Dodaj następujący kod:  
  
    ```vb  
    createTask1_TaskProperties1.ExtendedProperties("Outcome") =   
      workflowProperties.InitiationData  
    ```  
  
    ```csharp  
    createTask1_TaskProperties1.ExtendedProperties["Outcome"] =   
      workflowProperties.InitiationData;  
    ```  
  
## <a name="creating-an-application-page"></a>Tworzenie strony aplikacji  
 Następnie dodaj ASPX formularza do projektu. Ten formularz spowoduje wyświetlenie danych uzyskanych z projektu przepływu pracy raportu wydatków. Aby to zrobić, zostaną dodane strony aplikacji. Strony aplikacji używa tej samej strony wzorcowej jako inne strony programu SharePoint, co oznacza, że będzie podobny innych stron w witrynie programu SharePoint.  
  
#### <a name="to-add-an-application-page-to-the-project"></a>Aby dodać strony aplikacji do projektu  
  
1.  Wybierz projekt ExpenseReport, a następnie na pasku menu wybierz **projektu**, **Dodaj nowy element**.  
  
2.  W **szablony** okienku wybierz **strony aplikacji** szablon, użyj nazwy domyślnej dla elementu projektu (**ApplicaitonPage1.aspx**) i wybierz polecenie **Dodaj** przycisku.  
  
3.  W [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] z ApplicationPage1.aspx, Zastąp `PlaceHolderMain` sekcji z następujących czynności:  
  
    ```  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
        <asp:Label ID="Label1" runat="server" Font-Bold="True"   
            Text="Expenses that exceeded allotted amount" Font-Size="Medium"></asp:Label>  
        <br />  
        <asp:Table ID="Table1" runat="server">  
        </asp:Table>  
    </asp:Content>  
    ```  
  
     Ten kod dodaje tabelę do strony wraz z tytułu.  
  
4.  Dodawanie tytułu do strony aplikacji przez zastąpienie `PlaceHolderPageTitleInTitleArea` sekcji z następujących czynności:  
  
    ```  
    <asp:Content ID="PageTitleInTitleArea" ContentPlaceHolderID="PlaceHolderPageTitleInTitleArea" runat="server" >  
        Expense Report Summary  
    </asp:Content>  
    ```  
  
## <a name="coding-the-application-page"></a>Kodowanie strony aplikacji  
 Następnie dodaj kod, aby strona podsumowania aplikacji raportu wydatków. Po otwarciu strony kod skanuje listy zadań w programie SharePoint wydatków przekraczające przydzielonego limitu wydatków. Raport zawiera listę poszczególnych elementów wraz z sumą kosztów.  
  
#### <a name="to-code-the-application-page"></a>Do kodu strony aplikacji  
  
1.  Wybierz **ApplicationPage1.aspx** węzeł, a następnie na pasku menu wybierz **widoku**, **kod** do wyświetlenia w kodzie strony aplikacji.  
  
2.  Zastąp **przy użyciu** lub **importu** instrukcje (w zależności od języka programowania) u góry klasy następującym kodem:  
  
    ```vb  
    Imports System  
    Imports Microsoft.SharePoint  
    Imports Microsoft.SharePoint.WebControls  
    Imports System.Collections  
    Imports System.Data  
    Imports System.Web.UI  
    Imports System.Web.UI.WebControls  
    Imports System.Web.UI.WebControls.WebParts  
    Imports System.Drawing  
    Imports Microsoft.SharePoint.Navigation  
    ```  
  
    ```csharp  
    using System;  
    using Microsoft.SharePoint;  
    using Microsoft.SharePoint.WebControls;  
    using System.Collections;  
    using System.Data;  
    using System.Web.UI;  
    using System.Web.UI.WebControls;  
    using System.Web.UI.WebControls.WebParts;  
    using System.Drawing;  
    using Microsoft.SharePoint.Navigation;  
    ```  
  
3.  Dodaj następujący kod do `Page_Load` metody:  
  
    ```vb  
    Try  
        ' Reference the Tasks list on the SharePoint site.  
        ' Replace "TestServer" with a valid SharePoint server name.  
        Dim site As SPSite = New SPSite("http://TestServer")  
        Dim list As SPList = site.AllWebs(0).Lists("Tasks")  
        ' string text = "";  
        Dim sum As Integer = 0  
        Table1.Rows.Clear()  
        ' Add table headers.  
        Dim hr As TableHeaderRow = New TableHeaderRow  
        hr.BackColor = Color.LightBlue  
        Dim hc1 As TableHeaderCell = New TableHeaderCell  
        Dim hc2 As TableHeaderCell = New TableHeaderCell  
        hc1.Text = "Expense Report Name"  
        hc2.Text = "Amount Exceeded"  
        hr.Cells.Add(hc1)  
        hr.Cells.Add(hc2)  
        ' Add the TableHeaderRow as the first item   
        ' in the Rows collection of the table.  
        Table1.Rows.AddAt(0, hr)  
        ' Iterate through the tasks in the Task list and collect those    
        ' that have values in the "Related Content" and "Outcome" fields   
        ' - the fields written to when expense approval is required.  
        For Each item As SPListItem In list.Items  
            Dim s_relContent As String = ""  
            Dim s_outcome As String = ""  
            Try  
                ' Task has the fields - treat as expense report.  
                s_relContent = item.GetFormattedValue("Related Content")  
                s_outcome = item.GetFormattedValue("Outcome")  
            Catch erx As System.Exception  
                ' Task does not have fields - skip it.  
                Continue For  
            End Try  
            ' Convert amount to an int and keep a running total.  
            If (Not String.IsNullOrEmpty(s_relContent) And Not   
              String.IsNullOrEmpty(s_outcome)) Then  
                sum = (sum + Convert.ToInt32(s_outcome))  
                Dim relContent As TableCell = New TableCell  
                relContent.Text = s_relContent  
                Dim outcome As TableCell = New TableCell  
                outcome.Text = ("$" + s_outcome)  
                Dim dataRow2 As TableRow = New TableRow  
                dataRow2.Cells.Add(relContent)  
                dataRow2.Cells.Add(outcome)  
                Table1.Rows.Add(dataRow2)  
            End If  
        Next  
        ' Report the sum of the reports in the table footer.  
        Dim tfr As TableFooterRow = New TableFooterRow  
        tfr.BackColor = Color.LightGreen  
        ' Create a TableCell object to contain the   
        ' text for the footer.  
        Dim ftc1 As TableCell = New TableCell  
        Dim ftc2 As TableCell = New TableCell  
        ftc1.Text = "TOTAL: "  
        ftc2.Text = ("$" + Convert.ToString(sum))  
        ' Add the TableCell object to the Cells  
        ' collection of the TableFooterRow.  
        tfr.Cells.Add(ftc1)  
        tfr.Cells.Add(ftc2)  
        ' Add the TableFooterRow to the Rows  
        ' collection of the table.  
        Table1.Rows.Add(tfr)  
    Catch errx As Exception  
        System.Diagnostics.Debug.WriteLine(("Error: " + errx.ToString))  
    End Try  
    ```  
  
    ```csharp  
    try  
    {  
        // Reference the Tasks list on the SharePoint site.  
        // Replace "TestServer" with a valid SharePoint server name.  
        SPSite site = new SPSite("http://TestServer");  
        SPList list = site.AllWebs[0].Lists["Tasks"];  
  
        // string text = "";  
        int sum = 0;  
  
        Table1.Rows.Clear();  
  
        // Add table headers.  
        TableHeaderRow hr = new TableHeaderRow();  
        hr.BackColor = Color.LightBlue;  
        TableHeaderCell hc1 = new TableHeaderCell();  
        TableHeaderCell hc2 = new TableHeaderCell();  
        hc1.Text = "Expense Report Name";  
        hc2.Text = "Amount Exceeded";  
        hr.Cells.Add(hc1);  
        hr.Cells.Add(hc2);  
        // Add the TableHeaderRow as the first item   
        // in the Rows collection of the table.  
        Table1.Rows.AddAt(0, hr);  
  
        // Iterate through the tasks in the Task list and collect those   
        // that have values in the "Related Content" and "Outcome"   
        // fields - the fields written to when expense approval is   
        // required.  
        foreach (SPListItem item in list.Items)  
        {  
            string s_relContent = "";  
            string s_outcome = "";  
  
            try  
            {  
                // Task has the fields - treat as expense report.  
                s_relContent = item.GetFormattedValue("Related   
                  Content");  
                s_outcome = item.GetFormattedValue("Outcome");  
            }  
            catch  
            {  
                // Task does not have fields - skip it.  
                continue;  
            }  
  
            if (!String.IsNullOrEmpty(s_relContent) &&   
              !String.IsNullOrEmpty(s_outcome))  
            {  
                // Convert amount to an int and keep a running total.  
                sum += Convert.ToInt32(s_outcome);  
                TableCell relContent = new TableCell();  
                relContent.Text = s_relContent;  
                TableCell outcome = new TableCell();  
                outcome.Text = "$" + s_outcome;  
                TableRow dataRow2 = new TableRow();  
                dataRow2.Cells.Add(relContent);  
                dataRow2.Cells.Add(outcome);  
                Table1.Rows.Add(dataRow2);  
            }  
        }  
  
        // Report the sum of the reports in the table footer.  
           TableFooterRow tfr = new TableFooterRow();  
        tfr.BackColor = Color.LightGreen;  
  
        // Create a TableCell object to contain the   
        // text for the footer.  
        TableCell ftc1 = new TableCell();  
        TableCell ftc2 = new TableCell();  
        ftc1.Text = "TOTAL: ";  
        ftc2.Text = "$" + Convert.ToString(sum);  
  
        // Add the TableCell object to the Cells  
        // collection of the TableFooterRow.  
        tfr.Cells.Add(ftc1);  
        tfr.Cells.Add(ftc2);  
  
        // Add the TableFooterRow to the Rows  
        // collection of the table.  
        Table1.Rows.Add(tfr);  
    }  
  
    catch (Exception errx)  
    {  
        System.Diagnostics.Debug.WriteLine("Error: " + errx.ToString());  
    }  
    ```  
  
    > [!WARNING]  
    >  Pamiętaj zastąpić "elementu TestServer" w kodzie nazwę prawidłowego serwera z programem SharePoint.  
  
## <a name="testing-the-application-page"></a>Testowanie strony aplikacji  
 Następnie należy określić, czy strona aplikacji poprawne wyświetlanie danych wydatków.  
  
#### <a name="to-test-the-application-page"></a>Aby przetestować stronę aplikacji  
  
1.  Wybierz klawisz F5, aby uruchomić i wdrażanie projektu w programie SharePoint.  
  
2.  Wybierz **Home** przycisk, a następnie wybierz pozycję **dokumenty udostępnione** łącze na pasek szybkiego uruchamiania, aby wyświetlić listę dokumenty udostępnione w witrynie programu SharePoint.  
  
3.  Do reprezentowania raporty wydatków w tym przykładzie, Przekaż kilka nowych dokumentów do listy dokumentów, wybierając **dokumenty** łącze **LibraryTools** kartę w górnej części strony, a następnie wybierając  **Przekaż dokument** na wstążce narzędzi.  
  
4.  Po przekazaniu niektórych dokumentów wystąpienia przepływu pracy, wybierając **biblioteki** łącze **LibraryTools** kartę w górnej części strony, a następnie wybierając **ustawienia biblioteki**na wstążce narzędzi.  
  
5.  W **ustawienia biblioteki dokumentów** wybierz pozycję **ustawienia przepływu pracy** łącze w **uprawnienia i zarządzanie** sekcji.  
  
6.  W **ustawienia przepływu pracy** wybierz pozycję **Dodaj przepływ pracy** łącza.  
  
7.  W **Dodaj przepływ pracy** wybierz pozycję **ExpenseReport - Workflow1** przepływu pracy, wprowadź nazwę przepływu pracy, takich jak **ExpenseTest**, a następnie wybierz pozycję **Dalej** przycisku.  
  
     Zostanie wyświetlony formularz skojarzenia przepływu pracy. Służy on do zgłaszania kwota limit wydatków.  
  
8.  W formularzu skojarzenia wprowadź **1000** do **automatycznego zatwierdzania Limit** polu, a następnie wybierz pozycję **skojarzenia przepływu pracy** przycisku.  
  
9. Wybierz **macierzystego** przycisk, aby powrócić do strony głównej programu SharePoint.  
  
10. Wybierz **dokumenty udostępnione** łącze na pasek szybkiego uruchamiania.  
  
11. Wybierz jedną z przekazanego dokumentów, aby wyświetlić strzałkę listy rozwijanej, wybierz go, a następnie wybierz **przepływy pracy** elementu.  
  
12. Wybierz obraz obok ExpenseTest do wyświetlania formularza inicjowania przepływu pracy.  
  
13. W **całkowity koszt** polu tekstowym wprowadź wartość, która jest większa niż 1000, a następnie wybierz **Uruchom przepływ pracy** przycisku.  
  
     Gdy zgłoszone wydatków przekracza ilość przydzielonego wydatków, zadanie zostanie dodany do listy zadań. Kolumna o nazwie **ExpenseTest** z wartością **Ukończono** jest także dodawane do elementu raportu wydatków na liście dokumentów udostępnionych.  
  
14. Powtórz kroki od 11-13 z innych dokumentów na liście dokumentów udostępnionych. (Liczbą dokumentów nie jest ważne).  
  
15. Wyświetl stronę podsumowania aplikacji wydatków raportu, otwierając następujący adres URL w przeglądarce sieci Web: **http://***SystemName***/_layouts/ExpenseReport/ApplicationPage1.aspx**.  
  
     Strona podsumowania raportu wydatków zawiera listę wszystkich raportów wydatków, które przekroczyło przydzielony ilość, jej przekraczają ilość i sumy dla wszystkich raportów.  
  
## <a name="next-steps"></a>Następne kroki  
 Aby uzyskać więcej informacji na temat stron aplikacji programu SharePoint, zobacz [tworzenie stron aplikacji dla programu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
 Możesz można dowiedzieć się więcej na temat projektowania zawartości strony programu SharePoint przy użyciu projektanta wizualnego sieci Web w programie Visual Studio z tych tematów:  
  
-   [Tworzenie składników Web Part dla SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).  
  
-   [Tworzenie formantów wielokrotnych dla części sieciowych lub stron aplikacji](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Tworzenie przepływu pracy z formularzami inicjacji i skojarzenia](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)   
 [Porady: Tworzenie strony aplikacji](../sharepoint/how-to-create-an-application-page.md)   
 [Tworzenie stron aplikacji dla SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  