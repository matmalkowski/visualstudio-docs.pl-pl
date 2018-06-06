---
title: 'Wskazówki: Wiązanie danych do kontrolek okienku akcji programu Excel'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], data binding
- actions panes [Office development in Visual Studio], data binding
- data binding [Office development in Visual Studio], smart documents
- data binding [Office development in Visual Studio], actions panes
- actions panes [Office development in Visual Studio], binding controls
- smart documents [Office development in Visual Studio], data binding
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9d450a9c52ae8558167bf4cb581ce2e36f44f4e9
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767913"
---
# <a name="walkthrough-bind-data-to-controls-on-an-excel-actions-pane"></a>Wskazówki: Wiązanie danych do kontrolek okienku akcji programu Excel
  W tym przewodniku przedstawiono powiązywanie danych do kontrolek okienku akcji programu Microsoft Office Excel. Formanty pokazują wzorzec/szczegół relacji między tabelami w bazie danych programu SQL Server.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Dodawanie formantów do arkusza.  
  
-   Tworzenie formantu w okienku Akcje.  
  
-   Dodawanie formantów formularzy systemu Windows powiązane z danymi z formantem w okienku Akcje.  
  
-   Po otwarciu aplikacji są wyświetlane w okienku Akcje.  
  
> [!NOTE]  
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Dostęp do serwera z przykładowej bazy danych Northwind programu SQL Server.  
  
-   Uprawnienia do odczytu i zapisu w bazie danych programu SQL Server.  
  
## <a name="create-the-project"></a>Utwórz projekt  
 Pierwszym krokiem jest utworzenie projektu skoroszyt programu Excel.  
  
### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt  
  
