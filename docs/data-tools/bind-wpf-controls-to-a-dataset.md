---
title: "Powiązanie formantów WPF z zestawem danych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 177420b9-568b-4dad-9d16-1b0e98a24d71
caps.latest.revision: "32"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: d7609215f7145ae05d978ba10d556782c886ee3b
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2017
---
# <a name="bind-wpf-controls-to-a-dataset"></a>Powiązanie formantów WPF z zestawem danych
W tym przewodniku spowoduje utworzenie aplikacji WPF, który zawiera formanty powiązane z danymi. Formanty są powiązane z rekordów produktów, które znajdują się w zestawie danych. Zostanie również dodawanie przycisków do przeglądania produktów i Zapisz zmiany w rekordach produktu.  
  
W instruktażu przedstawiono następujące zagadnienia:  
  
- Tworzenie aplikacji WPF i zestawu danych, który jest generowany na podstawie danych w bazie danych AdventureWorksLT.  
  
- Tworzenie zestawu formantów powiązanych z danymi przez przeciągnięcie tabeli danych z **źródeł danych** okna do okna Projektanta WPF.  
  
- Tworzenie przycisków nawigowania rekordów produktu do przodu i do tyłu.  
  
- Utworzenie przycisku, który zapisuje zmiany wprowadzone przez użytkownika do rekordów produktu do tabeli danych i źródle danych.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
  
