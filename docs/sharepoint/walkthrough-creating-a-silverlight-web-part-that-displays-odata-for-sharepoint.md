---
title: 'Wskazówki: Tworzenie składnika Web Part Silverlight wyświetlającego dane OData dla programu SharePoint | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/22/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SPE.SilverlightWebPart
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 019c1d4b20f1d7a53fc68ef561d45989e93eee28
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint"></a>Wskazówki: Tworzenie składnika Web Part programu Silverlight wyświetlającego dane OData dla programu SharePoint
  SharePoint 2010 udostępnia dane listy za pomocą OData. W programie SharePoint usługa OData jest wdrażana przez usługę ListData.svc RESTful. W tym przewodniku przedstawiono sposób tworzenia programu SharePoint składnik web part, który jest hostem aplikacji Silverlight. Aplikacji Silverlight Wyświetla informacje o liście anonsów programu SharePoint przy użyciu ListData.svc. Aby uzyskać więcej informacji, zobacz [interfejsu REST programu SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=225999) i [Open Data Protocol](http://go.microsoft.com/fwlink/?LinkId=226000).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   Obsługiwane wersje systemu Microsoft Windows i programu SharePoint. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Wymagania związane z opracowywaniem rozwiązań SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].  
  
##  <a name="creating-a-silverlight-application-and-silverlight-web-part"></a>Tworzenie aplikacji Silverlight i składnik Web Part Silverlight  
 Najpierw utwórz aplikację Silverlight w programie Visual Studio. Aplikacji Silverlight pobiera dane z listy anonsów programu SharePoint przy użyciu usługi ListData.svc.  
  
> [!NOTE]  
>  Brak wersji Silverlight przed 4.0 obsługę wymaganych interfejsów odwołujące się do danych listy programu SharePoint.  
  
#### <a name="to-create-a-silverlight-application-and-silverlight-web-part"></a>Aby utworzyć aplikację Silverlight i składnik web part Silverlight  
  
1.  Na pasku menu wybierz **pliku**, **nowy**, **projektu** do wyświetlenia **nowy projekt** okno dialogowe.  
  
2.  Rozwiń węzeł **SharePoint** węźle albo **Visual C#** lub **Visual Basic**, a następnie wybierz pozycję **2010** węzła.  
  
3.  W okienku szablonów wybierz **składnik Web Part Silverlight programu SharePoint 2010** szablonu.  
  
4.  W **nazwa** wprowadź **SLWebPartTest** , a następnie wybierz **OK** przycisku.  
  
     **Kreator dostosowania programu SharePoint** zostanie wyświetlone okno dialogowe.  
  
5.  Na **określić poziom lokacji i zabezpieczeń dla debugowania** strony, wprowadź adres URL witryny programu SharePoint server gdzie chcesz debugować definicji witryny lub użyj domyślnej lokalizacji (http://*Nazwa systemowa*/) .  
  
6.  W **co to jest poziom zaufania dla tego rozwiązania programu SharePoint?** wybierz **Wdróż jako rozwiązanie farmy** przycisk opcji.  
  
     Mimo że w tym przykładzie użyto rozwiązanie farmy, projekty części sieci web Silverlight można wdrożyć jako farmy lub rozwiązań w trybie piaskownicy. Aby uzyskać więcej informacji na temat rozwiązań w trybie piaskownicy oraz rozwiązaniami farmy, zobacz [uwagi dotyczące rozwiązania piaskownicy](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  W **jak chcesz skojarzyć składnik Web Part Silverlight** sekcji **Określ informacje o konfiguracji Silverlight** wybierz pozycję **Utwórz nowy projekt Silverlight i skojarzyć go z części sieci web** przycisk opcji.  
  
8.  Zmień **nazwa** do **SLApplication**ustaw **języka** albo **Visual Basic** lub **Visual C#**, a następnie ustaw **wersji Silverlight** do **Silverlight 4.0**.  
  
9. Wybierz **Zakończ** przycisku. Projekty są wyświetlane w **Eksploratora rozwiązań**.  
  
     Rozwiązanie zawiera dwa projekty: aplikacji Silverlight oraz składnik web part Silverlight. Aplikacji Silverlight są pobierane i wyświetlane dane listy z programu SharePoint oraz składnika web part Silverlight obsługuje aplikację Silverlight, dzięki któremu można go wyświetlić w programie SharePoint.  
  
##  <a name="customizing-the-silverlight-application"></a>Dostosowywanie aplikacji Silverlight  
 Dodaj elementy kodu i projektu do aplikacji Silverlight.  
  
#### <a name="to-customize-the-silverlight-application"></a>Aby dostosować aplikacji Silverlight  
  
1.  Dodaj odwołanie do zestawu do System.Windows.Data w aplikacji Silverlight. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie lub usuwanie odwołań za pomocą okna dialogowego Dodaj odwołanie](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
2.  W **Eksploratora rozwiązań**, otwórz menu skrótów **odwołania**, a następnie wybierz pozycję **Dodaj odwołanie do usługi**.  
  
    > [!NOTE]  
    >  Jeśli używasz programu Visual Basic, należy wybrać **Pokaż wszystkie pliki** ikony na początku **Eksploratora rozwiązań** do wyświetlenia **odwołania** węzła.  
  
3.  W polu adres **Dodaj odwołanie do usługi** okna dialogowego wprowadź adres URL witryny programu SharePoint, takich jak **http://MySPSite**, a następnie wybierz pozycję **Przejdź** przycisku.  
  
     Gdy Silverlight lokalizuje usługi OData programu SharePoint ListData.svc, zastępuje adres z adresem URL usługi pełna. Na przykład http://myserver staje się http://myserver/_vti_bin/ListData.svc.  
  
4.  Wybierz **OK** przycisk, aby dodać odwołania do usługi do projektu i użyj domyślnej nazwy usługi, ServiceReference1.  
  
5.  Na pasku menu wybierz **kompilacji**, **Kompiluj rozwiązanie**.  
  
6.  Dodaj nowe źródło danych do projektu, na podstawie usługi programu SharePoint. Aby to zrobić, na pasku menu, wybierz polecenie **widoku**, **inne okna**, **źródeł danych**.  
  
     **Źródeł danych** okna są wyświetlane wszystkie dostępne dane listy programu SharePoint, takie jak zadania, anonsów i kalendarza.  
  
7.  Dodaj dane listy anonsów do aplikacji Silverlight. Możesz przeciągnąć "Powiadomienia" z **źródeł danych** okna do projektanta Silverlight.  
  
     Spowoduje to utworzenie formantu siatki związanego z listy anonsów witryny programu SharePoint.  
  
8.  Rozmiar formantu siatki w celu dopasowania jej do strony programu Silverlight.  
  
9. W pliku kodu MainPage.xaml (MainPage.xaml.cs Visual C#) lub MainPage.xaml.vb dla języka Visual Basic Dodaj następujące odwołania do przestrzeni nazw.  
  
    ```vb  
    ' Add the following three Imports statements.  
    Imports SLApplication.ServiceReference1  
    Imports System.Windows.Data  
    Imports System.Data.Services.Client  
    ```  
  
    ```csharp  
    // Add the following three using statements.  
    using SLApplication.ServiceReference1;  
    using System.Windows.Data;  
    using System.Data.Services.Client;  
    ```  
  
10. Dodaj następujące deklaracje zmiennej u góry klasy.  
  
    ```vb  
    Private context As TeamSiteDataContext  
    Private myCollectionViewSource As CollectionViewSource  
    Private announcements As New DataServiceCollection(Of AnnouncementsItem)()  
    ```  
  
    ```csharp  
    private TeamSiteDataContext context;  
    private CollectionViewSource myCollectionViewSource;  
    DataServiceCollection<AnnouncementsItem> announcements = new DataServiceCollection<AnnouncementsItem>();  
    ```  
   
11. Zastąp `UserControl_Loaded` procedury następującym kodem.  
  
    ```vb  
    Private Sub UserControl_Loaded_1(sender As Object, e As RoutedEventArgs)  
        ' The URL for the OData service.  
        ' Replace <server name> in the next line with the name of your SharePoint server.  
        context = New TeamSiteDataContext(New Uri("http://<server name>/_vti_bin/ListData.svc"))  
  
        ' Do not load your data at design time.  
        If Not System.ComponentModel.DesignerProperties.GetIsInDesignMode(Me) Then  
            'Load your data here and assign the results to the CollectionViewSource.  
            myCollectionViewSource =   DirectCast(Me.Resources("announcementsViewSource"), System.Windows.Data.CollectionViewSource)  
            announcements.LoadCompleted += New EventHandler(Of LoadCompletedEventArgs)(AddressOf announcements_LoadCompleted)  
            announcements.LoadAsync(context.Announcements)  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private void UserControl_Loaded_1(object sender, RoutedEventArgs e)  
    {  
        // The URL for the OData service.  
        // Replace <server name> in the next line with the name of your   
        // SharePoint server.  
        context = new TeamSiteDataContext(new Uri("http://ServerName>/_vti_bin/ListData.svc"));  
  
        // Do not load your data at design time.  
        if (!System.ComponentModel.DesignerProperties.GetIsInDesignMode(this))  
        {  
            //Load your data here and assign the results to the CollectionViewSource.  
            myCollectionViewSource = (System.Windows.Data.CollectionViewSource)this.Resources["announcementsViewSource"];  
            announcements.LoadCompleted += new EventHandler<LoadCompletedEventArgs>(announcements_LoadCompleted);  
            announcements.LoadAsync(context.Announcements);  
        }  
    }  
    ```  
     Pamiętaj zastąpić *ServerName* symbol zastępczy nazwą serwera z programem SharePoint.  
  
12. Dodaj procedurę obsługi błędów.  
  
    ```vb  
    Private Sub announcements_LoadCompleted(sender As Object, e As LoadCompletedEventArgs)  
        ' Handle any errors.  
        If e.[Error] Is Nothing Then  
            myCollectionViewSource.Source = announcements  
        Else  
            MessageBox.Show(String.Format("ERROR: {0}", e.[Error].Message))  
        End If  
    End Sub  
  
    ```  
  
    ```csharp  
    void announcements_LoadCompleted(object sender, LoadCompletedEventArgs e)  
    {  
        // Handle any errors.  
        if (e.Error == null)  
        {  
            myCollectionViewSource.Source = announcements;  
        }  
        else  
        {  
            MessageBox.Show(string.Format("ERROR: {0}", e.Error.Message));  
        }  
    }  
    ```  
       
## <a name="modifying-the-silverlight-web-part"></a>Modyfikowanie składnika Web Part Silverlight  
 Zmień właściwości w projekcie części sieci web Silverlight, aby włączyć debugowanie Silverlight.  
  
#### <a name="to-modify-the-silverlight-web-part"></a>Aby zmodyfikować składnik web part Silverlight  
  
1.  Otwórz menu skrótów dla projektu Silverlight części sieci web (**SLWebPartTest**), a następnie wybierz pozycję **właściwości**.  
  
2.  W **właściwości** okna, wybierz **SharePoint** kartę.  
  
3.  Jeśli jeszcze nie jest wybrana, wybierz **Silverlight włączyć debugowanie (zamiast debugowanie skryptów)** pole wyboru.  
  
4.  Zapisz projekt.  
  
##  <a name="testing-the-silverlight-web-part"></a>Testowanie składnik Web Part Silverlight  
 Nowy składnik web part Silverlight należy przetestować w programie SharePoint, aby zapewnić prawidłowe wyświetlanie danych listy programu SharePoint.  
  
#### <a name="to-test-the-silverlight-web-part"></a>Aby przetestować składnik web part Silverlight  
  
1.  Wybierz klawisz F5, aby skompilować i uruchomić rozwiązania programu SharePoint.  
  
2.  W programie SharePoint na **Akcje witryny** menu, wybierz **Nowa strona**.  
  
3.  W **nową stronę** okna dialogowego, wprowadź tytuł, takich jak **testu części sieci Web SL**, a następnie wybierz pozycję **Utwórz** przycisk.  
  
4.  W Projektancie strony na **narzędzia do edycji** , wybierz pozycję **Wstaw**.  
  
5.  Na pasku karty Wybierz **składnika Web Part**.  
  
6.  W **kategorii** wybierz **niestandardowy** folderu.  
  
7.  W **składników Web Part** listy, wybierz składnik web part Silverlight, a następnie wybierz pozycję **Dodaj** przycisk, aby dodać składnik web part do projektanta.  
  
8.  Po dokonaniu wszystkie dodatki do strony sieci web, który ma, wybierz **strony** karcie, a następnie wybierz pozycję **Zapisz i Zamknij** przycisk na pasku narzędzi.  
  
     Składnik web part Silverlight powinny teraz wyświetlanie danych anonsu z witryny programu SharePoint. Domyślnie strony znajduje się na liście stron witryny w programie SharePoint.  
  
    > [!NOTE]  
    >  Podczas uzyskiwania dostępu do danych w programie Silverlight między domenami, Silverlight chroni przed luk w zabezpieczeniach, które mogą służyć do wykorzystania w aplikacji sieci web. Jeśli wystąpią problemy podczas uzyskiwania dostępu do danych zdalnych w programie Silverlight, zobacz [wprowadzania Service Available Across Domain Boundaries](http://go.microsoft.com/fwlink/?LinkId=223276).  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie składników Web Part dla SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Wdrażanie, publikowanie i aktualizowanie pakietów rozwiązania SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)  
  
  
