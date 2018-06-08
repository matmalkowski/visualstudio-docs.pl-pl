---
title: 'Wskazówki: Zmiana danych z pamięci podręcznej skoroszytu na serwerze'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks [Office development in Visual Studio], changing server data
- datasets [Office development in Visual Studio], accessing on server
- server-side data access [Office development in Visual Studio]
- data [Office development in Visual Studio], accessing on server
- documents [Office development in Visual Studio], server-side data access
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6c46d0eeedfbfa1a9e25d3a89fdade3c923dac7a
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34845668"
---
# <a name="walkthrough-change-cached-data-in-a-workbook-on-a-server"></a>Wskazówki: Zmiana danych z pamięci podręcznej skoroszytu na serwerze
  W tym przewodniku pokazano, jak można zmodyfikować zestawu danych, który jest w pamięci podręcznej programu Microsoft Excel pakietu Office bez uruchamiania programu Excel za pomocą <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Definiowanie zestawu danych, który zawiera dane z bazy danych AdventureWorksLT.  
  
-   Tworzenie wystąpień zestawu danych w projekcie skoroszytu programu Excel i projekt aplikacji konsoli.  
  
-   Tworzenie <xref:Microsoft.Office.Tools.Excel.ListObject> jest powiązana z zestawu danych w skoroszycie i wypełnianie <xref:Microsoft.Office.Tools.Excel.ListObject> danych podczas otwierania skoroszytu.  
  
-   Dodawanie zestawu danych w skoroszycie do pamięci podręcznej danych.  
  
-   Modyfikowanie kolumny danych w pamięci podręcznej zestawu danych, uruchamiając kod w aplikacji konsoli bez uruchamiania programu Excel.  
  
 Mimo że w tym przewodniku przyjęto założenie, że uruchamiasz kodu na komputerze deweloperskim, kodu zostało to pokazane w tym przewodniku można użyć na serwerze, który nie ma zainstalowanego programu Excel.  
  
