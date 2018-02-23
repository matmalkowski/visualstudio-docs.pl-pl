---
title: "Wskazówki: Debugowanie aplikacji programu SharePoint przy użyciu funkcji IntelliTrace | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IntelliTrace [SharePoint development in Visual Studio]
- standalone data collector
- SharePoint development in Visual Studio, IntelliTrace
- data collector
- IntelliTrace
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: d9f3e5ae5997f7ae4f7c7f94bc61dc526404f144
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2018
---
# <a name="walkthrough-debugging-a-sharepoint-application-by-using-intellitrace"></a>Wskazówki: debugowanie aplikacji SharePoint przy użyciu narzędzia IntelliTrace

Przy użyciu funkcji IntelliTrace, można łatwiej debugowanie rozwiązań SharePoint. Tradycyjny debugery umożliwiają tylko migawki rozwiązania w danym momencie. Jednak można użyć funkcji IntelliTrace do przeglądania zdarzeń przeszłych, które wystąpiły w rozwiązaniu i kontekst, w którym wystąpił i przejdź do kodu.

 W tym przewodniku pokazano, jak debugowania programu SharePoint 2010 lub SharePoint 2013 projektu programu Visual Studio przy użyciu programu Microsoft Monitoring Agent zbierania danych funkcji IntelliTrace z wdrożone aplikacje. Aby analizować te dane, należy użyć programu Visual Studio Enterprise. Ten projekt zawiera Odbiorca funkcji, które po aktywowaniu funkcji dodaje zadania do listy zadań i powiadomienia na liście anonsów. Gdy funkcja jest dezaktywowana, zadanie zostanie oznaczone jako wykonane, a drugi anonsu zostanie dodany do listy anonsów. Jednak procedura zawiera logiczny błąd, który uniemożliwia uruchomiony prawidłowo projektu. Przy użyciu funkcji IntelliTrace, należy znaleźć i popraw błąd.

 **Dotyczy:** informacje przedstawione w tym temacie dotyczą rozwiązań programu SharePoint 2010 oraz SharePoint 2013, które zostały utworzone w programie Visual Studio.

 W instruktażu przedstawiono następujące zagadnienia:

- [Tworzenie odbiornika funkcji](#BKMK_CreateReceiver)

- [Dodaj kod, aby odbiorca funkcji](#BKMK_AddCode)

- [Projekt testowy](#BKMK_Test1)

- [Gromadzenie danych IntelliTrace za pomocą programu Microsoft Monitoring Agent](#BKMK_CollectDiagnosticData)

- [Debugowanie i Usuń rozwiązania SharePoint](#BKMK_DebugSolution)

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne

Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- Obsługiwane wersje systemu Windows i programu SharePoint. Zobacz [wymagania związane z opracowywaniem rozwiązań SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).

- Visual Studio Enterprise.

## <a name="BKMK_CreateReceiver">Tworzenie odbiornika funkcji</a>

Najpierw należy utworzyć pusty projekt SharePoint ma odbiorca funkcji.

1. Utwórz projekt rozwiązania programu SharePoint 2010 lub SharePoint 2013 i nadaj mu nazwę **IntelliTraceTest**.

     **Kreator dostosowania programu SharePoint** pojawia się, w którym można określić witrynę programu SharePoint dla projektu i poziom zaufania rozwiązania.

2. Wybierz **Wdróż jako rozwiązanie farmy** przycisk opcji, a następnie wybierz pozycję **Zakończ** przycisku.

     IntelliTrace działa tylko z rozwiązaniami farmy.

3. W **Eksploratora rozwiązań**, otwórz menu skrótów **funkcji** węzła, a następnie wybierz pozycję **funkcji Dodaj**.

     Pojawi się Feature1.Feature.

4. Otwórz menu skrótów dla Feature1.feature, a następnie wybierz pozycję **dodać odbiorcy zdarzeń** można dodać modułu kodu funkcji.

## <a name="BKMK_AddCode">Dodaj kod, aby odbiorca funkcji</a>

Następnie dodaj kod, aby dwie metody w Odbiorca funkcji: `FeatureActivated` i `FeatureDeactivating`. Te metody wyzwolenia zawsze, gdy funkcja jest aktywowany lub dezaktywowany w programie SharePoint, odpowiednio.

1. W górnej części `Feature1EventReceiver` klasy, Dodaj następujący kod, który deklaruje zmienne, które Określ witrynę programu SharePoint i podwitryny:

    ```vb
    ' SharePoint site and subsite.
    Private siteUrl As String = "http://localhost"
    Private webUrl As String = "/"
    ```

    ```csharp
    // SharePoint site and subsite.
    private string siteUrl = "http://localhost";
    private string webUrl = "/";
    ```

2. Zastąp `FeatureActivated` metodę z następującym kodem:

    ```vb
    Public Overrides Sub FeatureActivated(ByVal properties As SPFeatureReceiverProperties)
        Try
            Using site As New SPSite(siteUrl)
                Using web As SPWeb = site.OpenWeb(webUrl)
                    ' Reference the lists.
                    Dim announcementsList As SPList = web.Lists("Announcements")
                    Dim taskList As SPList = web.Lists("Tasks")

                    ' Add an announcement to the Announcements list.
                    Dim listItem As SPListItem = announcementsList.Items.Add()
                    listItem("Title") = "Activated Feature: " & Convert.ToString(properties.Definition.DisplayName)
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was activated on: " & DateTime.Now.ToString()
                    listItem.Update()

                    ' Add a task to the Task list.
                    Dim newTask As SPListItem = taskList.Items.Add()
                    newTask("Title") = "Deactivate feature: " & Convert.ToString(properties.Definition.DisplayName)
                    newTask.Update()
                End Using
            End Using

        Catch e As Exception
            Console.WriteLine("Error: " & e.ToString())
        End Try

    End Sub
    ```

    ```csharp
    public override void FeatureActivated(SPFeatureReceiverProperties properties)
    {
        try
        {
            using (SPSite site = new SPSite(siteUrl))
            {
                using (SPWeb web = site.OpenWeb(webUrl))
                {
                    // Reference the lists.
                    SPList announcementsList = web.Lists["Announcements"];
                    SPList taskList = web.Lists["Tasks"];

                    // Add an announcement to the Announcements list.
                    SPListItem listItem = announcementsList.Items.Add();
                    listItem["Title"] = "Activated Feature: " + properties.Definition.DisplayName;
                    listItem["Body"] = properties.Definition.DisplayName + " was activated on: " + DateTime.Now.ToString();
                    listItem.Update();

                    // Add a task to the Task list.
                    SPListItem newTask = taskList.Items.Add();
                    newTask["Title"] = "Deactivate feature: " + properties.Definition.DisplayName;
                    newTask.Update();
                }
            }
        }

        catch (Exception e)
        {
            Console.WriteLine("Error: " + e.ToString());
        }

    }
    ```

3. Zastąp `FeatureDeactivating` metodę z następującym kodem:

    ```vb
    Public Overrides Sub FeatureDeactivating(ByVal properties As SPFeatureReceiverProperties)
        ' The following line induces an error to demonstrate debugging.
        ' Remove this line later for proper operation.
        Throw New System.InvalidOperationException("Serious error occurred!")
        Try
            Using site As New SPSite(siteUrl)
                Using web As SPWeb = site.OpenWeb(webUrl)
                    ' Reference the lists.
                    Dim taskList As SPList = web.Lists("Tasks")
                    Dim announcementsList As SPList = web.Lists("Announcements")

                    ' Add an announcement that the feature was deactivated.
                    Dim listItem As SPListItem = announcementsList.Items.Add()
                    listItem("Title") = "Deactivated Feature: " & Convert.ToString(properties.Definition.DisplayName)
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was deactivated on: " & DateTime.Now.ToString()
                    listItem.Update()

                    ' Find the task that the feature receiver added to the Task list when the
                    ' feature was activated.
                    Dim qry As New SPQuery()
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>"
                    Dim taskItems As SPListItemCollection = taskList.GetItems(qry)

                    For Each taskItem As SPListItem In taskItems
                        ' Mark the task as complete.
                        taskItem("PercentComplete") = 1
                        taskItem("Status") = "Completed"
                        taskItem.Update()
                    Next
                End Using

            End Using

        Catch e As Exception
            Console.WriteLine("Error: " & e.ToString())
        End Try

    End Sub
    ```

    ```csharp
    public override void FeatureDeactivating(SPFeatureReceiverProperties properties)
    {
        // The following line induces an error to demonstrate debugging.
        // Remove this line later for proper operation.
        throw new System.InvalidOperationException("A serious error occurred!"); 
        try
        {
            using (SPSite site = new SPSite(siteUrl))
            {
                using (SPWeb web = site.OpenWeb(webUrl))
                {
                    // Reference the lists.
                    SPList taskList = web.Lists["Tasks"];
                    SPList announcementsList = web.Lists["Announcements"];

                    // Add an announcement that the feature was deactivated.
                    SPListItem listItem = announcementsList.Items.Add();
                    listItem["Title"] = "Deactivated Feature: " + properties.Definition.DisplayName;
                    listItem["Body"] = properties.Definition.DisplayName + " was deactivated on: " + DateTime.Now.ToString();
                    listItem.Update();

                    // Find the task that the feature receiver added to the Task list when the
                    // feature was activated.
                    SPQuery qry = new SPQuery();
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>";
                    SPListItemCollection taskItems = taskList.GetItems(qry);

                    foreach (SPListItem taskItem in taskItems)
                    {
                        // Mark the task as complete.
                        taskItem["PercentComplete"] = 1;
                        taskItem["Status"] = "Completed";
                        taskItem.Update();
                    }
                }
            }

        }

        catch (Exception e)
        {
            Console.WriteLine("Error: " + e.ToString());
        }
    }
    ```

## <a name="BKMK_Test1">Projekt testowy</a>

Kod zostanie dodany do Odbiorca funkcji i modułów zbierających dane jest uruchomiona, wdrażanie i uruchamianie rozwiązania programu SharePoint, aby sprawdzić, czy działa on prawidłowo.

> [!IMPORTANT]
> Na przykład w obsłudze zdarzeń FeatureDeactivating, jest zgłaszany błąd. W dalszej części tego przewodnika możesz znaleźć tego błędu przy użyciu pliku .iTrace, który utworzył modułów zbierających dane.

1. Wdrażanie rozwiązania do programu SharePoint, a następnie otwórz witrynę programu SharePoint w przeglądarce.

     Funkcja automatycznie aktywuje, powoduje jej odbiorca funkcji dodać powiadomienia i zadania.

2. Wyświetl zawartość list anonsów i zadania.

     Lista anonsów powinny mieć nowy anons o nazwie **funkcji aktywnego: IntelliTraceTest_Feature1**, oraz listy zadań powinno mieć nowe zadanie o nazwie **funkcji Dezaktywuj: IntelliTraceTest_ Feature1**. Jeśli brakuje jednej z tych elementów, sprawdź, czy funkcja jest aktywna. Jeśli go nie została aktywowana, Aktywuj ją.

3. Dezaktywuj tę funkcję, wykonując następujące czynności:

    1. Na **Akcje witryny** menu w programie SharePoint, wybierz **ustawienia lokacji**.

    2. W obszarze **Akcje witryny**, wybierz **Zarządzanie funkcjami witryny** łącza.

    3. Obok pozycji **IntelliTraceTest Feature1**, wybierz **Dezaktywuj** przycisku.

    4. Na stronie Ostrzeżenie Wybierz **Dezaktywuj tę funkcję** łącza.

     Program obsługi zdarzeń FeatureDeactivating() zgłasza błąd.

## <a name="BKMK_CollectDiagnosticData">Gromadzenie danych IntelliTrace za pomocą programu Microsoft Monitoring Agent</a>

Po zainstalowaniu programu Microsoft Monitoring Agent na komputerze z programem SharePoint, rozwiązań programu SharePoint można debugować przy użyciu danych, które jest bardziej szczegółowy niż ogólne informacje, które zwraca IntelliTrace. Agent działa poza Visual Studio przy użyciu poleceń cmdlet programu PowerShell do przechwycenia informacji o debugowaniu podczas sekwencji rozwiązania programu SharePoint.

> [!NOTE]
> Informacje o konfiguracji w tej sekcji są specyficzne dla tego przykładu. Aby uzyskać więcej informacji na temat innych opcji konfiguracji, zobacz [przy użyciu autonomicznego modułu zbierającego IntelliTrace](/visualstudio/debugger/using-the-intellitrace-stand-alone-collector).

1. Na komputerze z programem SharePoint [skonfigurować programu Microsoft Monitoring Agent i rozpocząć monitorowanie rozwiązania](/visualstudio/debugger/using-the-intellitrace-stand-alone-collector).

2. Dezaktywowanie funkcji:

    1. Na **Akcje witryny** menu w programie SharePoint, wybierz **ustawienia lokacji**.

    2. W obszarze **Akcje witryny**, wybierz **Zarządzanie funkcjami witryny** łącza.

    3. Obok pozycji **IntelliTraceTest Feature1**, wybierz **Dezaktywuj** przycisku.

    4. Na stronie Ostrzeżenie Wybierz **Dezaktywuj tę funkcję** łącza.

     (W tym przypadku z powodu błędu zgłoszony w obsłudze zdarzeń FeatureDeactivating()), wystąpi błąd.

3. W oknie programu PowerShell, uruchom [Stop-WebApplicationMonitoring](http://go.microsoft.com/fwlink/?LinkID=313687) polecenie, aby utworzyć plik .iTrace, zatrzymać monitorowanie i uruchom ponownie rozwiązanie programu SharePoint.

     **Stop-WebApplicationMonitoring***"\<SharePointSite >\\< SharePointAppName\>"* 

## <a name="BKMK_DebugSolution">Debugowanie i Usuń rozwiązania SharePoint</a>

Teraz można wyświetlić plik dziennika funkcji IntelliTrace w programie Visual Studio można znaleźć i napraw błąd w rozwiązaniu programu SharePoint.

1. W folderze \IntelliTraceLogs Otwórz plik .iTrace w programie Visual Studio.

     **Podsumowanie funkcji IntelliTrace** zostanie wyświetlona strona. Ponieważ błąd nie został obsłużony, identyfikator korelacji programu SharePoint (GUID) jest wyświetlany w obszarze nieobsługiwany wyjątek **analizy** sekcji. Wybierz **stos wywołań** przycisk, aby wyświetlić stos wywołań, w którym wystąpił błąd.

2. Wybierz **debugowania wyjątek** przycisku.

     Jeśli zostanie wyświetlony monit, załadować plików symboli. W **IntelliTrace** okna, wyjątek zostanie wyróżniona jako "wyrzuconych: Wystąpił poważny błąd!".

     W oknie funkcji IntelliTrace wybierz wyjątku, aby wyświetlić kod, który nie powiodło się.

3. Usuń błąd przez otwarcie rozwiązania programu SharePoint, a następnie komentowania lub usuwanie **throw** instrukcji w górnej części procedury FeatureDeactivating().

4. Ponownie skompiluj rozwiązanie w programie Visual Studio, a następnie ponownie wdrożyć do programu SharePoint.

5. Dezaktywuj tę funkcję, wykonując następujące czynności:

    1. Na **Akcje witryny** menu w programie SharePoint, wybierz **ustawienia lokacji**.

    2. W obszarze **Akcje witryny**, wybierz **Zarządzanie funkcjami witryny** łącza.

    3. Obok pozycji **IntelliTraceTest Feature1**, wybierz **Dezaktywuj** przycisku.

    4. Na stronie Ostrzeżenie Wybierz **Dezaktywuj tę funkcję** łącza.

6. Otwórz listę zadań i sprawdź, czy **stan** wartość Dezaktywuj zadania jest "ukończone" i jego **Ukończono** wartość wynosi 100%.

     Kod teraz działa prawidłowo.

## <a name="see-also"></a>Zobacz także

[Weryfikowanie i debugowanie kodu aplikacji programu SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md)  
[IntelliTrace](/visualstudio/debugger/intellitrace)  
[Wskazówki: Sprawdź kod programu SharePoint przy użyciu testów jednostkowych](https://msdn.microsoft.com/library/gg599006(v=vs.100).aspx)
