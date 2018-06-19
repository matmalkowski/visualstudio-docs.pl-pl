---
title: Powiązanie formantów WPF z usługi danych WCF
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 8823537c-82f0-41f7-bf30-705f0e5e59fd
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 8152a02df8f335a92024134dde89b45d2f3e115a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31927363"
---
# <a name="bind-wpf-controls-to-a-wcf-data-service"></a>Powiązanie formantów WPF z usługi danych WCF

W tym przewodniku spowoduje utworzenie aplikacji WPF, który zawiera formanty powiązane z danymi. Formanty są powiązane z rekordy klientów, które znajdują się w [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]. Dodasz również przycisków, których klienci mogą używać do wyświetlania i aktualizowania rekordów.

W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie modelu danych jednostki, które są generowane na podstawie danych w bazie danych AdventureWorksLT.

- Tworzenie [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] który uwidacznia danych w modelu danych jednostki w aplikacji WPF.

- Tworzenie zestawu formantów powiązanych z danymi przez przeciąganie elementów z **źródeł danych** okna Projektanta WPF.

- Tworzenie przycisków nawigowania rekordy klientów do przodu i do tyłu.

- Tworzenie przycisku, który zapisuje dane w formantach do zmiany [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] i źródła danych.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]

-   Dostęp do działającego wystąpienia programu SQL Server lub SQL Server Express z AdventureWorksLT przykładowej bazy danych do niego dołączony. Możesz pobrać bazę danych AdventureWorksLT z [witryny sieci Web w witrynie CodePlex](http://go.microsoft.com/fwlink/?linkid=87843).

Znajomość następujące pojęcia jest również przydatna, ale nie są wymagane do ukończenia Instruktaż:

-   Usługi danych WCF. Aby uzyskać więcej informacji, zobacz [omówienie](/dotnet/framework/data/wcf/wcf-data-services-overview).

-   Modele danych w [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)].

-   A modeli danych jednostki ADO.NET Entity Framework. Aby uzyskać więcej informacji, zobacz [Omówienie struktury jednostek](/dotnet/framework/data/adonet/ef/overview).

-   Powiązanie danych WPF. Aby uzyskać więcej informacji, zobacz [omówienie powiązania danych](/dotnet/framework/wpf/data/data-binding-overview).

## <a name="create-the-service-project"></a>Tworzenie projektu usługi
Skorzystaniem z tego przewodnika, tworząc projekt [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].

### <a name="to-create-the-service-project"></a>Aby utworzyć projekt usługi

1.  Uruchom program Visual Studio.

2.  Na **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu**.

3.  Rozwiń węzeł **Visual C#** lub **Visual Basic**, a następnie wybierz **Web**.

4.  Wybierz **aplikacji sieci Web ASP.NET** szablonu projektu.

5.  W **nazwa** wpisz `AdventureWorksService` i kliknij przycisk **OK**.

     Program Visual Studio tworzy `AdventureWorksService` projektu.

6.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Default.aspx** i wybierz **usunąć**. Ten plik nie jest konieczne w ramach tego przewodnika.

## <a name="create-an-entity-data-model-for-the-service"></a>Tworzenie modelu Entity Data Model dla usługi
Aby udostępnić dane do aplikacji przy użyciu [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], należy zdefiniować modelu danych dla usługi. [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] Obsługuje dwa typy modeli danych: modeli danych jednostki i modeli danych niestandardowych, które zdefiniowano przy użyciu języka wspólnego (CLR) typowe obiekty, które implementują <xref:System.Linq.IQueryable%601> interfejsu. W tym przewodniku tworzenia modelu danych jednostki do modelu danych.

### <a name="to-create-an-entity-data-model"></a>Do tworzenia modelu danych jednostki

1.  Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.

2.  Na liście Zainstalowane szablony kliknij **danych**, a następnie wybierz **modelu danych jednostki ADO.NET** elementu projektu.

3.  Zmień nazwę, aby `AdventureWorksModel.edmx`i kliknij przycisk **Dodaj**.

     **Modelu Entity Data Model** zostanie otwarty Kreator.

4.  Na **wybierz zawartość modelu** kliknij przycisk **generowania z bazy danych**i kliknij przycisk **dalej**.

5.  Na **wybierz połączenie danych** wybierz jedną z następujących opcji:

    -   Jeśli połączenie danych z przykładową bazę danych AdventureWorksLT jest dostępny na liście rozwijanej, wybierz go.

    -   Kliknij przycisk **nowe połączenie**oraz tworzenie połączenia z bazą danych AdventureWorksLT.