-   Dostęp do działającego wystąpienia programu SQL Server lub SQL Server Express z AdventureWorksLT przykładowej bazy danych do niego dołączony. Możesz pobrać bazę danych AdventureWorksLT z [witryny sieci Web w witrynie CodePlex](http://go.microsoft.com/fwlink/?linkid=87843).  
  
Znajomość następujące pojęcia jest również przydatna, ale nie są wymagane do ukończenia Instruktaż:  
  
-   Zestawy danych i TableAdapters. Aby uzyskać więcej informacji, zobacz [narzędzia zestawu danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md) i [TableAdapter](../data-tools/create-and-configure-tableadapters.md).  
  
-   Praca z projektanta WPF. Aby uzyskać więcej informacji, zobacz [Omówienie projektanta Silverlight i WPF](http://msdn.microsoft.com/en-us/570b7a5c-0c86-4326-a371-c9b63378fc62).  
  
-   Powiązanie danych WPF. Aby uzyskać więcej informacji, zobacz [omówienie powiązania danych](/dotnet/framework/wpf/data/data-binding-overview).  
  
## <a name="create-the-project"></a>Utwórz projekt  
 Utwórz nowy projekt WPF. Projekt spowoduje wyświetlenie rekordów produktu.  
  
#### <a name="to-create-the-project"></a>Aby utworzyć projekt  
  
1.  Uruchom program Visual Studio.  
  
2.  Na **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu**.  
  
3.  Rozwiń węzeł **Visual Basic** lub **Visual C#**, a następnie wybierz **Windows**.  
  
4.  Wybierz **aplikacji WPF** szablonu projektu.  
  
5.  W **nazwa** wpisz `AdventureWorksProductsEditor` i kliknij przycisk **OK**.  
  
     Program Visual Studio tworzy `AdventureWorksProductsEditor` projektu.  
  
## <a name="create-a-dataset-for-the-application"></a>Tworzenie zestawu danych dla aplikacji  
 Przed utworzeniem formantów powiązanych z danymi musi definiować modelu danych dla aplikacji i dodaj go do **źródeł danych** okna. W tym przewodniku możesz utworzyć zestaw danych do użycia jako modelu danych.  
  
#### <a name="to-create-a-dataset"></a>Można utworzyć zestawu danych  
  
1.  Na **danych** menu, kliknij przycisk **Pokaż źródeł danych**.  
  
     **Źródeł danych** zostanie otwarte okno.  
  
2.  W **źródeł danych** okna, kliknij przycisk **Dodaj nowe źródło danych**.  
  
     **Konfiguracji źródła danych** zostanie otwarty Kreator.  
  
3.  Na **wybierz typ źródła danych** wybierz pozycję **bazy danych**, a następnie kliknij przycisk **dalej**.  
  
4.  Na **wybierz Model bazy danych** wybierz pozycję **Dataset**, a następnie kliknij przycisk **dalej**.  
  
5.  Na **wybierz połączenie danych** wybierz jedną z następujących opcji:  
  
    -   Jeśli połączenie danych z przykładową bazę danych AdventureWorksLT jest dostępny na liście rozwijanej, zaznacz go, a następnie kliknij przycisk **dalej**.  
  
    -   Kliknij przycisk **nowe połączenie**oraz tworzenie połączenia z bazą danych AdventureWorksLT.  
  
6.  Na **zapisać parametry połączenia do pliku konfigurowania aplikacji** wybierz pozycję **tak, Zapisz połączenie jako** pole wyboru, a następnie kliknij przycisk **dalej**.  
  
7.  Na **wybierz obiekty bazy danych użytkownika** rozwiń pozycję **tabel**, a następnie wybierz **produktu (SalesLT)** tabeli.  
  
8.  Kliknij przycisk **Zakończ**.  
  
     Dodaje nowy program Visual Studio `AdventureWorksLTDataSet.xsd` dodaje plik do projektu, a odpowiadające mu **AdventureWorksLTDataSet** elementu do **źródeł danych** okna. `AdventureWorksLTDataSet.xsd` Plik definiuje typizowanego zestaw danych o nazwie `AdventureWorksLTDataSet` i TableAdapter o nazwie `ProductTableAdapter`. W dalszej części tego przewodnika, którego użyjesz `ProductTableAdapter` wypełnić dataset z danymi i zapisać zmiany w bazie danych.  
  
9. Skompiluj projekt.  
  
## <a name="edit-the-default-fill-method-of-the-tableadapter"></a>Edytuj wypełnienia domyślną metodę TableAdapter  
 Aby wypełnić dataset z danymi, użyj `Fill` metody `ProductTableAdapter`. Domyślnie `Fill` wypełnienia metody `ProductDataTable` w `AdventureWorksLTDataSet` z wszystkich wierszy danych z tabeli produktu. Można zmodyfikować tę metodę, aby zwrócić tylko podzbiór wierszy. W ramach tego przewodnika należy zmodyfikować `Fill` metodę, aby zwrócić tylko wiersze, dla produktów, które mają zdjęć.  
  
#### <a name="to-load-product-rows-that-have-photos"></a>Aby załadować wierszy produktu, które mają zdjęć  
  
1.  W **Eksploratora rozwiązań**, kliknij dwukrotnie `AdventureWorksLTDataSet.xsd` pliku.  
  
     Zostanie otwarty projektant obiektów Dataset.  
  
2.  W projektancie, kliknij prawym przyciskiem myszy **wypełnienia GetData()** zapytań i wybierz **Konfiguruj**.  
  
     **Konfiguracji TableAdapter** zostanie otwarty Kreator.  
  
3.  W **wprowadź instrukcję SQL** Dodaj następującą klauzulę WHERE po `SELECT` instrukcji w polu tekstowym.  
  
    ```  
    WHERE ThumbnailPhotoFileName <> 'no_image_available_small.gif'  
    ```  
  
4.  Kliknij przycisk **Zakończ**.  
  
## <a name="define-the-user-interface"></a>Definiowanie interfejsu użytkownika  
 Dodawanie przycisków kilka do okna, modyfikując XAML w Projektancie WPF. W dalszej części tego przewodnika należy dodać kodu, który umożliwia przewijanie za pośrednictwem, a następnie zapisz zmiany rekordów produktów za pomocą tych przycisków.  
  
#### <a name="to-define-the-user-interface-of-the-window"></a>Aby zdefiniować okna interfejsu użytkownika  
  
1.  W **Eksploratora rozwiązań**, kliknij dwukrotnie MainWindow.xaml.  
  
     Okno zostanie otwarty w Projektancie WPF.  
  
2.  W [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] wyświetlić projektanta, Dodaj następujący kod między `<Grid>` tagów:  
  
    ```xaml  
    <Grid.RowDefinitions>  
        <RowDefinition Height="75" />  
        <RowDefinition Height="625" />  
    </Grid.RowDefinitions>  
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>  
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>  
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>  
    ```  
  
3.  Skompiluj projekt.  
  
## <a name="create-data-bound-controls"></a>Tworzenie formantów powiązanych z danymi  
 Tworzenie formantów, które Wyświetl rekordy klientów, przeciągając `Product` tabeli **źródeł danych** okna Projektanta WPF.  
  
#### <a name="to-create-data-bound-controls"></a>Aby utworzyć formanty powiązane z danymi  
  
1.  W **źródeł danych** okna, kliknij menu rozwijane dla **produktu** a następnie wybierz węzeł **szczegóły**.  
  
2.  Rozwiń węzeł **produktu** węzła.  
  
3.  Na przykład niektóre pola nie będą wyświetlane, więc kliknij menu rozwijanym obok następujące węzły i wybierz **Brak**:  
  
    -   ProductCategoryID  
  
    -   ProductModelID  
  
    -   ThumbnailPhotoFileName  
  
    -   ROWGUID  
  
    -   Data modyfikacji  
  
4.  Kliknij menu rozwijane **ThumbNailPhoto** a następnie wybierz węzeł **obrazu**.  
  
    > [!NOTE]
    >  Domyślnie elementy w **źródeł danych** okna, które reprezentują obrazy mają kontrolę domyślną wartość **Brak**. To dlatego obrazy są przechowywane jako tablice typu byte w bazach danych i tablice typu byte może zawierać wszystko, od prostego tablicę bajtów do pliku wykonywalnego dużych aplikacji.  
  
5.  Z **źródeł danych** okna, przeciągnij **produktu** węzła do wiersza siatki, w obszarze wiersza, który zawiera przyciski.  
  
     Visual Studio generuje XAML, który definiuje zestaw kontrolek, które są powiązane z danymi w **produktów** tabeli. Generuje kod, który ładuje dane. Aby uzyskać więcej informacji na temat wygenerowanego XAML i kodem, zobacz [kontrolki powiązania WPF z danymi w Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).  
  
6.  W projektancie, kliknij pole tekstowe **identyfikator produktu** etykiety.  
  
7.  W **właściwości** okna, zaznacz pole wyboru obok pozycji **IsReadOnly** właściwości.  
  
## <a name="navigating-product-records"></a>Nawigowanie po rekordów produktu  
 Dodaj kod, który umożliwia przewijanie rekordów produktu za pomocą  **\<**  i  **>**  przycisków.  
  
#### <a name="to-enable-users-to-navigate-product-records"></a>Aby umożliwić użytkownikom Przejdź rekordów produktu  
  
1.  W projektancie, kliknij dwukrotnie  **<**  przycisk na powierzchni okna.  
  
     Visual Studio otworzy plik CodeBehind i tworzy nowy `backButton_Click` programu obsługi zdarzeń dla <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń.  
  
2.  Modyfikowanie `Window_Loaded` program obsługi zdarzeń, więc `ProductViewSource`, `AdventureWorksLTDataSet`, i `AdventureWorksLTDataSetProductTableAdapter` są poza metodą i jest dostępny dla całego formularza. Deklarowanie tylko te było globalne do formularza i przypisać je w ramach `Window_Loaded` obsługi zdarzenia podobne do następujących:  
  
     [!code-csharp[Data_WPFDATASET#1](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_1.cs)]
     [!code-vb[Data_WPFDATASET#1](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_1.vb)]  
  
3.  Dodaj następujący kod do `backButton_Click` obsługi zdarzeń:  
  
     [!code-csharp[Data_WPFDATASET#2](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_2.cs)]
     [!code-vb[Data_WPFDATASET#2](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_2.vb)]  
  
4.  Powrót do projektanta i kliknij dwukrotnie  **>**  przycisku.  
  
5.  Dodaj następujący kod do `nextButton_Click` obsługi zdarzeń:  
  
     [!code-csharp[Data_WPFDATASET#3](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_3.cs)]
     [!code-vb[Data_WPFDATASET#3](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_3.vb)]  
  
## <a name="save-changes-to-product-records"></a>Zapisz zmiany w rekordach produktu  
Dodaj kod, który umożliwia użytkownikom zapisać zmiany rekordów produktu za pomocą **zapisać zmiany** przycisku.  
  
#### <a name="to-add-the-ability-to-save-changes-to-product-records"></a>Aby dodać możliwość zapisania zmian rekordów produktu  
  
1.  W projektancie, kliknij dwukrotnie **zapisać zmiany** przycisku.  
  
     Visual Studio otworzy plik CodeBehind i tworzy nowy `saveButton_Click` programu obsługi zdarzeń dla <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń.  
  
2.  Dodaj następujący kod do `saveButton_Click` obsługi zdarzeń:  
  
     [!code-csharp[Data_WPFDATASET#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_4.cs)]
     [!code-vb[Data_WPFDATASET#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_4.vb)]  
  
    > [!NOTE]
    >  W tym przykładzie użyto `Save` metody `TableAdapter` Aby zapisać zmiany. Ta opcja jest odpowiednia w tym przewodniku, ponieważ tylko jeden danych tabeli został zmieniony. Jeśli chcesz zapisać zmiany z wieloma tabelami danych, możesz także użyć `UpdateAll` metody `TableAdapterManager` generujący Visual Studio z zestawu danych. Aby uzyskać więcej informacji, zobacz [TableAdapters](../data-tools/create-and-configure-tableadapters.md).  
  
## <a name="test-the-application"></a>Testowanie aplikacji  
 Skompiluj i uruchom aplikację. Sprawdź, czy można wyświetlać i aktualizować rekordy produktu.  
  
#### <a name="to-test-the-application"></a>Aby przetestować aplikację  
  
1.  Naciśnij klawisz **F5**.  
  
     Aplikacja kompiluje i uruchamia. Sprawdź następujące informacje:  
  
    -   Pola tekstowe są wyświetlane dane z pierwszego rekordu produktu, który ma zdjęcie. Ten produkt ma produktu 713 identyfikator i nazwa **Long kopertą Jersey Logo, S**.  
  
    -   Możesz kliknąć  **>**  lub  **<**  przyciski poruszać się po inne rekordy produktu.  
  
2.  W jednym z rekordów produktu, zmień **rozmiar** wartość, a następnie kliknij przycisk **zapisać zmiany**.  
  
3.  Zamknij aplikację, a następnie ponownie uruchom aplikację, naciskając klawisz **F5** w programie Visual Studio.  
  
4.  Przejdź do rekordu produktu, który został zmieniony i sprawdź, czy zmiana jest trwała.  
  
5.  Zamknij aplikację.  
  
## <a name="next-steps"></a>Następne kroki  
 Po ukończeniu tego przewodnika, można wykonać następujące zadania:  
  
-   Dowiedz się, jak używać **źródeł danych** okna w Visual Studio, aby powiązać WPF kontrolki na inne typy źródeł danych. Aby uzyskać więcej informacji, zobacz [powiązania WPF kontrolki do usługi danych WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).  
  
-   Dowiedz się, jak używać **źródeł danych** okna w programie Visual Studio, aby wyświetlić powiązane danych (to znaczy w relacji nadrzędny podrzędny) formantów WPF. Aby uzyskać więcej informacji, zobacz [wskazówki: wyświetlanie powiązanych danych w aplikacji WPF](../data-tools/display-related-data-in-wpf-applications.md).  
  
## <a name="see-also"></a>Zobacz także
[Powiązanie formantów WPF z danymi w Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)   
[Narzędzia zestawu danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)   
[Omówienie projektanta Silverlight i WPF](http://msdn.microsoft.com/en-us/570b7a5c-0c86-4326-a371-c9b63378fc62)   
[Omówienie powiązania danych](/dotnet/framework/wpf/data/data-binding-overview)