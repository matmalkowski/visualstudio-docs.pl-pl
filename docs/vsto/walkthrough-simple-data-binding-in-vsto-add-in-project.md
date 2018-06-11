---
title: 'Wskazówki: Proste powiązanie danych w projekcie dodatku narzędzi VSTO'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], binding data
- data binding [Office development in Visual Studio], Word
- data [Office development in Visual Studio], simple binding data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e4ef7d1a5fba975d987f3a485a282fdb3d6ea9fc
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35258086"
---
# <a name="walkthrough-simple-data-binding-in-vsto-add-in-project"></a>Wskazówki: Proste powiązanie danych w projekcie dodatku narzędzi VSTO
  Dane można powiązać z formanty hosta i formantów formularzy systemu Windows w projektów dodatku VSTO. W tym przewodniku pokazano, jak dodawanie formantów do dokumentu programu Microsoft Office Word i powiązanie kontrolek z danymi w czasie wykonywania.  
  
 [!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Dodawanie <xref:Microsoft.Office.Tools.Word.ContentControl> do dokumentu w czasie wykonywania.  
  
-   Tworzenie <xref:System.Windows.Forms.BindingSource> łączące formantu do wystąpienia zestawu danych.  
  
-   Włączanie użytkownika do przewijania rekordów i wyświetlić je w formancie.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] lub [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
-   Dostęp do działającego wystąpienia programu SQL Server 2005 lub SQL Server 2005 Express, która ma `AdventureWorksLT` przykładową bazę danych do niego dołączony. Możesz pobrać `AdventureWorksLT` bazy danych z [witryny sieci Web w witrynie CodePlex](http://go.microsoft.com/fwlink/?LinkId=115611). Aby uzyskać więcej informacji na temat dołączania bazy danych zobacz następujące tematy:  
  
    -   Aby dołączyć bazę danych przy użyciu programu SQL Server Management Studio lub SQL Server Management Studio Express, zobacz [porady: dołączanie bazy danych (SQL Server Management Studio)](http://msdn.microsoft.com/en-us/b4efb0ae-cfe6-4d81-a4b4-6e4916885caa).  
  
    -   Aby dołączyć bazę danych przy użyciu wiersza polecenia, zobacz [porady: dołączanie pliku bazy danych do programu SQL Server Express](http://msdn.microsoft.com/en-us/0f8e42b5-7a8c-4c30-8c98-7d2bdc8dcc68).  
  
## <a name="create-a-new-project"></a>Tworzenie nowego projektu  
 Pierwszym krokiem jest utworzenie projektu dodatku VSTO programu Word.  
  
### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt  
  
1.  Tworzenie projektów dodatku VSTO programu Word o nazwie **zapełnianie dokumentów z bazy danych**, za pomocą Visual Basic lub C#.  
  
     Aby uzyskać więcej informacji, zobacz [porady: tworzenie projektach pakietu Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio otworzy *ThisAddIn.vb* lub *ThisAddIn.cs* plików i dodaje **zapełnianie dokumentów z bazy danych** projektu do **Eksplorator rozwiązań** .  
  
2.  Jeśli elementy docelowe projektu [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], Dodaj odwołanie do *Microsoft.Office.Tools.Word.v4.0.Utilities.dll* zestawu. To odwołanie jest wymagane do programowo Dodaj formanty formularzy systemu Windows do dokumentów w dalszej części tego przewodnika.  
  
## <a name="create-a-data-source"></a>Utwórz źródło danych  
 Użyj **źródeł danych** okno, aby dodać typizowanego zestaw danych do projektu.  
  
### <a name="to-add-a-typed-dataset-to-the-project"></a>Aby dodać typizowanego zestaw danych do projektu  
  
1.  Jeśli **źródeł danych** okna nie jest widoczne, wyświetl ją, z menu, wybierając **widoku** > **inne okna**  >   **Źródła danych**.  
  
2.  Wybierz **Dodaj nowe źródło danych** uruchomić **Kreator konfiguracji źródła danych**.  
  
3.  Kliknij przycisk **bazy danych**, a następnie kliknij przycisk **dalej**.  
  
4.  Jeśli masz istniejące połączenie z `AdventureWorksLT` bazy danych, wybierz to połączenie i kliknij przycisk **dalej**.  
  
     W przeciwnym razie kliknij przycisk **nowe połączenie**i użyj **Dodawanie połączenia** okno dialogowe, aby utworzyć nowe połączenie. Aby uzyskać więcej informacji, zobacz [dodać nowe połączenia](../data-tools/add-new-connections.md).  
  
5.  W **zapisać parametry połączenia do pliku konfiguracji aplikacji** kliknij przycisk **dalej**.  
  
6.  W **wybierz obiekty bazy danych użytkownika** rozwiń pozycję **tabel** i wybierz **klienta (SalesLT)**.  
  
7.  Kliknij przycisk **Zakończ**.  
  
     *AdventureWorksLTDataSet.xsd* plik zostanie dodany do **Eksploratora rozwiązań**. Ten plik definiuje następujące elementy:  
  
    -   Typizowanego zestaw danych o nazwie `AdventureWorksLTDataSet`. Ten zestaw danych reprezentuje zawartość **klienta (SalesLT)** tabeli w bazie danych AdventureWorksLT.  
  
    -   TableAdapter o nazwie `CustomerTableAdapter`. Ten obiekt TableAdapter może służyć do odczytywania i zapisywania danych `AdventureWorksLTDataSet`. Aby uzyskać więcej informacji, zobacz [TableAdapter — Przegląd](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).  
  
     Użyje obu tych obiektów w dalszej części tego przewodnika.  
  
## <a name="create-controls-and-binding-controls-to-data"></a>Tworzenie formantów i powiązanie kontrolek z danymi  
 Interfejs do wyświetlania rekordów bazy danych w ramach tego przewodnika jest bardzo proste i utworzeniu prawa w dokumencie. Jeden <xref:Microsoft.Office.Tools.Word.ContentControl> przedstawia rekord pojedynczej bazy danych w czasie i dwa <xref:Microsoft.Office.Tools.Word.Controls.Button> formanty umożliwiają i z powrotem przewijania rekordów. Formant zawartości używa <xref:System.Windows.Forms.BindingSource> do połączenia z bazą danych.  
  
 Aby uzyskać więcej informacji na temat powiązanie kontrolek z danymi, zobacz [wiązanie danych do formantów w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
### <a name="to-create-the-interface-in-the-document"></a>Aby utworzyć interfejs w dokumencie  
  
1.  W `ThisAddIn` klasy, Zadeklaruj następujące sterowniki do wyświetlania i przewijać `Customer` tabeli `AdventureWorksLTDataSet` bazy danych.  
  
     [!code-vb[Trin_WordAddInDatabase#1](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDatabase#1](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#1)]  
  
2.  W `ThisAddIn_Startup` metody, Dodaj następujący kod, aby zainicjować zestawu danych, wypełnić dataset z informacjami z `AdventureWorksLTDataSet` bazy danych.  
  
     [!code-vb[Trin_WordAddInDatabase#2](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDatabase#2](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#2)]  
  
3.  Dodaj następujący kod do `ThisAddIn_Startup` metody. Generuje element hosta, rozszerzający dokumentu. Aby uzyskać więcej informacji, zobacz [dokumentów rozszerzania programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
     [!code-vb[Trin_WordAddInDatabase#3](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDatabase#3](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#3)]  
  
4.  Zdefiniuj kilka zakresów na początku dokumentu. Te zakresy ustalając, gdzie do wstawiania tekstu i umieść formanty.  
  
     [!code-vb[Trin_WordAddInDatabase#4](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDatabase#4](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#4)]  
  
5.  Dodawanie formantów interfejsu do wcześniej zdefiniowanych zakresów.  
  
     [!code-vb[Trin_WordAddInDatabase#5](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#5)]
     [!code-csharp[Trin_WordAddInDatabase#5](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#5)]  
  
6.  BIND formant zawartości `AdventureWorksLTDataSet` przy użyciu <xref:System.Windows.Forms.BindingSource>. C# deweloperom Dodaj dwa programy obsługi zdarzeń dla <xref:Microsoft.Office.Tools.Word.Controls.Button> kontrolki.  
  
     [!code-vb[Trin_WordAddInDatabase#6](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#6)]
     [!code-csharp[Trin_WordAddInDatabase#6](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#6)]  
  
7.  Dodaj następujący kod do nawigowania rekordów bazy danych.  
  
     [!code-vb[Trin_WordAddInDatabase#7](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#7)]
     [!code-csharp[Trin_WordAddInDatabase#7](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#7)]  
  
## <a name="test-the-add-in"></a>Testowanie dodatku  
 Po otwarciu programu Word formantu zawartości są wyświetlane dane z `AdventureWorksLTDataSet` zestawu danych. Przewijanie rekordów bazy danych, klikając **dalej** i **Wstecz** przycisków.  
  
### <a name="to-test-the-vsto-add-in"></a>Aby przetestować dodatku narzędzi VSTO  
  
1.  Naciśnij klawisz **F5**.  
  
     Formant zawartości o nazwie `customerContentControl` jest tworzone i wypełniane przy użyciu danych. Jednocześnie, obiekt zestawu danych o nazwie `adventureWorksLTDataSet` i <xref:System.Windows.Forms.BindingSource> o nazwie `customerBindingSource` zostaną dodane do projektu. <xref:Microsoft.Office.Tools.Word.ContentControl> Jest powiązany z <xref:System.Windows.Forms.BindingSource>, która z kolei jest powiązana z obiektem zestawu danych.  
  
2.  Kliknij przycisk **dalej** i **Wstecz** przycisków do przewijania rekordów bazy danych.  
  
## <a name="see-also"></a>Zobacz także  
 [Dane w rozwiązaniach pakietu Office](../vsto/data-in-office-solutions.md)   
 [Wiązanie danych do formantów w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Porady: zapełnianie arkuszy danymi z bazy danych](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Porady: zapełnianie dokumentów danymi z bazy danych](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Porady: zapełnianie dokumentów danymi z usług](../vsto/how-to-populate-documents-with-data-from-services.md)   
 [Porady: zapełnianie dokumentów danymi z obiektów](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Porady: przewijanie rekordów bazy danych w arkuszu](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)   
 [Porady: aktualizowanie źródła danych danymi z formanty hosta](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Wskazówki: Proste powiązanie danych w projektach na poziomie dokumentu](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)   
 [Wskazówki: Złożone powiązanie danych w projektach na poziomie dokumentu](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)   
 [Użyj plików lokalnej bazy danych w rozwiązań Office ― omówienie](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [Dodawanie nowych źródeł danych](/visualstudio/data-tools/add-new-data-sources)   
 [Powiązywanie formantów formularzy systemu Windows z danymi w Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Porady: zapełnianie dokumentów danymi z obiektów](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Porady: aktualizowanie źródła danych danymi z formanty hosta](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Użyj plików lokalnej bazy danych w rozwiązań Office ― omówienie](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [Łączenie z danymi w aplikacjach formularzy systemu Windows](/visualstudio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [Informacje o składniku BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)  
  
  