6.  Na **wybierz połączenie danych** strony, upewnij się, że **Zapisz ustawienia połączenia w pliku App.Config jako jednostki** opcja jest zaznaczona, a następnie kliknij **dalej**.

7.  Na **wybierz obiekty bazy danych użytkownika** rozwiń pozycję **tabel**, a następnie wybierz **SalesOrderHeader** tabeli.

8.  Kliknij przycisk **Zakończ**.

## <a name="create-the-service"></a>Tworzenie usługi
Utwórz [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] do udostępniania danych w modelu danych jednostki w aplikacji WPF.

### <a name="to-create-the-service"></a>Aby utworzyć usługę

1.  Na **projektu** menu, wybierz opcję **Dodaj nowy element**.

2.  Na liście Zainstalowane szablony kliknij **Web**, a następnie wybierz **usługi danych WCF** elementu projektu.

3.  W **nazwa** wpisz `AdventureWorksService.svc`i kliknij przycisk **Dodaj**.

     Dodaje programu Visual Studio `AdventureWorksService.svc` do projektu.

## <a name="configure-the-service"></a>Skonfiguruj usługę
Należy skonfigurować usług może działać w modelu Entity Data Model, który został utworzony.

### <a name="to-configure-the-service"></a>Aby skonfigurować usługę

