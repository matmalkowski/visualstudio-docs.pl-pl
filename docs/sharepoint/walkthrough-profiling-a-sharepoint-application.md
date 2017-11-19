---
title: "Wskazówki: Profilowanie aplikacji SharePoint | Dokumentacja firmy Microsoft"
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
helpviewer_keywords:
- SharePoint development in Visual Studio, profiling
- performance testing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, performance testing
- profiling [SharePoint development in Visual Studio]
ms.assetid: 0b19d4b7-5fcc-42a2-b411-96eccd00137f
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0b2785e69bbfd6dff17f73b9840b88ad48454e0b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-profiling-a-sharepoint-application"></a>Wskazówki: Profilowanie aplikacji SharePoint
  W tym przewodniku przedstawiono sposób korzystania z narzędzi profilowania w programie Visual Studio do optymalizowania wydajności aplikacji programu SharePoint. Przykładowa aplikacja jest odbiorcy zdarzeń funkcji programu SharePoint, zawierający pętli bezczynności, który powoduje spadek wydajności odbiorcy zdarzeń funkcji. Profilera Visual Studio można znaleźć i wyeliminować najdroższych (najwolniejsze wykonywania) część projektu, znanej także jako *aktywnej ścieżki*.  
  
 W tym przewodniku przedstawiono następujące zadania:  
  