1.  Tworzenie projektu skoroszyt programu Excel o nazwie **Moje okienku akcji programu Excel**. W kreatorze Wybierz **Utwórz nowy dokument**. Aby uzyskać więcej informacji, zobacz [porady: tworzenie projektach pakietu Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio zostanie otwarty nowy skoroszyt programu Excel w Projektancie i dodaje **Moje okienku akcji programu Excel** projektu do **Eksploratora rozwiązań**.  
  
## <a name="add-a-new-data-source-to-the-project"></a>Dodaj nowe źródło danych do projektu  
  
### <a name="to-add-a-new-data-source-to-the-project"></a>Aby dodać nowego źródła danych do projektu  
  
1.  Jeśli **źródeł danych** okno nie jest widoczny, wyświetl ją, z menu, wybierając **widoku** > **inne okna**  >   **Źródła danych**.  
  
2.  Wybierz **Dodaj nowe źródło danych** uruchomić **Kreator konfiguracji źródła danych**.  
  
3.  Wybierz **bazy danych** , a następnie kliknij przycisk **dalej**.  
  
4.  Wybierz połączenie danych z bazie danych programu SQL Server Northwind lub Dodaj nowe połączenie przy użyciu **nowe połączenie** przycisku.  
  
5.  Kliknij przycisk **Dalej**.  
  
6.  Wyczyść opcję, aby zapisać połączenie, jeśli jest zaznaczone, a następnie kliknij przycisk **dalej**.  
  
7.  Rozwiń węzeł **tabel** w węźle **obiekty bazy danych** okna.  
  
8.  Zaznacz pole wyboru obok pozycji **dostawców** tabeli.  
  
9. Rozwiń węzeł **produktów** tabeli i wybierz **ProductName**, **IDDostawcy**, **QuantityPerUnit**, i **UnitPrice**.  
  
10. Kliknij przycisk **Zakończ**.  
  
 Kreator dodaje **dostawców** tabeli i **produktów** do tabeli **źródeł danych** okna. Dodano również typizowanego zestaw danych do projektu, które są widoczne w **Eksploratora rozwiązań**.  
  
## <a name="add-controls-to-the-worksheet"></a>Dodawanie formantów do arkusza  
 Następnie dodaj <xref:Microsoft.Office.Tools.Excel.NamedRange> kontroli i <xref:Microsoft.Office.Tools.Excel.ListObject> formantu do pierwszego arkusza.  
  
### <a name="to-add-a-namedrange-control-and-a-listobject-control"></a>Aby dodać formantu NamedRange i ListObject — formant  
  
1.  Sprawdź, czy **Moje Pane.xlsx akcji programu Excel** skoroszyt jest otwarty w projektancie programu Visual Studio z `Sheet1` wyświetlane.  
  
2.  W **źródeł danych** okna, rozwiń węzeł **dostawców** tabeli.  
  
3.  Kliknij strzałkę listy rozwijanej w **nazwa firmy** węzeł, a następnie kliknij przycisk **NamedRange**.  
  
4.  Przeciągnij **nazwa firmy** z **źródeł danych** okna do komórki **A2** w `Sheet1`.  
  
     A <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu o nazwie `CompanyNameNamedRange` został utworzony, a tekst \<NazwaFirmy > pojawia się w komórce **A2**. W tym samym czasie <xref:System.Windows.Forms.BindingSource> o nazwie `suppliersBindingSource`, karty tabeli, a <xref:System.Data.DataSet> zostaną dodane do projektu. Kontrolka jest powiązana z <xref:System.Windows.Forms.BindingSource>, która z kolei jest powiązana <xref:System.Data.DataSet> wystąpienia.  
  
5.  W **źródeł danych** okna, przewiń w dół poza kolumn, które są objęte **dostawców** tabeli. W dolnej części listy jest **produktów** tabeli; tutaj jest ponieważ jest elementem podrzędnym **dostawców** tabeli. Wybierz tę opcję, **produktów** tabeli nie jedną, która jest na tym samym poziomie jako **dostawców** tabeli, a następnie kliknij strzałkę listy rozwijanej, która jest wyświetlana.  
  
6.  Kliknij przycisk **ListObject** w listy rozwijanej, a następnie przeciągnij **produktów** tabeli do komórki **A6** w `Sheet1`.  
  
     A <xref:Microsoft.Office.Tools.Excel.ListObject> formantu o nazwie `ProductNameListObject` jest tworzony w komórce **A6**. W tym samym czasie <xref:System.Windows.Forms.BindingSource> o nazwie `productsBindingSource` i karty tabeli zostaną dodane do projektu. Kontrolka jest powiązana z <xref:System.Windows.Forms.BindingSource>, która z kolei jest powiązana <xref:System.Data.DataSet> wystąpienia.  
  
7.  Język C# tylko, wybierz **suppliersBindingSource** na składnik na pasku zadań, a następnie zmień **Modyfikatory** właściwości **wewnętrzne** w **właściwości** okna.  
  
## <a name="add-controls-to-the-actions-pane"></a>Dodawanie formantów do okienka Akcje  
 Następnie należy kontrolkę w okienku akcji, która ma pola kombi.  
  
### <a name="to-add-an-actions-pane-control"></a>Aby dodać kontrolkę okienka Akcje  
  
1.  Wybierz **Moje okienku akcji programu Excel** projektu w **Eksploratora rozwiązań**.  
  
2.  Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.  
  
3.  W **Dodaj nowy element** okno dialogowe, wybierz opcję **formant okienka Akcje**, nadaj jej nazwę **ActionsControl**i kliknij przycisk **Dodaj**.  
  
### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Aby dodać formanty formularzy systemu Windows z danymi z formantem w okienku Akcje  
  
1.  Z **formanty standardowe** karty **przybornika**, przeciągnij <xref:System.Windows.Forms.ComboBox> formant do formantu w okienku Akcje.  
  
2.  Zmień **rozmiar** właściwości **171, 21**.  
  
3.  Zmień rozmiar formantu użytkownika w celu dopasowania pola kombi.  
  
## <a name="bind-the-control-on-the-actions-pane-to-data"></a>Powiązanie z danymi formantu w okienku Akcje  
 W tej sekcji będziesz Ustaw źródło danych <xref:System.Windows.Forms.ComboBox> do tego samego źródła danych jako <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu w arkuszu.  
  
### <a name="to-set-data-binding-properties-of-the-control"></a>Aby ustawić właściwości wiązania danych formantu  
  
1.  Kliknij prawym przyciskiem myszy formant okienka Akcje, a następnie kliknij przycisk **kod widoku**.  
  
2.  Dodaj następujący kod do <xref:System.Windows.Forms.UserControl.Load> zdarzeń formantu w okienku Akcje.  
  
     [!code-vb[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#1)]  
  
3.  W języku C#, należy utworzyć programu obsługi zdarzeń dla `ActionsControl`. Możesz umieścić ten kod w `ActionsControl` konstruktora. Aby uzyskać więcej informacji o tworzeniu procedury obsługi zdarzeń, zobacz [porady: tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#2)]  
  
## <a name="show-the-actions-pane"></a>Umożliwia wyświetlenie okienka Akcje  
 W okienku Akcje nie są widoczne do momentu dodania formantu w czasie wykonywania.  
  
#### <a name="to-show-the-actions-pane"></a>Aby wyświetlić w okienku Akcje  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy *ThisWorkbook.vb* lub *ThisWorkbook.cs*, a następnie kliknij przycisk **kod widoku**.  
  
2.  Tworzenie nowego wystąpienia kontrolki użytkownika w `ThisWorkbook` klasy.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#3)]  
  
3.  W <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> obsługi zdarzeń `ThisWorkbook`, Dodaj formant w okienku Akcje.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#4)]  
  
## <a name="test-the-application"></a>Testowanie aplikacji  
 Teraz możesz przetestować dokumencie, aby sprawdzić, czy po otwarciu dokumentu zostanie otwarty w okienku Akcje i czy formanty mają relacji wzorzec/szczegół.  
  
### <a name="to-test-your-document"></a>Aby przetestować dokumentu  
  
1.  Naciśnij klawisz **F5** do uruchomienia projektu.  
  
2.  Upewnij się, że widoczne jest okienko akcji.  
  
3.  Wybierz firmę, w polu listy. Sprawdź, czy nazwa firmy jest wyświetlana w <xref:Microsoft.Office.Tools.Excel.NamedRange> kontroli i że są wyświetlane szczegóły produktu <xref:Microsoft.Office.Tools.Excel.ListObject> formantu.  
  
4.  Wybierz różnych firm, aby zweryfikować nazwę firmy, a następnie odpowiednio zmienić informacje szczegółowe.  
  
## <a name="next-steps"></a>Następne kroki  
 Poniżej przedstawiono niektóre zadania, które mogą występować:  
  
-   Wiązanie danych do kontrolek w programie Word. Aby uzyskać więcej informacji, zobacz [wskazówki: wiązanie danych do kontrolek okienku akcji programu Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).  
  
-   Wdrażanie projektu. Aby uzyskać więcej informacji, zobacz [wdrażania rozwiązania do pakietu Office przy użyciu technologii ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Okienko akcji ― omówienie](../vsto/actions-pane-overview.md)   
 [Porady: Zarządzanie układem formantu w okienkach akcji](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Wiązanie danych do formantów w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  