1.  W `AdventureWorks.svc` kodu pliku, Zastąp `AdventureWorksService` klasy deklaracji z następującym kodem.

     [!code-csharp[Data_WPFWCF#1](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_1.cs)]
     [!code-vb[Data_WPFWCF#1](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_1.vb)]

     Ten kod aktualizacji `AdventureWorksService` klasy, dzięki czemu dziedziczy <xref:System.Data.Services.DataService%601> który operuje na `AdventureWorksLTEntities` obiektu kontekstu klasy w modelu Entity Data Model. Aktualizuje również `InitializeService` metody do zezwalania klientom usług dostęp Pełna odczytu/zapisu do `SalesOrderHeader` jednostki.

2.  Skompilować projekt i sprawdź, czy zbudował bez błędów.

## <a name="create-the-wpf-client-application"></a>Tworzenie aplikacji klienckich WPF
Aby wyświetlić dane z [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], Utwórz nową aplikację WPF ze źródłem danych, która jest oparta na usługę. W dalszej części tego przewodnika będzie Dodaj formanty powiązane z danymi do aplikacji.

### <a name="to-create-the-wpf-client-application"></a>Aby utworzyć aplikację klienta WPF

1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł rozwiązania, kliknij przycisk **Dodaj**i wybierz **nowy projekt**.

2.  W **nowy projekt** okna dialogowego, rozwiń węzeł **Visual C#** lub **Visual Basic**, a następnie wybierz **Windows**.

3.  Wybierz **aplikacji WPF** szablonu projektu.

4.  W **nazwa** wpisz `AdventureWorksSalesEditor`i kliknij przycisk **OK**.

     Dodaje programu Visual Studio `AdventureWorksSalesEditor` projektu do rozwiązania.

5.  Na **danych** menu, kliknij przycisk **Pokaż źródeł danych**.

     **Źródeł danych** zostanie otwarte okno.

6.  W **źródeł danych** okna, kliknij przycisk **Dodaj nowe źródło danych**.

     **Konfiguracji źródła danych** zostanie otwarty Kreator.

7.  W **wybierz typ źródła danych** strony kreatora wybierz pozycję **usługi**, a następnie kliknij przycisk **dalej**.

8.  W **Dodaj odwołanie do usługi** okno dialogowe, kliknij przycisk **odnajdowania**.

     Visual Studio wyszukiwania w bieżącym rozwiązaniu dostępne usługi i dodaje `AdventureWorksService.svc` do listy dostępnych usług w **usług** pole.

9. W **Namespace** wpisz `AdventureWorksService`.

10. W **usług** kliknij **AdventureWorksService.svc**, a następnie kliknij przycisk **OK**.

     Visual Studio pobierze informacje usługi, a następnie zwraca do **konfiguracji źródła danych** kreatora.

11. W **Dodaj odwołanie do usługi** kliknij przycisk **Zakończ**.

     Visual Studio dodaje węzły, które reprezentują danych zwróconych przez usługę **źródeł danych** okna.

## <a name="define-the-user-interface-of-the-window"></a>Zdefiniuj okna interfejsu użytkownika
Dodawanie przycisków kilka do okna, modyfikując XAML w Projektancie WPF. W dalszej części tego przewodnika należy dodać kodu, która umożliwia użytkownikom wyświetlanie i aktualizowanie sprzedaży rekordów przy użyciu tych przycisków.

### <a name="to-create-the-window-layout"></a>Aby utworzyć układ okna

1.  W **Eksploratora rozwiązań**, kliknij dwukrotnie **MainWindow.xaml**.

     Okno zostanie otwarty w Projektancie WPF.

2.  W [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] wyświetlić projektanta, Dodaj następujący kod między `<Grid>` tagów:

    ```xaml
    <Grid.RowDefinitions>
        <RowDefinition Height="75" />
        <RowDefinition Height="525" />
    </Grid.RowDefinitions>
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
    ```

3.  Skompiluj projekt.

## <a name="create-the-data-bound-controls"></a>Tworzenie formantów powiązanych z danymi
Tworzenie formantów, które Wyświetl rekordy klientów, przeciągając `SalesOrderHeaders` węzła z **źródeł danych** okna do projektanta.

### <a name="to-create-the-data-bound-controls"></a>Aby utworzyć formanty powiązane z danymi

1.  W **źródeł danych** okna, kliknij menu rozwijane dla **SalesOrderHeaders** , a następnie wybierz węzeł **szczegóły**.

2.  Rozwiń węzeł **SalesOrderHeaders** węzła.

3.  Na przykład niektóre pola nie będą wyświetlane, więc kliknij menu rozwijanym obok następujące węzły i wybierz **Brak**:

    -   **CreditCardApprovalCode**

    -   **Data modyfikacji**

    -   **OnlineOrderFlag**

    -   **RevisionNumber**

    -   **ROWGUID**

    Ta akcja uniemożliwia tworzenie formantów powiązanych z danymi dla tych węzłów w następnym kroku Visual Studio. W ramach tego przewodnika założono, że użytkownik końcowy nie musi do wyświetlania tych danych.

4.  Z **źródeł danych** okna, przeciągnij **SalesOrderHeaders** węzła do wiersza siatki, w obszarze wiersza, który zawiera przyciski.

     Visual Studio generuje XAML i kod, który tworzy zestaw kontrolek, które są powiązane z danymi w **produktu** tabeli. Aby uzyskać więcej informacji na temat wygenerowanego XAML i kodem, zobacz [kontrolki powiązania WPF z danymi w Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

5.  W projektancie, kliknij pole tekstowe **identyfikator klienta** etykiety.

6.  W **właściwości** okna, zaznacz pole wyboru obok pozycji **IsReadOnly** właściwości.

7.  Ustaw **IsReadOnly** właściwości dla każdego z poniższych polach tekstowych:

    -   **Numer zamówienia zakupu**

    -   **Identyfikator zamówienia sprzedaży**

    -   **Numer zamówienia sprzedaży**

## <a name="load-the-data-from-the-service"></a>Ładowanie danych z usługi
Obiekt serwera proxy usługi używany do ładowania danych sprzedaży z usługi. Następnie przypisz zwróconych danych do źródła danych <xref:System.Windows.Data.CollectionViewSource> w oknie WPF.

### <a name="to-load-the-data-from-the-service"></a>Aby załadować dane z usługi

1.  W projektancie, aby utworzyć `Window_Loaded` program obsługi zdarzeń, kliknij dwukrotnie tekst, który brzmi: **właściwości MainWindow**.

2.  Zastąp następujący kod obsługi zdarzeń. Upewnij się, że zastępuje *localhost* adres w tym kodzie adres hosta lokalnego na komputerze deweloperskim.

     [!code-csharp[Data_WPFWCF#2](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_2.cs)]
     [!code-vb[Data_WPFWCF#2](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_2.vb)]

## <a name="navigate-sales-records"></a>Przejdź rekordy sprzedaży
Dodaj kod, który umożliwia przewijanie rekordów sprzedaży przy użyciu **\<** i **>** przycisków.

### <a name="to-enable-users-to-navigate-sales-records"></a>Aby umożliwić użytkownikom przechodzenie rekordy sprzedaży

1.  W projektancie, kliknij dwukrotnie **<** przycisk na powierzchni okna.

     Visual Studio otworzy plik CodeBehind i tworzy nowy `backButton_Click` programu obsługi zdarzeń dla <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń.

2.  Dodaj następujący kod do wygenerowanej `backButton_Click` obsługi zdarzeń:

     [!code-csharp[Data_WPFWCF#3](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_3.cs)]
     [!code-vb[Data_WPFWCF#3](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_3.vb)]

3.  Powrót do projektanta, a następnie kliknij dwukrotnie **>** przycisku.

     Visual Studio otworzy plik CodeBehind i tworzy nowy `nextButton_Click` programu obsługi zdarzeń dla <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń.

4.  Dodaj następujący kod do wygenerowanej `nextButton_Click` obsługi zdarzeń:

     [!code-csharp[Data_WPFWCF#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_4.cs)]
     [!code-vb[Data_WPFWCF#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_4.vb)]

## <a name="saving-changes-to-sales-records"></a>Zapisywanie zmian rekordów sprzedaży
Dodaj kod, który umożliwia użytkownikom do wyświetlenia i zapisać zmiany w sprzedaży rekordów przy użyciu **zapisać zmiany** przycisku.

### <a name="to-add-the-ability-to-save-changes-to-sales-records"></a>Aby dodać możliwość zapisywania zmian w sprzedaży rekordów

1.  W projektancie, kliknij dwukrotnie **Zapisz zmiany** przycisku.

     Visual Studio otworzy plik CodeBehind i tworzy nowy `saveButton_Click` programu obsługi zdarzeń dla <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń.

2.  Dodaj następujący kod do `saveButton_Click` obsługi zdarzeń.

     [!code-csharp[Data_WPFWCF#5](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_5.cs)]
     [!code-vb[Data_WPFWCF#5](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_5.vb)]

## <a name="testing-the-application"></a>Testowanie aplikacji
Skompiluj i uruchom aplikację, aby sprawdzić, czy można wyświetlać i aktualizować rekordów klientów.

### <a name="to-test-the-application"></a>Aby przetestować aplikację

1.  Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**. Upewnij się, że rozwiązanie kompilacje bez błędów.

2.  Naciśnij klawisz **klawisze Ctrl + F5**.

     Uruchamia program Visual Studio **AdventureWorksService** projekt bez debugowania go.

3.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **AdventureWorksSalesEditor** projektu.

4.  W menu kontekstowym w obszarze **debugowania**, kliknij przycisk **Start nowe wystąpienie**.

     Aplikacja zostanie uruchomiona. Sprawdź następujące informacje:

    -   Pola tekstowe wyświetlać różne pola danych z pierwszego rekordu sprzedaży ma identyfikator zamówienia **71774**.

    -   Możesz kliknąć **>** lub **<** przyciski poruszać się po inne rekordy sprzedaży.

5.  W jednym z rekordów sprzedaży, wpisz dowolny tekst w **komentarz** , a następnie kliknij przycisk **zapisać zmiany**.

6.  Zamknij aplikację, a następnie ponownie uruchom aplikację w programie Visual Studio.

7.  Przejdź do rekordu sprzedaży, który został zmodyfikowany, a następnie sprawdź, czy zmiana będzie nadal występować po Zamknij i otwórz ponownie aplikację.

8.  Zamknij aplikację.

## <a name="next-steps"></a>Następne kroki

Po ukończeniu tego przewodnika, można wykonać następujące zadania:

-   Dowiedz się, jak używać **źródeł danych** okna w Visual Studio, aby powiązać WPF kontrolki na inne typy źródeł danych. Aby uzyskać więcej informacji, zobacz [kontrolki powiązania WPF z zestawem danych](../data-tools/bind-wpf-controls-to-a-dataset.md).

-   Dowiedz się, jak używać **źródeł danych** okna w programie Visual Studio, aby wyświetlić powiązane danych (to znaczy w relacji nadrzędny podrzędny) formantów WPF. Aby uzyskać więcej informacji, zobacz [wskazówki: wyświetlanie powiązanych danych w aplikacji WPF](../data-tools/display-related-data-in-wpf-applications.md).

## <a name="see-also"></a>Zobacz także

- [Powiązanie formantów WPF z danymi w Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Powiązywanie kontrolek WPF z zestawem danych](../data-tools/bind-wpf-controls-to-a-dataset.md)
- [Omówienie WCF (.NET Framework)](/dotnet/framework/data/wcf/wcf-data-services-overview)
- [Omówienie struktury jednostek (.NET Framework)](/dotnet/framework/data/adonet/ef/overview)
- [Omówienie (.NET Framework) powiązanie danych](/dotnet/framework/wpf/data/data-binding-overview)