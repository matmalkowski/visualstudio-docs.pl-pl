---
title: Okienko akcji ― omówienie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], about actions panes
- actions panes [Office development in Visual Studio]
- smart documents [Office development in Visual Studio]
- user controls [Office development in Visual Studio], actions panes
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 50f39b6fc292bba2081d8eb5c3bc87d6f9041b49
ms.sourcegitcommit: 04a717340b4ab4efc82945fbb25dfe58add2ee4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="actions-pane-overview"></a>Okienko akcji ― Omówienie
  W okienku Akcje jest modyfikowalny **akcji dla dokumentów** okienka zadań, który jest dołączony do określonego dokumentu programu Microsoft Office Word lub skoroszyt programu Microsoft Office Excel. W okienku Akcje znajduje się w okienku zadań Office oraz inne okienka wbudowanego zadania, takie jak **źródło XML** okienka zadań w programie Excel lub **style i formatowanie** okienka zadań w programie Word. Formanty formularzy systemu Windows lub formantów WPF umożliwia projektowanie interfejsu użytkownika w okienku Akcje.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  

 Okienku akcji programu można utworzyć tylko w przypadku dostosowania poziomie dokumentu dla programu Word i Excel. Nie można utworzyć w okienku Akcje w dodatku VSTO. Aby uzyskać więcej informacji, zobacz [dostępne funkcje uporządkowane według aplikacji pakietu Office i typu projektu](../vsto/features-available-by-office-application-and-project-type.md).  

