---
title: "Wskazówki: Wstawianie danych do skoroszytu na serwerze | Dokumentacja firmy Microsoft"
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
- datasets [Office development in Visual Studio], accessing on server
- server-side data access [Office development in Visual Studio]
- data [Office development in Visual Studio], accessing on server
- documents [Office development in Visual Studio], server-side data access
- workbooks [Office development in Visual Studio], inserting data
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 389252ed9457935c86dcaca0ce8a9a5733202d94
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-inserting-data-into-a-workbook-on-a-server"></a>Wskazówki: wstawianie danych do skoroszytu na serwerze
  W tym przewodniku pokazano, jak wstawianie danych do zestawu danych, który jest w pamięci podręcznej programu Microsoft Excel pakietu Office bez uruchamiania programu Excel za pomocą <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Definiowanie zestawu danych, który zawiera dane z bazy danych AdventureWorksLT.  
  
-   Tworzenie wystąpień zestawu danych w projekcie skoroszytu programu Excel i projekt aplikacji konsoli.  
  
-   Tworzenie <xref:Microsoft.Office.Tools.Excel.ListObject> który jest powiązany z zestawem danych w skoroszycie.  
  
-   Dodawanie zestawu danych w skoroszycie do pamięci podręcznej danych.  
  
-   Wstawianie danych do pamięci podręcznej zestawu danych, uruchamiając kod w aplikacji konsoli bez uruchamiania programu Excel.  
  
 Mimo że w tym przewodniku przyjęto założenie, że uruchamiasz kodu na komputerze deweloperskim, kodu zostało to pokazane w tym przewodniku można użyć na serwerze, który nie ma zainstalowanego programu Excel.  
  