-   [Dodawanie funkcji i odbiorcy zdarzeń funkcji](#BKMK_AddFtrandFtrEvntReceiver).  
  
-   [Konfigurowanie i wdrażanie aplikacji programu SharePoint](#BKMK_ConfigSharePointApp).  
  
-   [Uruchamianie aplikacji programu SharePoint](#BKMK_RunSPApp).  
  
-   [Wyświetlanie i interpretowaniu wyników profilowania](#BKMK_ViewResults).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   Obsługiwane wersje systemu Microsoft Windows i programu SharePoint. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Wymagania związane z opracowywaniem rozwiązań SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].  
  
## <a name="creating-a-sharepoint-project"></a>Tworzenie projektu programu SharePoint  
 Najpierw utwórz projekt programu SharePoint.  
  
#### <a name="to-create-a-sharepoint-project"></a>Aby utworzyć projekt programu SharePoint  
  
1.  Na pasku menu wybierz **pliku**, **nowy**, **projektu** do wyświetlenia **nowy projekt** okno dialogowe.  
  
2.  Rozwiń węzeł **SharePoint** węźle albo **Visual C#** lub **Visual Basic**, a następnie wybierz pozycję **2010** węzła.  
  
3.  W okienku szablonów wybierz **projektu programu SharePoint 2010** szablonu.  
  
4.  W **nazwa** wprowadź **ProfileTest**, a następnie wybierz pozycję **OK** przycisku.  
  
     **Kreator dostosowania programu SharePoint** pojawi się.  
  
5.  Na **określić poziom lokacji i zabezpieczeń dla debugowania** strony, wprowadź adres URL witryny programu SharePoint server gdzie chcesz debugować definicji witryny lub użyj domyślnej lokalizacji (http://*Nazwa systemowa*/) .  
  
6.  W **co to jest poziom zaufania dla tego rozwiązania programu SharePoint?** wybierz **Wdróż jako rozwiązanie farmy** przycisk opcji.  
  
     Obecnie można tylko profilu rozwiązania farmy. Aby uzyskać więcej informacji na temat rozwiązania piaskownicy w porównaniu z rozwiązaniami farmy, zobacz [uwagi dotyczące rozwiązania piaskownicy](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  Wybierz **Zakończ** przycisku. Projekt zostanie wyświetlony w **Eksploratora rozwiązań**.  
  
##  <a name="BKMK_AddFtrandFtrEvntReceiver"></a>Dodawanie funkcji i funkcji odbiorcy zdarzeń  
 Następnie dodaj funkcji do projektu wraz z obsługiwanego odbiornika dla funkcji. Odbiornik zdarzeń będzie zawierać kod do profilowania.  
  
#### <a name="to-add-a-feature-and-feature-event-receiver"></a>Aby dodać funkcję i odbiorcy zdarzeń funkcji  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów **funkcje** węzła, wybierz **dodać funkcję**i pozostaw wartość domyślną nazwę **Feature1**.  
  
2.  W **Eksploratora rozwiązań**, otwórz menu skrótów **Feature1**, a następnie wybierz pozycję **dodać odbiorcy zdarzeń**.  
  
     Dodaje plik kodu do funkcji z kilku poza komentarzem zdarzenia i otwiera plik do edycji.  
  
3.  W klasie odbiornik event Dodaj następujące deklaracje zmiennej.  
  
    ```vb  
    ' SharePoint site/subsite.  
    Private siteUrl As String = "http://localhost"  
    Private webUrl As String = "/"  
    ```  
  
    ```csharp  
    // SharePoint site/subsite.  
    private string siteUrl = "http://localhost";  
    private string webUrl = "/";  
    ```  
  
4.  Zastąp `FeatureActivated` procedury z następującym kodem.  
  
    ```vb  
    Public Overrides Sub FeatureActivated(properties As SPFeatureReceiverProperties)  
        Try  
            Using site As New SPSite(siteUrl)  
                Using web As SPWeb = site.OpenWeb(webUrl)  
                    ' Reference the lists.  
                    Dim announcementsList As SPList = web.Lists("Announcements")  
  
                    ' Add a new announcement to the Announcements list.  
                    Dim listItem As SPListItem = announcementsList.Items.Add()  
                    listItem("Title") = "Activated Feature: " & Convert.ToString(properties.Definition.DisplayName)  
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was activated on: " & DateTime.Now.ToString()  
                    ' Waste some time.  
                    TimeCounter()  
                    ' Update the list.  
                    listItem.Update()  
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
  
                    // Add a new announcement to the Announcements list.  
                    SPListItem listItem = announcementsList.Items.Add();  
                    listItem["Title"] = "Activated Feature: " + properties.Definition.DisplayName;  
                    listItem["Body"] = properties.Definition.DisplayName + " was activated on: " +   
    DateTime.Now.ToString();  
                    // Waste some time.  
                    TimeCounter();  
                    // Update the list.  
                    listItem.Update();                          
                }  
            }  
        }  
  
        catch (Exception e)  
        {  
            Console.WriteLine("Error: " + e.ToString());  
        }  
    }  
    ```  
  
5.  Dodaj następujące Poniższa procedura `FeatureActivated`procedury.  
  
    ```vb  
  
    Public Sub TimeCounter()  
        Dim result As Integer  
        For i As Integer = 0 To 99999  
            For j As Integer = 0 To 9999  
                result = i * j  
            Next j  
        Next i  
    End Sub  
    ```  
  
    ```csharp  
    public void TimeCounter()  
    {  
        for (int i = 0; i < 100000; i++)  
        {  
            for (int j = 0; j < 10000; j++)  
            {  
                int result = i * j;  
            }  
        }  
    }  
    ```  
  
6.  W **Eksploratora rozwiązań**, otwórz menu skrótów projektu (**ProfileTest**), a następnie wybierz pozycję **właściwości**.  
  
7.  W **właściwości** oknie dialogowym wybierz **SharePoint** kartę.  
  
8.  W **aktywnej konfiguracji wdrożenia** wybierz **aktywacji nie**.  
  
     Wybranie tej konfiguracji wdrożenia można ręcznie uaktywnić funkcję później w programie SharePoint.  
  
9. Zapisz projekt.  
  
##  <a name="BKMK_ConfigSharePointApp"></a>Konfigurowanie i wdrażanie aplikacji programu SharePoint  
 Teraz, projekt SharePoint jest gotowy, ją skonfigurować i wdrożyć go na serwerze programu SharePoint.  
  
#### <a name="to-configure-and-deploy-the-sharepoint-application"></a>Aby skonfigurować i wdrożyć aplikację programu SharePoint  
  
1.  Na **Analizuj** menu, wybierz **Uruchom Kreatora osiągów**.  
  
2.  Na stronie jedną **kreatora osiągów**, pozostaw — metoda profilowania jako **próbkowanie Procesora** i wybierz polecenie **dalej** przycisk.  
  
     Inne metody profilowania można używać w bardziej zaawansowane profilowania sytuacji. Aby uzyskać więcej informacji, zobacz [metoda zbierania danych wydajności opis](/visualstudio/profiling/understanding-performance-collection-methods).  
  
3.  Na stronie dwóch **kreatora osiągów**, pozostaw cel profilu jako **ProfileTest** i wybierz polecenie **dalej** przycisku.  
  
     Jeśli rozwiązanie zawiera wiele projektów, znajdują się na tej liście.  
  
4.  Na stronie trzy **kreatora osiągów**, wyczyść **Włącz profilowanie interakcji między warstwami** pole wyboru, a następnie wybierz pozycję **dalej** przycisku.  
  
     Funkcja profilowanie interakcji warstwy (TIP) jest przydatna do pomiaru wydajności aplikacji z tej kwerendy bazy danych i dla pokazuje, ile razy żądanie strony sieci web. Ponieważ te dane nie jest wymagana w tym przykładzie, firma Microsoft nie włączyć tę funkcję.  
  
5.  Na stronie cztery **kreatora osiągów**, pozostaw **Uruchom profilowanie po zakończeniu pracy kreatora** zaznaczone pole wyboru, a następnie wybierz pozycję **Zakończ** przycisku.  
  
     Kreator Włącza profilowanie aplikacji na serwerze, wyświetla **Eksplorator wydajności** okna, a następnie kompilacji, wdraża i uruchamia aplikację programu SharePoint.  
  
##  <a name="BKMK_RunSPApp"></a>Uruchamianie aplikacji programu SharePoint  
 Uaktywnij funkcję w programie SharePoint, wyzwalania `FeatureActivation` zdarzeń kod wymagany do uruchomienia.  
  
#### <a name="to-run-the-sharepoint-application"></a>Uruchamianie aplikacji programu SharePoint  
  
1.  W programie SharePoint, należy otworzyć **Akcje witryny** menu, a następnie wybierz pozycję **ustawienia lokacji**.  
  
2.  W **Akcje witryny** wybierz **Zarządzanie funkcjami witryny** łącza.  
  
3.  W **funkcje** wybierz **Aktywuj** znajdujący się obok **ProfileTest Feature1**.  
  
     Występuje przerwie, gdy to zrobisz, z powodu pętli bezczynności wywoływana `FeatureActivated` funkcji.  
  
4.  Na **Szybkie uruchamianie** pasek, wybierz **wymieniono** , a następnie w **wymieniono** wybierz **anonsów**.  
  
     Zwróć uwagę, czy nowy anons został dodany do listy z informacją, że funkcja została aktywowana.  
  
5.  Zamknij witryny programu SharePoint.  
  
     Po zamknięciu programu SharePoint, profilera tworzy i Wyświetla przykładowy raport profilowania i zapisuje go jako plik Vsp w **ProfileTest** folder tego projektu.  
  
##  <a name="BKMK_ViewResults"></a>Wyświetlanie i interpretowaniu wyników profilowania  
 Teraz, gdy zostało uruchomione i profilowane aplikacji programu SharePoint, należy wyświetlić wyniki testów.  
  
#### <a name="to-view-and-interpret-the-profiling-results"></a>Aby wyświetlić i interpretuj wyniki profilowania  
  
1.  W **funkcje wykonujące najwięcej indywidualnej pracy** sekcji raportu profilowania próbki, należy zauważyć, że `TimeCounter` znalazł się na górze listy.  
  
     Ta lokalizacja wskazuje, że `TimeCounter` był funkcji o najwyższym numerze próbek, co oznacza jest jednym z największych wąskich gardeł wydajności w aplikacji. Taka sytuacja nie jest zaskoczysz, ponieważ był celowo zaprojektowany w ten sposób w celach demonstracyjnych.  
  
2.  W **funkcje wykonujące najwięcej indywidualnej pracy** wybierz `ProcessRequest` łącze, aby wyświetlić dystrybucję koszt `ProcessRequest` funkcji.  
  
     W **wywołuje funkcje** sekcji `ProcessRequest`, zwróć uwagę, że **FeatureActiviated** funkcji jest wymieniony jako najbardziej kosztowne wywołał funkcję.  
  
3.  W **wywołuje funkcje** wybierz **FeatureActivated** przycisku.  
  
     W **wywołuje funkcje** sekcji **FeatureActivated**, `TimeCounter` funkcji jest wymieniony jako najbardziej kosztowne wywołał funkcję. W **widoku kodu funkcji** okienka, wyróżniony kod (`TimeCounter`) jest aktywny i wskazuje, gdzie jest potrzebna korekty.  
  
4.  Zamknij przykładowy raport profilowania.  
  
     Aby wyświetlić raport ponownie w dowolnej chwili, otwórz plik Vsp w **Eksplorator wydajności** okna.  
  
## <a name="fixing-the-code-and-reprofiling-the-application"></a>Rozwiązanie problemu kod i Reprofiling aplikacji  
 Teraz, gdy wykryto funkcja punkt aktywny w aplikacji programu SharePoint, usuń go.  
  
#### <a name="to-fix-the-code-and-reprofile-the-application"></a>Aby naprawić kod i reprofile aplikacji  
  
1.  W kodzie odbiorcy zdarzeń funkcji komentarz `TimeCounter` wywołanie metody `FeatureActivated` aby zapobiec wywoływane.  
  
2.  Zapisz projekt.  
  
3.  W **Eksplorator wydajności**, otwórz folder elementów docelowych, a następnie wybierz **ProfileTest** węzła.  
  
4.  Na **Eksplorator wydajności** paska narzędzi w **akcje** , wybierz pozycję **Uruchom profilowanie** przycisku.  
  
     Jeśli chcesz zmienić dowolne z właściwości profilowania przed reprofiling aplikacji, wybierz **Uruchom Kreatora osiągów** zamiast tego przycisku.  
  
5.  Postępuj zgodnie z instrukcjami **uruchamiania aplikacji programu SharePoint** sekcji wcześniej w tym temacie.  
  
     Teraz, gdy wywołanie pętli bezczynności został wyeliminowany, funkcję należy aktywować znacznie szybciej. Przykładowy raport profilowania powinien odzwierciedlać to.  
  
## <a name="see-also"></a>Zobacz też  
 [Eksplorator wydajności](/visualstudio/profiling/performance-explorer)   
 [Sesja wydajności — omówienie](/visualstudio/profiling/performance-session-overview)   
 [Profilowanie wydajności — przewodnik dla początkujących](/visualstudio/profiling/beginners-guide-to-performance-profiling)   
 [Znajdź wąskich gardeł aplikacji z profilera Visual Studio](http://go.microsoft.com/fwlink/?LinkID=137266)  
  
  