> [!NOTE]  
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Dostęp do działającego wystąpienia programu Microsoft SQL Server lub programu Microsoft SQL Server Express zawierający AdventureWorksLT przykładowej bazy danych do niego dołączony. Możesz pobrać bazę danych AdventureWorksLT z [witryny sieci Web w witrynie CodePlex](http://go.microsoft.com/fwlink/?linkid=87843). Aby uzyskać więcej informacji na temat dołączania bazy danych zobacz następujące tematy:  
  
    -   Aby dołączyć bazę danych przy użyciu programu SQL Server Management Studio lub SQL Server Management Studio Express, zobacz [porady: dołączanie bazy danych (SQL Server Management Studio)](http://msdn.microsoft.com/en-us/b4efb0ae-cfe6-4d81-a4b4-6e4916885caa).  
  
    -   Aby dołączyć bazę danych przy użyciu wiersza polecenia, zobacz [porady: dołączanie pliku bazy danych do programu SQL Server Express](http://msdn.microsoft.com/en-us/0f8e42b5-7a8c-4c30-8c98-7d2bdc8dcc68).  
  
## <a name="create-a-class-library-project-that-defines-a-dataset"></a>Tworzenie projektu biblioteki klas, który definiuje zestaw danych  
 Aby użyć tego samego zestawu danych w projekcie skoroszytu programu Excel i aplikacji konsoli, należy zdefiniować element dataset w osobny zestaw, do którego odwołuje się obu tych projektów. W ramach tego przewodnika Definiowanie zestawu danych w projektach biblioteki klas.  
  
### <a name="to-create-the-class-library-project"></a>Aby utworzyć projektu biblioteki klas  
  
1.  Uruchom [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Na **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu**.  
  
3.  W okienku szablonów rozwiń **Visual C#** lub **Visual Basic**, a następnie kliknij przycisk **Windows**.  
  
4.  Na liście szablony projektów, wybierz **biblioteki klas**.  
  
5.  W **nazwa** wpisz **AdventureWorksDataSet**.  
  
6.  Kliknij przycisk **Przeglądaj**, przejdź do Twojej *%UserProfile%\My dokumenty* (dla systemu Windows XP i starszych) lub *%UserProfile%\Documents* (dla systemu Windows Vista) folderu, a następnie kliknij przycisk **Wybierz Folder**.  
  
7.  W **nowy projekt** okna dialogowego Sprawdź, czy **Utwórz katalog rozwiązania** nie zaznaczono pola wyboru.  
  
8.  Kliknij przycisk **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje **AdventureWorksDataSet** projektu do **Eksploratora rozwiązań** i otwiera **Class1.cs** lub **Class1.vb** pliku kodu.  
  
9. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Class1.cs** lub **Class1.vb**, a następnie kliknij przycisk **usunąć**. Nie trzeba tego pliku w ramach tego przewodnika.  
  
## <a name="define-a-dataset-in-the-class-library-project"></a>Definiowanie zestawu danych w projektu biblioteki klas  
 Zdefiniuj typizowanego zestaw danych, który zawiera dane z bazy danych AdventureWorksLT dla programu SQL Server 2005. W dalszej części tego przewodnika będzie odwoływać ten zestaw danych z projektu skoroszyt programu Excel i projekt aplikacji konsoli.  
  
 Zestaw danych jest *wpisane dataset* reprezentujący dane w tabeli Produkty bazy danych AdventureWorksLT. Aby uzyskać więcej informacji na temat typizowane zbiory danych, zobacz [narzędzia zestawu danych w programie Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).  
  
### <a name="to-define-a-typed-dataset-in-the-class-library-project"></a>Aby zdefiniować typizowanego obiektu dataset w projektu biblioteki klas  
  
1.  W **Eksploratora rozwiązań**, kliknij przycisk **AdventureWorksDataSet** projektu.  
  
2.  Jeśli **źródeł danych** okna nie jest widoczne, wyświetl ją, z menu, wybierając **widoku** > **inne okna**  >   **Źródła danych**.  
  
3.  Wybierz **Dodaj nowe źródło danych** uruchomić **Kreator konfiguracji źródła danych**.  
  
4.  Kliknij przycisk **bazy danych**, a następnie kliknij przycisk **dalej**.  
  
5.  Jeśli masz istniejące połączenie z bazą danych AdventureWorksLT, wybierz to połączenie i kliknij przycisk **dalej**.  
  
     W przeciwnym razie kliknij przycisk **nowe połączenie**i użyj **Dodawanie połączenia** okno dialogowe, aby utworzyć nowe połączenie. Aby uzyskać więcej informacji, zobacz [dodać nowe połączenia](../data-tools/add-new-connections.md).  
  
6.  W **zapisać parametry połączenia do pliku konfiguracji aplikacji** kliknij przycisk **dalej**.  
  
7.  W **wybierz obiekty bazy danych użytkownika** rozwiń pozycję **tabel** i wybierz **produktu (SalesLT)**.  
  
8.  Kliknij przycisk **Zakończ**.  
  
     *AdventureWorksLTDataSet.xsd* plik zostanie dodany do **AdventureWorksDataSet** projektu. Ten plik definiuje następujące elementy:  
  
    -   Typizowanego zestaw danych o nazwie `AdventureWorksLTDataSet`. Ten zestaw danych reprezentuje zawartość tabeli produktu w bazie danych AdventureWorksLT.  
  
    -   TableAdapter o nazwie `ProductTableAdapter`. Ten obiekt TableAdapter może służyć do odczytywania i zapisywania danych `AdventureWorksLTDataSet`. Aby uzyskać więcej informacji, zobacz [TableAdapter — Przegląd](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).  
  
     Użyje obu tych obiektów w dalszej części tego przewodnika.  
  
9. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **AdventureWorksDataSet** i kliknij przycisk **kompilacji**.  
  
     Upewnij się, że projekt tworzy się bez błędów.  
  
## <a name="create-an-excel-workbook-project"></a>Tworzenie projektu skoroszyt programu Excel  
 Tworzenie projektu skoroszyt programu Excel dla interfejsu do danych. W dalszej części tego przewodnika, utworzysz <xref:Microsoft.Office.Tools.Excel.ListObject> wyświetlający danych i wystąpienia zestawu danych zostaną dodane do pamięci podręcznej danych w skoroszycie.  
  
### <a name="to-create-the-excel-workbook-project"></a>Aby utworzyć projekt skoroszytu programu Excel  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **AdventureWorksDataSet** rozwiązania, wskaż **Dodaj**, a następnie kliknij przycisk **nowy projekt**.  
  
2.  W okienku szablonów rozwiń **Visual C#** lub **Visual Basic**, a następnie rozwiń węzeł **Office**.  
  
3.  Pod rozwiniętym **Office** węzła, wybierz opcję **2010** węzła.  
  
4.  Na liście szablony projektów wybierz projektu skoroszyt programu Excel.  
  
5.  W **nazwa** wpisz **AdventureWorksReport**. Nie należy modyfikować lokalizację.  
  
6.  Kliknij przycisk **OK**.  
  
     **Visual Studio Tools dla pakietu Office, Kreator projektu** otwiera.  
  
7.  Upewnij się, że **Utwórz nowy dokument** jest zaznaczone, a następnie kliknij przycisk **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Otwiera **AdventureWorksReport** skoroszytu w Projektancie i dodaje **AdventureWorksReport** projektu do **Eksploratora rozwiązań**.  
  
## <a name="add-the-dataset-to-data-sources-in-the-excel-workbook-project"></a>Dodaj zestaw danych ze źródłami danych w projekcie skoroszytu programu Excel  
 Aby wyświetlić zestaw danych w skoroszycie programu Excel, najpierw należy dodać zestaw danych ze źródłami danych w projekcie skoroszytu programu Excel.  
  
### <a name="to-add-the-dataset-to-the-data-sources-in-the-excel-workbook-project"></a>Aby dodać zestaw danych do źródła danych w projekcie skoroszytu programu Excel  
  
1.  W **Eksploratora rozwiązań**, kliknij dwukrotnie **Sheet1.cs** lub **Sheet1.vb** w obszarze **AdventureWorksReport** projektu.  
  
     Skoroszyt zostanie otwarty w projektancie.  
  
2.  Na **danych** menu, kliknij przycisk **Dodaj nowe źródło danych**.  
  
     **Kreator konfiguracji źródła danych** otwiera.  
  
3.  Kliknij przycisk **obiektu**, a następnie kliknij przycisk **dalej**.  
  
4.  W **wybierz obiekt ma zostać powiązania** kliknij przycisk **Dodaj odwołanie**.  
  
5.  Na **projekty** , kliknij pozycję **AdventureWorksDataSet** , a następnie kliknij przycisk **OK**.  
  
6.  W obszarze **AdventureWorksDataSet** przestrzeń nazw **AdventureWorksDataSet** zestawu, kliknij przycisk **AdventureWorksLTDataSet** , a następnie kliknij przycisk **Zakończ** .  
  
     **Źródeł danych** zostanie otwarte okno i **AdventureWorksLTDataSet** zostanie dodany do listy źródeł danych.  
  
## <a name="create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Utwórz ListObject, który jest powiązany z wystąpieniem zestawu danych  
 Aby wyświetlić zestaw danych w skoroszycie, Utwórz <xref:Microsoft.Office.Tools.Excel.ListObject> który jest powiązany z wystąpieniem elementu dataset. Aby uzyskać więcej informacji na temat powiązanie kontrolek z danymi, zobacz [wiązanie danych do formantów w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
### <a name="to-create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Aby utworzyć ListObject, który jest powiązany z wystąpieniem zestawu danych  
  
1.  W **źródeł danych** okna, rozwiń węzeł **AdventureWorksLTDataSet** węźle **AdventureWorksDataSet**.  
  
2.  Wybierz **produktu** węzła, kliknij strzałkę listy rozwijanej, która jest wyświetlana, a następnie wybierz **ListObject** na liście rozwijanej.  
  
     Jeśli nie ma strzałkę listy rozwijanej, upewnij się, że skoroszyt jest otwarty w projektancie.  
  
3.  Przeciągnij **produktu** tabeli do komórki A1.  
  
     A <xref:Microsoft.Office.Tools.Excel.ListObject> formantu o nazwie `productListObject` jest tworzony w arkuszu, począwszy od komórki A1. Jednocześnie, obiekt zestawu danych o nazwie `adventureWorksLTDataSet` i <xref:System.Windows.Forms.BindingSource> o nazwie `productBindingSource` zostaną dodane do projektu. <xref:Microsoft.Office.Tools.Excel.ListObject> Jest powiązany z <xref:System.Windows.Forms.BindingSource>, która z kolei jest powiązana z obiektem zestawu danych.  
  
## <a name="add-the-dataset-to-the-data-cache"></a>Dodaj zestaw danych do pamięci podręcznej danych  
 Aby włączyć kod spoza projektu skoroszyt programu Excel do zestawu danych w skoroszycie, należy dodać zestaw danych do pamięci podręcznej danych. Aby uzyskać więcej informacji o pamięci podręcznej danych, zobacz [buforowane dane w dostosowaniach na poziomie dokumentu](../vsto/cached-data-in-document-level-customizations.md) i [dane z pamięci podręcznej](../vsto/caching-data.md).  
  
### <a name="to-add-the-dataset-to-the-data-cache"></a>Aby dodać zestaw danych do pamięci podręcznej danych  
  
1.  W projektancie, kliknij **adventureWorksLTDataSet**.  
  
2.  W **właściwości** ustaw **Modyfikatory** właściwości **publicznego**.  
  
3.  Ustaw **CacheInDocument** właściwości **True**.  
  
## <a name="initialize-the-dataset-in-the-workbook"></a>Inicjowanie zestawu danych w skoroszycie  
 Zanim będzie można pobrać danych z pamięci podręcznej zestawu danych za pomocą aplikacji konsoli, należy najpierw wypełnienia pamięci podręcznej zestawu danych z danymi.  
  
### <a name="to-initialize-the-dataset-in-the-workbook"></a>Aby zainicjować zestawu danych w skoroszycie  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Sheet1.cs** lub **Sheet1.vb** plik i kliknij przycisk **kod widoku**.  
  
2.  Zastąp `Sheet1_Startup` obsługi zdarzeń z następującym kodem. Ten kod używa wystąpienia `ProductTableAdapter` klasy, która jest zdefiniowana w **AdventureWorksDataSet** projektu do wypełnienia pamięci podręcznej zestawu danych za pomocą danych, jeśli jest obecnie pusta.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/CSharp/AdventureWorksDataSet/AdventureWorksReport/Sheet1.cs#8)]
     [!code-vb[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/AdventureWorksReport/Sheet1.vb#8)]  
  
## <a name="checkpoint"></a>Punkt kontrolny  
 Tworzenie i uruchamianie projektu skoroszytu programu Excel, aby upewnić się, że kompiluje i uruchamia bez błędów. Ta operacja również wypełnienia pamięci podręcznej zestawu danych i zapisuje dane w skoroszycie.  
  
### <a name="to-build-and-run-the-project"></a>Aby skompilować i uruchomić projekt  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **AdventureWorksReport** projektu, wybierz **debugowania**, a następnie kliknij przycisk **Start nowe wystąpienie**.  
  
     Projekt jest budowany i otwiera skoroszyt w programie Excel. Sprawdź następujące informacje:  
  
    -   <xref:Microsoft.Office.Tools.Excel.ListObject> Wypełnia przy użyciu danych.  
  
    -   Wartość w **ListPrice** kolumnie dla pierwszego wiersza <xref:Microsoft.Office.Tools.Excel.ListObject> jest 1431.5. W dalszej części tego przewodnika użyjesz aplikacji konsoli, aby zmodyfikować wartości w **ListPrice** kolumny.  
  
2.  Zapisz skoroszyt. Nie należy modyfikować nazwy pliku lub lokalizacji skoroszytu.  
  
3.  Zamknij program Excel.  
  
## <a name="create-a-console-application-project"></a>Utwórz projekt aplikacji konsoli  
 Utwórz projekt aplikacji konsoli, można użyć w celu modyfikacji danych w pamięci podręcznej zestawu danych w skoroszycie.  
  
### <a name="to-create-the-console-application-project"></a>Aby utworzyć projekt aplikacji konsoli  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **AdventureWorksDataSet** rozwiązania, wskaż **Dodaj**, a następnie kliknij przycisk **nowy projekt**.  
  
2.  W **typów projektów** okienku rozwiń **Visual C#** lub **Visual Basic**, a następnie kliknij przycisk **Windows**.  
  
3.  W **szablony** okienku wybierz **aplikacji konsoli**.  
  
4.  W **nazwa** wpisz **DataWriter**. Nie należy modyfikować lokalizację.  
  
5.  Kliknij przycisk **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje **DataWriter** projektu do **Eksploratora rozwiązań** i otwiera **Program.cs** lub **Module1.vb** pliku kodu.  
  
## <a name="change-data-in-the-cached-dataset-by-using-the-console-application"></a>Zmiany danych w pamięci podręcznej zestawu danych za pomocą aplikacji konsoli  
 Użyj <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy w aplikacji konsoli, aby odczytać dane na komputerze lokalnym `AdventureWorksLTDataSet` obiektów, zmodyfikować te dane, a następnie zapisz go do pamięci podręcznej zestawu danych.  
  
### <a name="to-change-data-in-the-cached-dataset"></a>Aby zmienić dane w pamięci podręcznej zestawu danych  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **DataWriter** projekt i kliknij przycisk **Dodaj odwołanie**.  
  
2.  Na **.NET** wybierz opcję **Microsoft.VisualStudio.Tools.Applications**.  
  
3.  Kliknij przycisk **OK**.  
  
4.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **DataWriter** projekt i kliknij przycisk **Dodaj odwołanie**.  
  
5.  Na **projekty** wybierz opcję **AdventureWorksDataSet**i kliknij przycisk **OK**.  
  
6.  Otwórz *Program.cs* lub *Module1.vb* plik w edytorze kodu.  
  
7.  Dodaj następujące **przy użyciu** (dla C#) lub **importów** (w języku Visual Basic) instrukcji na początku pliku kodu.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#1)]
     [!code-vb[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#1)]  
  
8.  Dodaj następujący kod do `Main` metody. Ten kod deklaruje następujące obiekty:  
  
    -   Wystąpienie `AdventureWorksLTDataSet` typu, który jest zdefiniowany w **AdventureWorksDataSet** projektu.  
  
    -   Ścieżka do skoroszytu AdventureWorksReport w folderze kompilacji **AdventureWorksReport** projektu.  
  
    -   A <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> obiektu na potrzeby pamięci podręcznej danych w skoroszycie.  
  
        > [!NOTE]  
        >  Poniższy kod przyjęto założenie, że używasz skoroszytu, który ma *xlsx* rozszerzenia pliku. Jeśli skoroszytu w projekcie ma rozszerzenie innego pliku, zmodyfikuj ścieżkę zgodnie z potrzebami.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#6](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#6)]
     [!code-vb[Trin_CachedDataWalkthroughs#6](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#6)]  
  
9. Dodaj następujący kod do `Main` metody po kodzie dodanym w poprzednim kroku. Kod będzie wykonywał następujące zadania:  
  
    -   Używa <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> właściwość <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy można uzyskać dostępu do pamięci podręcznej zestawu danych w skoroszycie.  
  
    -   Odczytuje dane z pamięci podręcznej zestawu danych do lokalnego zestawu danych.  
  
    -   Zmienia `ListPrice` wartość każdego produktu w tabeli produktu zestawu danych.  
  
    -   Zapisuje zmiany do pamięci podręcznej zestawu danych w skoroszycie.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#7](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#7)]
     [!code-vb[Trin_CachedDataWalkthroughs#7](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#7)]  
  
10. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **DataWriter** projektu, wskaż pozycję **debugowania**, a następnie kliknij przycisk **Start nowe wystąpienie**.  
  
     Aplikacja konsolowa wyświetla komunikaty go odczytuje zestaw danych w pamięci podręcznej do lokalnego zestawu danych, gdy modyfikuje cen produktu w zestawie danych lokalnych i zapisuje te nowe wartości do pamięci podręcznej zestawu danych. Naciśnij klawisz **Enter** aby zamknąć aplikację.  
  
## <a name="test-the-workbook"></a>Testowanie skoroszytu  
 Podczas otwierania skoroszytu, <xref:Microsoft.Office.Tools.Excel.ListObject> są obecnie wyświetlane zmiany wprowadzone w `ListPrice` kolumny danych w pamięci podręcznej zestawu danych.  
  
### <a name="to-test-the-workbook"></a>Aby przetestować skoroszytu  
  
1.  Zamknij skoroszyt AdventureWorksReport w projektancie programu Visual Studio, jeśli jest nadal otwarty.  
  
2.  Otwórz skoroszyt AdventureWorksReport, który znajduje się w folderze kompilacji **AdventureWorksReport** projektu. Domyślnie folder kompilacji znajduje się w jednym z następujących lokalizacji:  
  
    -   *%UserProfile%\My Documents\AdventureWorksReport\bin\Debug* (dla systemu Windows XP i starszych)  
  
    -   *%USERPROFILE%\Documents\AdventureWorksReport\bin\Debug* (dla systemu Windows Vista)  
  
3.  Sprawdź, czy wartość w **ListPrice** kolumnie dla pierwszego wiersza <xref:Microsoft.Office.Tools.Excel.ListObject> jest teraz 1574.65.  
  
4.  Zamknij skoroszyt.  
  
## <a name="see-also"></a>Zobacz także  
 [Wskazówki: Wstawianie danych do skoroszytu na serwerze](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)   
 [Łączenie z danymi w aplikacjach formularzy systemu Windows](/visualstudio/data-tools/connecting-to-data-in-windows-forms-applications)  
  
  