> [!NOTE]  
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)]lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Dostęp do działającego wystąpienia programu Microsoft SQL Server lub programu Microsoft SQL Server Express zawierający AdventureWorksLT przykładowej bazy danych do niego dołączony. Możesz pobrać bazę danych AdventureWorksLT z [witryny sieci Web w witrynie CodePlex](http://go.microsoft.com/fwlink/?linkid=87843). Aby uzyskać więcej informacji na temat dołączania bazy danych zobacz następujące tematy:  
  
    -   Aby dołączyć bazę danych przy użyciu programu SQL Server Management Studio lub SQL Server Management Studio Express, zobacz [porady: dołączanie bazy danych (SQL Server Management Studio)](http://msdn.microsoft.com/en-us/b4efb0ae-cfe6-4d81-a4b4-6e4916885caa).  
  
    -   Aby dołączyć bazę danych przy użyciu wiersza polecenia, zobacz [porady: dołączanie pliku bazy danych do programu SQL Server Express](http://msdn.microsoft.com/en-us/0f8e42b5-7a8c-4c30-8c98-7d2bdc8dcc68).  
  
## <a name="creating-a-class-library-project-that-defines-a-dataset"></a>Tworzenie projektu biblioteki klas, który definiuje zestaw danych  
 Aby użyć tego samego zestawu danych w projekcie skoroszytu programu Excel i aplikacji konsoli, należy zdefiniować element dataset w osobny zestaw, do którego odwołuje się obu tych projektów. W ramach tego przewodnika Definiowanie zestawu danych w projektach biblioteki klas.  
  
#### <a name="to-create-the-class-library-project"></a>Aby utworzyć projektu biblioteki klas  
  
1.  Uruchom [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Na **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu**.  
  
3.  W okienku szablonów rozwiń **Visual C#** lub **Visual Basic**, a następnie kliknij przycisk **Windows**.  
  
4.  Na liście szablony projektów, wybierz **biblioteki klas**.  
  
5.  W **nazwa** wpisz **AdventureWorksDataSet**.  
  
6.  Kliknij przycisk **Przeglądaj**, przejdź do dokumentów %UserProfile%\My (dla systemu Windows XP i starszych) lub folderu %UserProfile%\Documents (dla systemu Windows Vista), a następnie kliknij przycisk **wybierz Folder**.  
  
7.  W **nowy projekt** okna dialogowego Sprawdź, czy **Utwórz katalog rozwiązania** nie zaznaczono pola wyboru.  
  
8.  Kliknij przycisk **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]dodaje **AdventureWorksDataSet** projektu do **Eksploratora rozwiązań** i otwiera **Class1.cs** lub **Class1.vb** pliku kodu.  
  
9. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Class1.cs** lub **Class1.vb**, a następnie kliknij przycisk **usunąć**. Nie trzeba tego pliku w ramach tego przewodnika.  
  
## <a name="defining-a-dataset-in-the-class-library-project"></a>Definiowanie zestawu danych w ramach projektu biblioteki klas  
 Zdefiniuj typizowanego zestaw danych, który zawiera dane z bazy danych AdventureWorksLT dla programu SQL Server 2005. W dalszej części tego przewodnika będzie odwoływać ten zestaw danych z projektu skoroszyt programu Excel i projekt aplikacji konsoli.  
  
 Zestaw danych jest *wpisane dataset* reprezentujący dane w tabeli Produkty bazy danych AdventureWorksLT. Aby uzyskać więcej informacji na temat typizowane zbiory danych, zobacz [narzędzia zestawu danych w programie Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).  
  
#### <a name="to-define-a-typed-dataset-in-the-class-library-project"></a>Aby zdefiniować typizowanego obiektu dataset w projektu biblioteki klas  
  
1.  W **Eksploratora rozwiązań**, kliknij przycisk **AdventureWorksDataSet** projektu.  
  
2.  Jeśli **źródeł danych** okna nie jest widoczne, wyświetl ją, z menu, wybierając **widoku**, **inne okna**, **źródeł danych**.  
  
3.  Wybierz **Dodaj nowe źródło danych** uruchomić **Kreator konfiguracji źródła danych**.  
  
4.  Kliknij przycisk **bazy danych**, a następnie kliknij przycisk **dalej**.  
  
5.  Jeśli masz istniejące połączenie z bazą danych AdventureWorksLT, wybierz to połączenie i kliknij przycisk **dalej**.  
  
     W przeciwnym razie kliknij przycisk **nowe połączenie**i użyj **Dodawanie połączenia** okno dialogowe, aby utworzyć nowe połączenie. Aby uzyskać więcej informacji, zobacz [porady: łączenie z danymi w bazie danych](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md).  
  
6.  W **zapisać parametry połączenia do pliku konfiguracji aplikacji** kliknij przycisk **dalej**.  
  
7.  W **wybierz obiekty bazy danych użytkownika** rozwiń pozycję **tabel** i wybierz **produktu (SalesLT)**.  
  
8.  Kliknij przycisk **Zakończ**.  
  
     Plik AdventureWorksLTDataSet.xsd jest dodawany do **AdventureWorksDataSet** projektu. Ten plik definiuje następujące elementy:  
  
    -   Typizowanego zestaw danych o nazwie `AdventureWorksLTDataSet`. Ten zestaw danych reprezentuje zawartość tabeli produktu w bazie danych AdventureWorksLT.  
  
    -   TableAdapter o nazwie `ProductTableAdapter`. Ten obiekt TableAdapter może służyć do odczytywania i zapisywania danych `AdventureWorksLTDataSet`. Aby uzyskać więcej informacji, zobacz [TableAdapter — Przegląd](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).  
  
     Użyje obu tych obiektów w dalszej części tego przewodnika.  
  
9. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **AdventureWorksDataSet** i kliknij przycisk **kompilacji**.  
  
     Upewnij się, że projekt tworzy się bez błędów.  
  
## <a name="creating-an-excel-workbook-project"></a>Tworzenie projektu skoroszyt programu Excel  
 Tworzenie projektu skoroszyt programu Excel dla interfejsu do danych. W dalszej części tego przewodnika, utworzysz <xref:Microsoft.Office.Tools.Excel.ListObject> wyświetlający danych i wystąpienia zestawu danych zostaną dodane do pamięci podręcznej danych w skoroszycie.  
  
#### <a name="to-create-the-excel-workbook-project"></a>Aby utworzyć projekt skoroszytu programu Excel  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **AdventureWorksDataSet** rozwiązania, wskaż **Dodaj**, a następnie kliknij przycisk **nowy projekt**.  
  
2.  W okienku szablonów rozwiń **Visual C#** lub **Visual Basic**, a następnie rozwiń węzeł **Office i SharePoint**.  
  
3.  Pod rozwiniętym **Office i SharePoint** węzła, wybierz opcję **dodatków pakietu Office** węzła.  
  
4.  Na liście szablony projektów, wybierz **skoroszyt programu Excel 2010** lub **skoroszyt programu Excel 2013** projektu.  
  
5.  W **nazwa** wpisz **AdventureWorksReport**. Nie należy modyfikować lokalizację.  
  
6.  Kliknij przycisk **OK**.  
  
     **Visual Studio Tools dla pakietu Office, Kreator projektu** otwiera.  
  
7.  Upewnij się, że **Utwórz nowy dokument** jest zaznaczone, a następnie kliknij przycisk **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Otwiera **AdventureWorksReport** skoroszytu w Projektancie i dodaje **AdventureWorksReport** projektu do **Eksploratora rozwiązań**.  
  
## <a name="adding-the-dataset-to-data-sources-in-the-excel-workbook-project"></a>Dodawanie zestawu danych do źródła danych w projekcie skoroszytu programu Excel  
 Aby wyświetlić zestaw danych w skoroszycie programu Excel, najpierw należy dodać zestaw danych ze źródłami danych w projekcie skoroszytu programu Excel.  
  
#### <a name="to-add-the-dataset-to-the-data-sources-in-the-excel-workbook-project"></a>Aby dodać zestaw danych do źródła danych w projekcie skoroszytu programu Excel  
  
1.  W **Eksploratora rozwiązań**, kliknij dwukrotnie **Sheet1.cs** lub **Sheet1.vb** w obszarze **AdventureWorksReport** projektu.  
  
     Skoroszyt zostanie otwarty w projektancie.  
  
2.  Na **danych** menu, kliknij przycisk **Dodaj nowe źródło danych**.  
  
     **Kreator konfiguracji źródła danych** otwiera.  
  
3.  Kliknij przycisk **obiektu**, a następnie kliknij przycisk **dalej**.  
  
4.  W **wybierz obiekt ma zostać powiązania** strony, kliknij przycisk **Dodaj odwołanie**.  
  
5.  Na **projekty** , kliknij pozycję **AdventureWorksDataSet** , a następnie kliknij przycisk **OK**.  
  
6.  W obszarze **AdventureWorksDataSet** przestrzeń nazw **AdventureWorksDataSet** zestawu, kliknij przycisk **AdventureWorksLTDataSet** , a następnie kliknij przycisk **Zakończ** .  
  
     **Źródeł danych** zostanie otwarte okno i **AdventureWorksLTDataSet** zostanie dodany do listy źródeł danych.  
  
## <a name="creating-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Tworzenie ListObject, który jest powiązany z wystąpieniem zestawu danych  
 Aby wyświetlić zestaw danych w skoroszycie, Utwórz <xref:Microsoft.Office.Tools.Excel.ListObject> który jest powiązany z wystąpieniem elementu dataset. Aby uzyskać więcej informacji na temat powiązanie kontrolek z danymi, zobacz [powiązania danych do formantów w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
#### <a name="to-create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Aby utworzyć ListObject, który jest powiązany z wystąpieniem zestawu danych  
  
1.  W **źródeł danych** okna, rozwiń węzeł **AdventureWorksLTDataSet** węźle **AdventureWorksDataSet**.  
  
2.  Wybierz **produktu** węzła, kliknij strzałkę listy rozwijanej, która jest wyświetlana, a następnie wybierz **ListObject** na liście rozwijanej.  
  
     Jeśli nie ma strzałkę listy rozwijanej, upewnij się, że skoroszyt jest otwarty w projektancie.  
  
3.  Przeciągnij **produktu** tabeli do komórki A1.  
  
     A <xref:Microsoft.Office.Tools.Excel.ListObject> formantu o nazwie `productListObject` jest tworzony w arkuszu, począwszy od komórki A1. Jednocześnie, obiekt zestawu danych o nazwie `adventureWorksLTDataSet` i <xref:System.Windows.Forms.BindingSource> o nazwie `productBindingSource` zostaną dodane do projektu. <xref:Microsoft.Office.Tools.Excel.ListObject> Jest powiązany z <xref:System.Windows.Forms.BindingSource>, która z kolei jest powiązana z obiektem zestawu danych.  
  
## <a name="adding-the-dataset-to-the-data-cache"></a>Dodawanie zestawu danych do pamięci podręcznej danych  
 Aby włączyć kod spoza projektu skoroszyt programu Excel do zestawu danych w skoroszycie, należy dodać zestaw danych do pamięci podręcznej danych. Aby uzyskać więcej informacji o pamięci podręcznej danych, zobacz [buforowane dane w dostosowaniach na poziomie dokumentu](../vsto/cached-data-in-document-level-customizations.md) i [buforowanie danych](../vsto/caching-data.md).  
  
#### <a name="to-add-the-dataset-to-the-data-cache"></a>Aby dodać zestaw danych do pamięci podręcznej danych  
  
1.  W projektancie, kliknij **adventureWorksLTDataSet**.  
  
2.  W **właściwości** ustaw **Modyfikatory** właściwości **publicznego**.  
  
3.  Ustaw **CacheInDocument** właściwości **True**.  
  
## <a name="checkpoint"></a>Punkt kontrolny  
 Tworzenie i uruchamianie projektu skoroszytu programu Excel, aby upewnić się, że kompiluje i uruchamia bez błędów.  
  
#### <a name="to-build-and-run-the-project"></a>Aby skompilować i uruchomić projekt  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **AdventureWorksReport** projektu, wybierz **debugowania**, a następnie kliknij przycisk **Start nowe wystąpienie**.  
  
     Projekt jest budowany i otwiera skoroszyt w programie Excel. <xref:Microsoft.Office.Tools.Excel.ListObject> w **Sheet1 —** jest pusta, ponieważ `adventureWorksLTDataSet` obiektu w pamięci podręcznej danych nie ma jeszcze żadnych danych. W następnej sekcji użyjesz aplikacji konsoli, aby wypełnić `adventureWorksLTDataSet` obiektu z danych.  
  
2.  Zamknij program Excel. Nie zapisuj zmian.  
  
## <a name="creating-a-console-application-project"></a>Tworzenie nowego projektu aplikacji konsoli  
 Utwórz projekt aplikacji konsoli służące do wstawiania danych w pamięci podręcznej zestawu danych w skoroszycie.  
  
#### <a name="to-create-the-console-application-project"></a>Aby utworzyć projekt aplikacji konsoli  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **AdventureWorksDataSet** rozwiązania, wskaż **Dodaj**, a następnie kliknij przycisk **nowy projekt**.  
  
2.  W **typów projektów** okienku rozwiń **Visual C#** lub **Visual Basic**, a następnie kliknij przycisk **Windows**.  
  
3.  W **szablony** okienku wybierz **aplikacji konsoli**.  
  
4.  W **nazwa** wpisz **DataWriter**. Nie należy modyfikować lokalizację.  
  
5.  Kliknij przycisk **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]dodaje **DataWriter** projektu do **Eksploratora rozwiązań** i otwiera **Program.cs** lub **Module1.vb** pliku kodu.  
  
## <a name="adding-data-to-the-cached-dataset-by-using-the-console-application"></a>Dodawanie danych do pamięci podręcznej zestawu danych za pomocą aplikacji konsoli  
 Użyj <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy w aplikacji konsoli w celu wypełnienia pamięci podręcznej zestawu danych w skoroszycie z danymi.  
  
#### <a name="to-add-data-to-the-cached-dataset"></a>Aby dodać dane do pamięci podręcznej zestawu danych  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **DataWriter** projekt i kliknij przycisk **Dodaj odwołanie**.  
  
2.  Na **.NET** wybierz opcję **Microsoft.VisualStudio.Tools.Applications.ServerDocument**.  
  
3.  Kliknij przycisk **OK**.  
  
4.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **DataWriter** projekt i kliknij przycisk **Dodaj odwołanie**.  
  
5.  Na **projekty** wybierz opcję **AdventureWorksDataSet**i kliknij przycisk **OK**.  
  
6.  Otwórz plik Program.cs lub Module1.vb w edytorze kodu.  
  
7.  Dodaj następujące **przy użyciu** (dla C#) lub **importów** (w języku Visual Basic) instrukcji na początku pliku kodu.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#1)]
     [!code-vb[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#1)]  
  
8.  Dodaj następujący kod do `Main` metody. Ten kod deklaruje następujące obiekty:  
  
    -   Wystąpienia `AdventureWorksLTDataSet` i `ProductTableAdapter` typy, które są zdefiniowane w **AdventureWorksDataSet** projektu.  
  
    -   Ścieżka do skoroszytu AdventureWorksReport w folderze kompilacji **AdventureWorksReport** projektu.  
  
    -   A <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> obiektu na potrzeby pamięci podręcznej danych w skoroszycie.  
  
        > [!NOTE]  
        >  Poniższy kod przyjęto założenie, że używasz skoroszytu, który ma rozszerzenie pliku xlsx. Jeśli skoroszytu w projekcie ma rozszerzenie innego pliku, zmodyfikuj ścieżkę zgodnie z potrzebami.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#3](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#3)]
     [!code-vb[Trin_CachedDataWalkthroughs#3](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#3)]  
  
9. Dodaj następujący kod do `Main` metody po kodzie dodanym w poprzednim kroku. Kod będzie wykonywał następujące zadania:  
  
    -   Umieszcza obiektu typizowanego obiektu dataset za pomocą karty tabeli.  
  
    -   Używa <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> właściwość <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy można uzyskać dostępu do pamięci podręcznej zestawu danych w skoroszycie.  
  
    -   Używa <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> metody w celu wypełnienia pamięci podręcznej zestawu danych danymi z lokalnym typizowanego obiektu dataset.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#4](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#4)]
     [!code-vb[Trin_CachedDataWalkthroughs#4](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#4)]  
  
10. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **DataWriter** projektu, wskaż pozycję **debugowania**, a następnie kliknij przycisk **Start nowe wystąpienie**.  
  
     Projekt jest budowany oraz aplikacji konsoli wyświetla kilka komunikatów o stanie podczas wypełniania lokalnego zestawu danych i gdy aplikacja zapisuje dane w pamięci podręcznej zestawu danych w skoroszycie. Naciśnij klawisz ENTER, aby zamknąć aplikację.  
  
## <a name="testing-the-workbook"></a>Testowanie skoroszytu  
 Podczas otwierania skoroszytu, <xref:Microsoft.Office.Tools.Excel.ListObject> są obecnie wyświetlane dane, która została dodana do pamięci podręcznej zestawu danych za pomocą aplikacji konsoli.  
  
#### <a name="to-test-the-workbook"></a>Aby przetestować skoroszytu  
  
1.  Zamknij skoroszyt AdventureWorksReport w projektancie programu Visual Studio, jeśli jest nadal otwarty.  
  
2.  W Eksploratorze plików, otwórz skoroszyt AdventureWorksReport, który znajduje się w folderze kompilacji **AdventureWorksReport** projektu. Domyślnie folder kompilacji znajduje się w jednym z następujących lokalizacji:  
  
    -   %UserProfile%\My Documents\AdventureWorksReport\bin\Debug (dla systemu Windows XP i starszych)  
  
    -   %USERPROFILE%\Documents\AdventureWorksReport\bin\Debug (dla systemu Windows Vista)  
  
3.  Sprawdź, czy <xref:Microsoft.Office.Tools.Excel.ListObject> jest wypełniana danych, po otwarciu skoroszytu.  
  
## <a name="next-steps"></a>Następne kroki  
 Dodatkowe informacje na temat pracy z pamięci podręcznej danych z tych tematów:  
  
-   Modyfikowanie danych w pamięci podręcznej zestawu danych, bez konieczności uruchamiania programu Excel. Aby uzyskać więcej informacji, zobacz [wskazówki: zmiana danych w pamięci podręcznej ze skoroszytu na serwerze](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Zmiana danych z pamięci podręcznej skoroszytu na serwerze](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)   
 [Łączenie z danymi w aplikacjach formularzy systemu Windows](/visualstudio/data-tools/connecting-to-data-in-windows-forms-applications)  
  
  