> [!NOTE]  
>  W okienku Akcje różni się od niestandardowych okienek zadań. Niestandardowe okienka zadań są skojarzone z aplikacją, określonego dokumentu. Niestandardowe okienka zadań można tworzyć w dodatkach VSTO niektórych aplikacji pakietu Microsoft Office. Aby uzyskać więcej informacji, zobacz [niestandardowego okienka zadań](../vsto/custom-task-panes.md).  

 ![łącze do wideo](../vsto/media/playvideo.gif "łącze do wideo") dla powiązanych pokaz wideo, zobacz [jak czy I: Użyj WPF kontrolki wewnątrz okienku akcji Excel?](http://go.microsoft.com/fwlink/?LinkId=132763).

## <a name="displaying-the-actions-pane"></a>Wyświetlanie w okienku Akcje  
 W okienku Akcje jest reprezentowana przez <xref:Microsoft.Office.Tools.ActionsPane> klasy. Podczas tworzenia projektu poziomie dokumentu wystąpienia tej klasy jest dostępna w kodzie za pomocą `ActionsPane` pole `ThisWorkbook` (dla programu Excel) lub `ThisDocument` (dla programu Word) klasy w projekcie. Aby wyświetlić w okienku Akcje, Dodaj formant formularzy systemu Windows do <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> właściwości `ActionsPane` pola. Poniższy przykładowy kod dodaje formantu o nazwie `actions` w okienku Akcje.  

 [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
 [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]  

 W okienku Akcje staje się widoczna w czasie wykonywania, jak formantu jawnie dodać do niego. Po wyświetleniu w okienku Akcje można dynamicznie Dodawanie lub usuwanie formantów w odpowiedzi na działania użytkownika. Zwykle, Dodaj kod, aby wyświetlić w okienku Akcje `Startup` obsługi zdarzeń `ThisDocument` lub `ThisWorkbook` tak aby były widoczne w okienku Akcje po pierwszym otwarciu użytkownika dokumentu. Jednak można wyświetlić w okienku Akcje tylko w odpowiedzi na akcję użytkownika w dokumencie. Na przykład można dodać kod `Click` zdarzeń formantu w dokumencie.  

### <a name="adding-multiple-controls-to-the-actions-pane"></a>Dodawanie wielu formantów w okienku Akcje  
 Podczas dodawania wielu formantów w okienku Akcje, grupowanie formantów w formancie użytkownika a następnie dodaj kontrolkę użytkownika do <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> właściwości. Ten proces obejmuje następujące kroki:  

1.  Utwórz interfejs użytkownika (UI) w okienku Akcje, dodając **formant okienka Akcje** lub **kontrolki użytkownika** elementu do projektu. Elementy te obejmują niestandardowych formularzy systemu Windows <xref:System.Windows.Forms.UserControl> klasy. **Formant okienka Akcje** i **kontrolki użytkownika** elementy są równoważne; jedyna różnica polega na ich nazwy.  

2.  Dodaj formanty formularzy systemu Windows do <xref:System.Windows.Forms.UserControl> przy użyciu narzędzia Projektant lub pisanie kodu.  

    > [!NOTE]  
    >  Można również dodać formantów WPF w okienku Akcje, przez dodanie WPF <xref:System.Windows.Controls.UserControl> do formularzy systemu Windows <xref:System.Windows.Forms.UserControl>. Aby uzyskać więcej informacji, zobacz [za pomocą formantów WPF w rozwiązaniach pakietu Office](../vsto/using-wpf-controls-in-office-solutions.md).  

3.  Dodaje wystąpienie Kontrolki niestandardowe użytkownika z formantami, które są zawarte w `ActionsPane` pole `ThisWorkbook` (dla programu Excel) lub `ThisDocument` (dla programu Word) klasy w projekcie.  

 Przykłady ilustrujące ten proces bardziej szczegółowo opisano w części [porady: Dodawanie okienek akcji do dokumentów programu Word i skoroszytów programu Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  

## <a name="hiding-the-actions-pane"></a>Ukrywanie okienka Akcje  
 Mimo że <xref:Microsoft.Office.Tools.ActionsPane> klasa ma <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> — metoda i <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> właściwości, nie można usunąć okienka działań z interfejsu użytkownika przy użyciu wszystkich członków <xref:Microsoft.Office.Tools.ActionsPane> samej klasy. Wywoływanie <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> metody lub ustawienie <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> właściwości **false** ukrywa tylko formanty w okienku Akcje; nie ukrywa w okienku zadań.  

 Aby ukryć okienka zadań w rozwiązaniu, masz kilka opcji:  

-   Dla programu Word, ustaw <xref:Microsoft.Office.Interop.Word.TaskPane.Visible%2A> właściwość <xref:Microsoft.Office.Interop.Word.TaskPane> obiekt, który reprezentuje okienko akcji dla dokumentów do **false**. Poniższy przykładowy kod jest przeznaczona do uruchamiania z `ThisDocument` klasy w projekcie.  

     [!code-csharp[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#34)]
     [!code-vb[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#34)]  

-   Dla programu Excel, ustaw <xref:Microsoft.Office.Interop.Excel._Application.DisplayDocumentActionTaskPane%2A> właściwość <xref:Microsoft.Office.Tools.Excel.Workbook.Application%2A> do obiektu **false**. Poniższy przykładowy kod jest przeznaczona do uruchamiania z `ThisWorkbook` klasy w projekcie.  

     [!code-csharp[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#11)]  

-   Dla programu Word i Excel, można również ustawić <xref:Microsoft.Office.Core.CommandBar.Visible%2A> właściwości paska poleceń reprezentujący okienka zadań do **false**. Poniższy przykładowy kod jest przeznaczona do uruchamiania z `ThisDocument` lub `ThisWorkbook` klasy w projekcie.  

     [!code-csharp[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#9)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#9)]  

### <a name="clearing-the-actions-pane-when-the-document-is-opened"></a>Wyczyszczenie po dokumentu dla okienka Akcje jest otwarty.  
 Gdy użytkownik zapisuje dokument, gdy jest widoczny w okienku Akcje, w okienku Akcje jest widoczna za każdym razem, gdy dokument zostanie otwarty, czy w okienku Akcje zawiera wszystkie formanty. Jeśli chcesz kontrolować Jeśli wygląda na to, wywołanie <xref:Microsoft.Office.Tools.ActionsPane.Clear%2A> metody `ActionsPane` w `Startup` obsługi zdarzeń `ThisDocument` lub `ThisWorkbook` aby upewnić się, że w okienku Akcje nie jest widoczne, gdy dokument jest otwarty.  

### <a name="determining-when-the-actions-pane-is-closed"></a>Określanie okienka Akcje po zamknięciu  
 Nie ma żadnego zdarzenia, które jest wywoływane, gdy zostanie zamknięty w okienku Akcje. Mimo że <xref:Microsoft.Office.Tools.ActionsPane> klasa ma <xref:Microsoft.Office.Tools.ActionsPane.VisibleChanged> zdarzenie, to zdarzenie nie jest wywoływane, gdy użytkownik zamyka w okienku Akcje. Zamiast tego, to zdarzenie jest wywoływane, gdy formantów w okienku Akcje są ukryte przez wywołanie metody <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> metody lub przez ustawienie <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> właściwości **false**.  

 Gdy użytkownik zamyka w okienku Akcje, użytkownik może wyświetlać go ponownie, wykonując jedną z poniższych procedur w interfejsie użytkownika (UI) aplikacji.  

##### <a name="to-display-the-actions-pane-by-using-the-ui-of-word-or-excel"></a>Aby wyświetlić w okienku Akcje, za pomocą interfejsu użytkownika programu Word czy Excel  

1.  Na wstążce kliknij **widoku** kartę.  

2.  W **Pokaż/Ukryj** kliknij przycisk **akcji dla dokumentów** przycisk przełącznika.  

## <a name="programming-actions-pane-events"></a>Zdarzenia w okienku Akcje programowania  
 Można dodać wiele formantów użytkownika w okienku Akcje, a następnie wpisz kod w celu reagowania na zdarzenia w dokumencie przez wyświetlanie i ukrywanie formantów użytkownika. Jeśli mapujesz elementów schematu XML do dokumentu, zawsze, gdy punkt wstawiania znajduje się w jednym z elementów XML można wyświetlić niektórych formantów użytkownika w okienku Akcje. Aby uzyskać więcej informacji, zobacz [porady: mapy schematów do programu Word dokumenty w Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md) i [jak: schematy mapy do arkuszy w Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md).  

 Można również napisać kod do reagowania na zdarzenia wszystkich obiektów, w tym kontroli hosta, aplikacji lub zdarzenia dokumentu. Aby uzyskać więcej informacji, zobacz [wskazówki: Programowanie przed zdarzeń formantu NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).  

## <a name="binding-data-to-controls-on-the-actions-pane"></a>Wiązanie danych z kontrolkami w okienku Akcje  
 Formanty w okienku Akcje mają te same możliwości wiązania danych jako formantów na formularzach systemu Windows. Kontrolki można powiązać ze źródłami danych, takie jak zestawy danych, typizowanych zestawów danych i XML. Aby uzyskać więcej informacji, zobacz [powiązania danych i formularze systemu Windows](/dotnet/framework/winforms/data-binding-and-windows-forms).  

 Formanty w okienku Akcje i w dokumencie można powiązać z tym samym zestawem danych. Na przykład można utworzyć relacji wzorzec/szczegół między kontrolkami w okienku Akcje i formantów w arkuszu. Aby uzyskać więcej informacji, zobacz [wskazówki: wiązanie danych do kontrolek okienku akcji programu Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).  

## <a name="validating-data-in-actions-pane-controls"></a>Sprawdzanie poprawności danych w kontrolkach okienka Akcje  
 Jeśli wyświetlane w oknie komunikatu <xref:System.Windows.Forms.Control.Validating> obsługi zdarzeń formantu w okienku Akcje, zdarzenie może zostać wywołane podczas fokusu z formantu w oknie komunikatu po raz drugi. Aby uniknąć tego problemu, należy użyć <xref:System.Windows.Forms.ErrorProvider> formantu, aby wyświetlić komunikaty o błędach weryfikacji.  

## <a name="user-control-stacking-order"></a>Kolejność układania kontrolki użytkownika  
 Jeśli używasz wielu formantów użytkownika można napisać kod do prawidłowo stosu kontrolek użytkownika w okienku Akcje czy jest zadokowany w pionie lub poziomie. Należy określić kolejność kontrolek użytkownika w okienku akcji przy użyciu <xref:Microsoft.Office.Tools.StackStyle> wyliczenie <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> właściwości. Aby uzyskać więcej informacji, zobacz [porady: Zarządzanie układem formantu w okienkach akcji](../vsto/how-to-manage-control-layout-on-actions-panes.md)  

 <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> Właściwości można wziąć pod uwagę następujące <xref:Microsoft.Office.Tools.StackStyle> wartości wyliczenia.  

|Styl stosu|Definicja|  
|--------------------|----------------|  
|FromBottom|Stosu w dolnej części okienka działań.|  
|FromLeft|Stos z lewej strony w okienku Akcje.|  
|FromRight|Stos z prawej strony, w okienku Akcje.|  
|FromTop|Stos od góry w okienku Akcje.|  
|Brak|Nie stosu zdefiniowane. kolejność jest kontrolowana przez dewelopera.|  

 Poniższy kod ustawia <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> stosu kontrolek użytkownika w górnej części okienka Akcje dla właściwości.  

 [!code-csharp[Trin_VstcoreActionsPaneExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#10)]
 [!code-vb[Trin_VstcoreActionsPaneExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#10)]  

## <a name="anchoring-controls"></a>Zakotwiczanie formantów  
 Jeśli użytkownik zmieni rozmiar okienka akcji w czasie wykonywania, zmieniać rozmiar kontrolki z panelu akcji. Można użyć <xref:System.Windows.Forms.Control.Anchor%2A> właściwości formantu formularzy systemu Windows z formantami zakotwiczenia w okienku Akcje. Formanty formularzy systemu Windows w formancie użytkownika można również zakotwiczyć w taki sam sposób. Aby uzyskać więcej informacji, zobacz [porady: zakotwiczenie formantów na formularzach systemu Windows](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms).  

## <a name="resizing-the-actions-pane"></a>Zmiana rozmiaru w okienku Akcje  
 Nie można bezpośrednio zmienić rozmiar <xref:Microsoft.Office.Tools.ActionsPane> ponieważ <xref:Microsoft.Office.Tools.ActionsPane> jest osadzony w okienku zadań. Jednak programowo można zmienić szerokość w okienku zadań przez ustawienie <xref:Microsoft.Office.Core.CommandBar.Width%2A> właściwość <xref:Microsoft.Office.Core.CommandBar> reprezentujący w okienku zadań. Można zmienić wysokość w okienku zadań, gdy jest zadokowany poziomo, lub jest zmiennoprzecinkową.  

 Programowane Zmienianie rozmiaru okienka zadania nie jest zalecane, ponieważ użytkownik powinien mieć możliwość wybierz rozmiar okienka zadań, który najlepiej odpowiada potrzebom ich. Jednak jeśli należy zmienić rozmiar szerokość panelu zadań, można użyć poniższego kodu do wykonania tego zadania.  

 [!code-csharp[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#102)]
 [!code-vb[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#102)]  

## <a name="repositioning-the-actions-pane"></a>Zmienianie położenia w okienku Akcje  
 Nie można bezpośrednio zmienić położenie <xref:Microsoft.Office.Tools.ActionsPane> ponieważ jest osadzony w okienku zadań. Jednak programowo można przenieść w okienku zadań przez ustawienie <xref:Microsoft.Office.Core.CommandBar.Position%2A> właściwość <xref:Microsoft.Office.Core.CommandBar> reprezentujący w okienku zadań.  

 Programowo położenia w okienku zadań jest zwykle niezalecane, ponieważ użytkownik powinno być możliwe wybranie pozycji okienka zadań na ekranie, który najlepiej odpowiada potrzebom własnego. Jednak w okienku zadań konieczne jest przejście do określonej pozycji, można użyć poniższego kodu do wykonania tego zadania.  

 [!code-csharp[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#100)]
 [!code-vb[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#100)]  

> [!NOTE]  
>  Użytkownicy końcowi ręcznie zmienić położenie w okienku zadań w dowolnym momencie. Nie istnieje sposób, aby upewnić się, że w okienku zadań pozostaną zadokowanych w pozycji wskazanej programowo. Można jednak Sprawdź, czy zmiany orientacji i upewnij się, stos formantów w okienku Akcje w odpowiednim kierunku. Aby uzyskać więcej informacji, zobacz [porady: Zarządzanie układem formantu w okienkach akcji](../vsto/how-to-manage-control-layout-on-actions-panes.md).  

 Ustawienie <xref:Microsoft.Office.Tools.ActionsPane.Top%2A> i <xref:Microsoft.Office.Tools.ActionsPane.Left%2A> właściwości <xref:Microsoft.Office.Tools.ActionsPane> nie powoduje zmiany położenia, ponieważ <xref:Microsoft.Office.Tools.ActionsPane> obiekt jest osadzony w okienku zadań.  

 Jeśli nie jest zadokowany w okienku zadań, możesz ustawić <xref:Microsoft.Office.Core.CommandBar.Top%2A> i <xref:Microsoft.Office.Core.CommandBar.Left%2A> właściwości <xref:Microsoft.Office.Core.CommandBar> reprezentujący w okienku zadań. Poniższy kod przenosi okienka zadań niezadokowanego lewego górnego rogu dokumentu.  

 [!code-csharp[Trin_VstcoreActionsPaneWord#101](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#101)]
 [!code-vb[Trin_VstcoreActionsPaneWord#101](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#101)]  

## <a name="see-also"></a>Zobacz też  
 [Korzystanie z formantów WPF w rozwiązaniach pakietu Office](../vsto/using-wpf-controls-in-office-solutions.md)   
 [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)   
 [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Porady: Dodawanie okienek akcji do dokumentów programu Word i skoroszytów programu Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Wskazówki: Wstawianie tekstu do dokumentu z okienka akcji](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Wskazówki: Wiązanie danych do kontrolek okienku akcji programu Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)   
 [Wskazówki: Wiązanie danych do kontrolek okienku akcji programu Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)   
 [Porady: Zarządzanie układem formantu w okienkach akcji](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Przewodnik: Wstawianie tekstu do dokumentu z okienka akcji](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
