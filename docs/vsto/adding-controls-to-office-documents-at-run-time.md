---
title: Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- host controls [Office development in Visual Studio], adding
- Windows Forms controls [Office development in Visual Studio], adding
- Office documents [Office development in Visual Studio, host controls
- user controls [Office development in Visual Studio], adding at runtime
- documents [Office development in Visual Studio], Windows Forms controls
- document-level customizations [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- document-level customizations [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], adding at runtime
- helper methods [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: af280d407a8453b66658ee5395a88d2b91b991b7
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="add-controls-to-office-documents-at-runtime"></a>Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania
  Można dodawać formanty do dokumentu programu Microsoft Office Word i Microsoft Office Excel skoroszytu w czasie wykonywania. Można również usunąć je w czasie wykonywania. Formanty, które są dodawane lub usuwane w czasie wykonywania są nazywane *formantów dynamicznych*.  

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  

 W tym temacie opisano następujące czynności:  

-   [Zarządzanie formantów w czasie wykonywania za pomocą formantu kolekcje](#ControlsCollection).  

-   [Dodaj formanty hosta do dokumentów](#HostControls).  

-   [Dodaj formanty formularzy systemu Windows do dokumentów](#WindowsForms).  

 ![łącze do wideo](../vsto/media/playvideo.gif "łącze do wideo") dla powiązanych pokaz wideo, zobacz [jak I: Dodaj formanty do dokumentu powierzchni w czasie wykonywania?](http://go.microsoft.com/fwlink/?LinkId=132782).  

##  <a name="ControlsCollection"></a> Zarządzanie formantów w czasie wykonywania za pomocą kontrolki kolekcji  
 Aby dodać, pobrać lub usunąć formantów w czasie wykonywania, należy użyć metody pomocnika <xref:Microsoft.Office.Tools.Excel.ControlCollection> i <xref:Microsoft.Office.Tools.Word.ControlCollection> obiektów.  

 Sposób uzyskać dostępu do tych obiektów, zależy od typu projektu, który tworzysz:  

-   W projekcie poziomie dokumentu dla programu Excel, użyj <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> właściwość `Sheet1`, `Sheet2`, i `Sheet3` klasy. Aby uzyskać więcej informacji na temat tych klas, zobacz [element hosta arkusza](../vsto/worksheet-host-item.md).  

-   W projekcie poziomie dokumentu dla programu Word, użyj <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> właściwość `ThisDocument` klasy. Aby uzyskać więcej informacji na temat tej klasy, zobacz [element hosta dokumentu](../vsto/document-host-item.md).  

-   W projekcie dodatku narzędzi VSTO dla programu Excel lub Word użyć `Controls` właściwość <xref:Microsoft.Office.Tools.Excel.Worksheet> lub <xref:Microsoft.Office.Tools.Word.Document> generowany w czasie wykonywania. Aby uzyskać więcej informacji na temat generowania tych obiektów w czasie wykonywania, zobacz [dokumentów rozszerzania programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  

### <a name="add-controls"></a>Dodawanie formantów  
 <xref:Microsoft.Office.Tools.Excel.ControlCollection> i <xref:Microsoft.Office.Tools.Word.ControlCollection> typy metody pomocnicze, które można dodać kontrolki hosta i typowych formantów formularzy systemu Windows do dokumentów i arkuszy. Każda nazwa metody ma format `Add` *kontrolować klasy*, gdzie *kontrolować klasy* jest nazwą klasy formantu, który chcesz dodać. Na przykład, aby dodać <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu do dokumentu, użyj <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddNamedRange%2A> metody.  

 Poniższy przykładowy kod dodaje <xref:Microsoft.Office.Tools.Excel.NamedRange> do `Sheet1` w projektach na poziomie dokumentu dla programu Excel.  

 [!code-vb[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#3)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#3)]  

### <a name="access-and-delete-controls"></a>Kontroli dostępu i delete  
 Można użyć `Controls` właściwość <xref:Microsoft.Office.Tools.Excel.Worksheet> lub <xref:Microsoft.Office.Tools.Word.Document> do iterowania po wszystkich kontrolek w dokumencie, łącznie z formantami dodawanymi w czasie projektowania. Formanty dodane w czasie projektowania są również nazywane *formantów statycznych*.  

 Możesz usunąć formantów dynamicznych, wywołując `Delete` metody sterowania lub przez wywołanie metody `Remove` metody każdej kolekcji formantów. Poniższy przykład kodu wykorzystuje <xref:Microsoft.Office.Tools.Excel.ControlCollection.Remove%2A> metodę, aby usunąć <xref:Microsoft.Office.Tools.Excel.NamedRange> z `Sheet1` w projektach na poziomie dokumentu dla programu Excel.  

 [!code-vb[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#4)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#4)]  

 Nie można usunąć statyczne formantów w czasie wykonywania. Jeśli spróbujesz użyć `Delete` lub `Remove` metodę statyczną kontrolkę, Usuń <xref:Microsoft.Office.Tools.CannotRemoveControlException> zostanie wygenerowany.  

> [!NOTE]  
>  Nie usuwaj programowo formantów w `Shutdown` obsługi zdarzeń dokumentu. Elementy interfejsu użytkownika dokumentu nie będą dostępne podczas `Shutdown` zdarzenia. Jeśli chcesz usunąć formanty przed zamknięciem dokumentu, Dodaj swój kod obsługi zdarzeń dla innego zdarzenia, takie jak <xref:Microsoft.Office.Tools.Word.Document.BeforeClose> lub <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> dla programu Word, lub <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeClose>, lub <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeSave> dla programu Excel.  

##  <a name="HostControls"></a> Dodaj formanty hosta do dokumentów  
 Po dodaniu programowo hosta formantów do dokumentów, należy podać nazwę, która unikatowo identyfikuje formant i musisz określić, gdzie można dodać kontrolki w dokumencie. Aby uzyskać szczegółowe instrukcje zobacz następujące tematy:  

-   [Porady: dodawanie formantów ListObject do arkuszy](../vsto/how-to-add-listobject-controls-to-worksheets.md)  

-   [Porady: dodawanie formantów NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md)  

-   [Porady: dodawanie formantów wykresu do arkuszy](../vsto/how-to-add-chart-controls-to-worksheets.md)  

-   [Porady: Dodawanie zawartości formantów do dokumentów programu Word](../vsto/how-to-add-content-controls-to-word-documents.md)  

-   [Porady: dodawanie formantów zakładek do dokumentów programu Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)  

 Aby uzyskać informacje o formantach hosta, zobacz [elementów, a informacje o formantach](../vsto/host-items-and-host-controls-overview.md).  

 Gdy dokumentu jest zapisane, a następnie zamknięte, wszystkie formanty hosta utworzony dynamicznie zostały odłączone od ich zdarzeń i utracą ich funkcji wiązania danych. Można dodać kod do rozwiązania, aby ponownie utworzyć formanty hosta po otwarciu dokumentu. Aby uzyskać więcej informacji, zobacz [utrwalić formantów dynamicznych w dokumentach pakietu Office](../vsto/persisting-dynamic-controls-in-office-documents.md).  

> [!NOTE]  
>  Metody pomocnicze nie są dostarczane dla następujących hostowania formantów, ponieważ tych kontrolek nie można dodać programistycznie do dokumentów: <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>, <xref:Microsoft.Office.Tools.Word.XMLNode>, i <xref:Microsoft.Office.Tools.Word.XMLNodes>.  

##  <a name="WindowsForms"></a> Dodaj formanty formularzy systemu Windows do dokumentów  
 Po dodaniu programowo formantu formularzy systemu Windows do dokumentu, należy podać lokalizację formantu i nazwy, które jednoznacznie identyfikuje formant. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Udostępnia metody pomocy dla każdego formantu. Te metody są przeciążone tak, aby można przekazać zakres lub określone współrzędne lokalizacji kontrolki.  

 Gdy dokumentu jest zapisane, a następnie zamknięte, wszystkie formanty formularzy systemu Windows utworzony dynamicznie zostaną usunięte z dokumentu. Można dodać kod do rozwiązania, aby ponownie utworzyć formantów po otwarciu dokumentu. Jeśli utworzysz dynamiczne formanty formularzy systemu Windows przy użyciu dodatku VSTO otoki ActiveX formantów pozostają w dokumencie. Aby uzyskać więcej informacji, zobacz [utrwalić formantów dynamicznych w dokumentach pakietu Office](../vsto/persisting-dynamic-controls-in-office-documents.md).  

> [!NOTE]  
>  Formanty formularzy systemu Windows nie można dodać programistycznie do dokumentów chronionych. Jeśli nie można programistycznie Chroń, dokumentu programu Word lub arkuszu programu Excel, aby dodać kontrolkę, należy napisać dodatkowy kod w celu usunięcia formantu ActiveX otoki, gdy dokument zostanie zamknięty. Kontrolki ActiveX otoki nie zostanie automatycznie usunięta z chronionych dokumentów.  

### <a name="add-custom-controls"></a>Dodaj formanty niestandardowe  
 Jeśli chcesz dodać <xref:System.Windows.Forms.Control> nie jest obsługiwana przez metody pomocnika dostępne, takich jak kontrola użytkownika niestandardowego, należy użyć następujących metod:  

-   Dla programu Excel, użyj jednej z <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> metody <xref:Microsoft.Office.Tools.Excel.ControlCollection> obiektu.  

-   Dla programu Word, użyj jednej z <xref:Microsoft.Office.Tools.Word.ControlCollection.AddControl%2A> metody <xref:Microsoft.Office.Tools.Word.ControlCollection> obiektu.  

 Aby dodać kontrolki, należy przekazać <xref:System.Windows.Forms.Control>, lokalizacji dla formantu oraz nazwę, która unikatowo identyfikuje formant do `AddControl` metody. `AddControl` Metoda zwraca obiekt definiujący jak kontrolki współdziała z arkusza kalkulacyjnego lub dokumentu. `AddControl` Metoda zwraca <xref:Microsoft.Office.Tools.Excel.ControlSite> (dla programu Excel) lub <xref:Microsoft.Office.Tools.Word.ControlSite> obiektu (dla programu Word).  

 Poniższy przykład kodu pokazuje sposób użycia <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> metody dynamiczne dodawanie formantu niestandardowego użytkownika do arkusza w projektach na poziomie dokumentu programu Excel. W tym przykładzie kontrolki użytkownika o nazwie `UserControl1`i <xref:Microsoft.Office.Interop.Excel.Range> nosi nazwę `range1`. Aby użyć tego przykładu, uruchom go z `Sheet` *n* klasy w projekcie.  

 [!code-vb[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#2)]
 [!code-csharp[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#2)]  

### <a name="use-members-of-custom-controls"></a>Użyj członkami formanty niestandardowe  
 Po zakończeniu korzystania z jednego z `AddControl` metody, aby dodać kontrolkę do arkusza lub dokument, możesz teraz mają dwa obiekty inny formant:  

-   <xref:System.Windows.Forms.Control> Reprezentujący kontrolkę niestandardową.  

-   `ControlSite`, `OLEObject`, Lub `OLEControl` obiekt, który reprezentuje kontrolkę po został dodany do arkusza lub dokumentu.  

 Wiele właściwości i metody są wspólne dla tych kontrolek. Jest ważne, dostęp do tych elementów członkowskich za pomocą odpowiedniej kontrolki:  

-   Aby uzyskać dostęp do elementów członkowskich, które należeć tylko do kontrolki niestandardowej, należy użyć <xref:System.Windows.Forms.Control>.  

-   Aby uzyskać dostęp do elementów członkowskich, które są udostępniane przez formanty, należy użyć `ControlSite`, `OLEObject`, lub `OLEControl` obiektu.  

 Jeśli dostęp do udostępnionego elementu członkowskiego z <xref:System.Windows.Forms.Control>, może być niemożliwe bez ostrzeżenia lub powiadomienie, lub może spowodować nieprawidłowe wyniki. Należy zawsze używać metody lub właściwości `ControlSite`, `OLEObject`, lub `OLEControl` obiekt chyba że potrzebne metoda lub właściwość nie jest dostępny; dopiero wtedy powinien odniesienia należy <xref:System.Windows.Forms.Control>.  

 Na przykład zarówno <xref:Microsoft.Office.Tools.Excel.ControlSite> klasy i <xref:System.Windows.Forms.Control> klasa ma `Top` właściwości. Aby pobrać lub ustawić odległość między górną krawędzią formantu a górnej części dokumentu, należy użyć <xref:Microsoft.Office.Tools.Excel.ControlSite.Top%2A> właściwość <xref:Microsoft.Office.Tools.Excel.ControlSite>, a nie <xref:System.Windows.Forms.Control.Top%2A> właściwość <xref:System.Windows.Forms.Control>.  

 [!code-vb[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#3)]
 [!code-csharp[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#3)]  

## <a name="see-also"></a>Zobacz także  
 [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)   
 [Utrwalanie formantów dynamicznych w dokumentach pakietu Office](../vsto/persisting-dynamic-controls-in-office-documents.md)   
 [Porady: dodawanie formantów ListObject do arkuszy](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [Porady: dodawanie formantów NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Porady: dodawanie formantów wykresu do arkuszy](../vsto/how-to-add-chart-controls-to-worksheets.md)   
 [Porady: dodawanie formantów zawartości do dokumentów programu Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Porady: dodawanie formantów zakładek do dokumentów programu Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Formanty formularzy systemu Windows na przegląd dokumentów pakietu Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Porady: dodawanie formantów formularzy systemu Windows do dokumentów pakietu Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
