---
title: 'Wskazówki: Wiązanie danych do kontrolek okienku akcji programu Word | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: d84c42e2b51d55cbbb73a7f26d6d6853ff7a3392
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-binding-data-to-controls-on-a-word-actions-pane"></a>Wskazówki: powiązywanie danych z kontrolkami w okienku akcji programu Word
  W tym przewodniku przedstawiono powiązywanie danych do kontrolek okienku akcji programu Word. Formanty pokazują wzorzec/szczegół relacji między tabelami w bazie danych programu SQL Server.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Tworzenie okienek akcji za pomocą formantów formularzy systemu Windows, które są związane z danymi.  
  
-   Aby wyświetlić dane w formantach przy użyciu relacji wzorzec/szczegół.  
  
-   Umożliwia wyświetlenie okienka Akcje po otwarciu aplikacji.  
  
> [!NOTE]  
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] lub [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
-   Dostęp do serwera z przykładowej bazy danych Northwind programu SQL Server.  
  
-   Uprawnienia do odczytu i zapisu w bazie danych programu SQL Server.  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Pierwszym krokiem jest utworzenie projektu dokument programu Word.  
  
#### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt  
  
1.  Tworzenie projektu dokument programu Word o nazwie **Moje okienku akcji programu Word**. W kreatorze Wybierz **Utwórz nowy dokument**.  
  
     Aby uzyskać więcej informacji, zobacz [porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio zostanie otwarty nowy dokument programu Word w Projektancie i dodaje **Moje okienku akcji programu Word** projektu do **Eksploratora rozwiązań**.  
  
## <a name="adding-controls-to-the-actions-pane"></a>Dodawanie formantów do okienka Akcje  
 W ramach tego przewodnika należy formant okienka Akcje, który zawiera formanty formularzy systemu Windows z danymi. Dodawanie źródła danych do projektu, a następnie przeciągnij formanty z **źródeł danych** okna do formantu w okienku Akcje.  
  
#### <a name="to-add-an-actions-pane-control"></a>Aby dodać kontrolkę okienka Akcje  
  
1.  Wybierz **Moje okienku akcji programu Word** projektu w **Eksploratora rozwiązań**.  
  
2.  Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.  
  
3.  W **Dodaj nowy element** okno dialogowe, wybierz opcję **formant okienka Akcje**, nadaj jej nazwę **ActionsControl**, a następnie kliknij przycisk **Dodaj**.  
  
#### <a name="to-add-a-data-source-to-the-project"></a>Aby dodać źródła danych do projektu  
  
1.  Jeśli **źródeł danych** okna nie jest widoczne, wyświetl ją, z menu, wybierając **widoku**, **inne okna**, **źródeł danych**.  
  
    > [!NOTE]  
    >  Jeśli **Pokaż źródeł danych** nie jest dostępny, kliknij go, a następnie sprawdź ponownie.  
  
2.  Kliknij przycisk **Dodaj nowe źródło danych** uruchomić **Kreator konfiguracji źródła danych**.  
  
3.  Wybierz **bazy danych** , a następnie kliknij przycisk **dalej**.  
  
4.  Wybierz połączenie danych z bazie danych programu SQL Server Northwind lub Dodaj nowe połączenie przy użyciu **nowe połączenie** przycisku.  
  
5.  Kliknij przycisk **Dalej**.  
  
6.  Wyczyść opcję, aby zapisać połączenie, jeśli jest zaznaczone, a następnie kliknij przycisk **dalej**.  
  
7.  Rozwiń węzeł **tabel** w węźle **obiekty bazy danych** okna.  
  
8.  Zaznacz pole wyboru obok pozycji **dostawców** i **produktów** tabel.  
  
9. Kliknij przycisk **Zakończ**.  
  
 Kreator dodaje **dostawców** tabeli i **produktów** do tabeli **źródeł danych** okna. Dodano również typizowanego zestaw danych do projektu, które są widoczne w **Eksploratora rozwiązań**.  
  
#### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Aby dodać formanty formularzy systemu Windows z danymi z formantem w okienku Akcje  
  
1.  W **źródeł danych** okna, rozwiń węzeł **dostawców** tabeli.  
  
2.  Kliknij strzałkę listy rozwijanej w **nazwa firmy** , a następnie wybierz węzeł **ComboBox**.  
  
3.  Przeciągnij **NazwaFirmy** z **źródeł danych** okna do formantu w okienku Akcje.  
  
     A <xref:System.Windows.Forms.ComboBox> formant jest tworzony na formancie w okienku Akcje. W tym samym czasie <xref:System.Windows.Forms.BindingSource> o nazwie `SuppliersBindingSource`, karty tabeli, a <xref:System.Data.DataSet> zostaną dodane do projektu na pasku składnika.  
  
4.  Wybierz `SuppliersBindingNavigator` w **składnika** na pasku zadań i naciśnij klawisz DELETE. Nie będzie używać `SuppliersBindingNavigator` w tym przewodniku.  
  
    > [!NOTE]  
    >  Usuwanie `SuppliersBindingNavigator` nie powoduje usunięcia wszystkich kodu, który został wygenerowany dla niego. Można usunąć tego kodu.  
  
5.  Przenieś pola kombi tak, aby w ramach etykiety i zmień **rozmiar** właściwości **171, 21**.  
  
6.  W **źródeł danych** okna, rozwiń węzeł **produktów** tabeli będący elementem podrzędnym **dostawców** tabeli.  
  
7.  Kliknij strzałkę listy rozwijanej w **ProductName** , a następnie wybierz węzeł **ListBox**.  
  
8.  Przeciągnij **ProductName** do formantu w okienku Akcje.  
  
     A <xref:System.Windows.Forms.ListBox> formant jest tworzony na formancie w okienku Akcje. W tym samym czasie <xref:System.Windows.Forms.BindingSource> o nazwie `ProductBindingSource` i karty tabeli zostaną dodane do projektu na pasku składnika.  
  
9. Przenieś pola listy, aby była w obszarze etykiety i zmień **rozmiar** właściwości **171,95**.  
  
10. Przeciągnij <xref:System.Windows.Forms.Button> z **przybornika** do okienka Akcje kontroli i umieść go poniżej.  
  
11. Kliknij prawym przyciskiem myszy <xref:System.Windows.Forms.Button>, kliknij przycisk **właściwości** w menu skrótów i Zmień następujące właściwości.  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |**Nazwa**|**Wstaw**|  
    |**Tekst**|**Wstaw**|  
  
12. Zmień rozmiar formantu użytkownika w celu dopasowania kontrolki.  
  
## <a name="setting-up-the-data-source"></a>Konfigurowanie źródła danych  
 Aby skonfigurować źródło danych, Dodaj kod, aby <xref:System.Windows.Forms.UserControl.Load> zdarzeń formant okienka Akcje do wypełnienia kontrolki z danymi z <xref:System.Data.DataTable>i ustaw <xref:System.Windows.Forms.Binding.DataSource%2A> i <xref:System.Windows.Forms.BindingSource.DataMember%2A> właściwości dla każdego formantu.  
  
#### <a name="to-load-the-control-with-data"></a>Aby załadować formantu z danymi  
  
1.  W <xref:System.Windows.Forms.UserControl.Load> obsługi zdarzeń `ActionsControl` klasy, Dodaj następujący kod.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#1)]  
  
2.  W języku C#, należy dołączyć do programu obsługi zdarzeń <xref:System.Windows.Forms.UserControl.Load> zdarzeń. Możesz umieścić ten kod w `ActionsControl` konstruktora, po wywołaniu `InitializeComponent`. Aby uzyskać więcej informacji na temat tworzenia procedury obsługi zdarzeń, zobacz [porady: tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#33](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#33)]  
  
#### <a name="to-set-data-binding-properties-of-the-controls"></a>Aby ustawić właściwości powiązania danych formantów  
  
1.  Wybierz `CompanyNameComboBox` formantu.  
  
2.  W **właściwości** okna, kliknij przycisk z prawej strony **źródła danych** właściwości, a następnie wybierz **suppliersBindingSource**.  
  
3.  Kliknij przycisk z prawej strony **DisplayMember** właściwości, a następnie wybierz **NazwaFirmy**.  
  
4.  Rozwiń węzeł **powiązania danych** właściwości, kliknij przycisk z prawej strony **tekst** właściwości, a następnie wybierz **Brak**.  
  
5.  Wybierz `ProductNameListBox` formantu.  
  
6.  W **właściwości** okna, kliknij przycisk z prawej strony **źródła danych** właściwości, a następnie wybierz **productsBindingSource**.  
  
7.  Kliknij przycisk z prawej strony **DisplayMember** właściwości, a następnie wybierz **ProductName**.  
  
8.  Rozwiń węzeł **powiązania danych** właściwości, kliknij przycisk z prawej strony **SelectedValue** właściwości, a następnie wybierz **Brak**.  
  
## <a name="adding-a-method-to-insert-data-into-a-table"></a>Dodawanie metody do wstawiania danych do tabeli  
 Następne zadanie to odczytywanie danych z formanty powiązane i wypełnianie tabeli w dokumencie programu Word. Najpierw utwórz procedurę formatowania nagłówków w tabeli, a następnie dodaj `AddData` metody do utworzenia i sformatowania tabeli programu Word.  
  
#### <a name="to-format-the-table-headings"></a>Aby sformatować nagłówki tabeli  
  
1.  W `ActionsControl` klasy, Utwórz metodę formatowania nagłówków w tabeli.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#2)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#2)]  
  
#### <a name="to-create-the-table"></a>Aby utworzyć tabelę  
  
1.  W `ActionsControl` klasy, napisanie metody, która spowoduje utworzenie tabeli, jeżeli jeszcze nie istnieje i dodać dane w okienku Akcje do tabeli.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#3)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#3)]  
  
#### <a name="to-insert-text-into-a-word-table"></a>Aby wstawić tekst do tabeli w programie Word  
  
1.  Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń **Wstaw** przycisku.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#4)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#4)]  
  
2.  W języku C#, należy utworzyć programu obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzeń przycisku.  Możesz umieścić ten kod w <xref:System.Windows.Forms.UserControl.Load> obsługi zdarzeń `ActionsControl` klasy.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#5)]  
  
## <a name="showing-the-actions-pane"></a>Wyświetlanie w okienku Akcje  
 W okienku Akcje staje się widoczna po dodaniu do niego formantów.  
  
#### <a name="to-show-the-actions-pane"></a>Aby wyświetlić w okienku Akcje  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ThisDocument.vb** lub **ThisDocument.cs**, a następnie kliknij przycisk **kod widoku** menu skrótów.  
  
2.  Utwórz nowe wystąpienie formantu w górnej części `ThisDocument` klasy wyglądającą jak w następującym przykładzie.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#6)]
     [!code-vb[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#6)]  
  
3.  Dodaj kod, aby <xref:Microsoft.Office.Tools.Word.Document.Startup> obsługi zdarzeń `ThisDocument` wyglądającą jak w następującym przykładzie.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]  
  
## <a name="testing-the-application"></a>Testowanie aplikacji  
 Teraz możesz przetestować dokumencie, aby sprawdzić, czy po otwarciu dokumentu jest widoczny w okienku Akcje. Testowanie dla relacji wzorzec/szczegół w formantach w okienku Akcje i upewnij się, że danych jest wypełniana w wyrazie tabeli, gdy **Wstaw** kliknięciu przycisku.  
  
#### <a name="to-test-your-document"></a>Aby przetestować dokumentu  
  
1.  Naciśnij klawisz F5, aby uruchomić projekt.  
  
2.  Upewnij się, że widoczne jest okienko akcji.  
  
3.  Wybierz firmę, w polu kombi i sprawdź, czy elementy w **produktów** zmiany pola listy.  
  
4.  Kliknij pozycję Wybierz produkt **Wstaw** w okienku Akcje i sprawdź, czy szczegóły produktu są dodawane do tabeli w programie Word.  
  
5.  Wstaw dodatkowe produkty z różnych firm.  
  
## <a name="next-steps"></a>Następne kroki  
 W tym przewodniku przedstawiono podstawowe wiązanie danych do kontrolek okienku akcji programu Word. Poniżej przedstawiono niektóre zadania, które mogą występować:  
  
-   Wiązanie danych do kontrolek w programie Excel. Aby uzyskać więcej informacji, zobacz [wskazówki: wiązanie danych do kontrolek okienku akcji programu Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).  
  
-   Wdrażanie projektu. Aby uzyskać więcej informacji, zobacz [wdrażania rozwiązania do pakietu Office za pomocą technologii ClickOnce za pomocą](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Okienko akcji ― omówienie](../vsto/actions-pane-overview.md)   
 [Porady: Dodawanie okienek akcji do dokumentów programu Word i skoroszytów programu Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Powiązywanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  