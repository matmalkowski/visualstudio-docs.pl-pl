---
title: 'Porady: dodawanie formantów ListObject do arkuszy'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ListObject control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5af88022529263446c82fc27aee9d781d7da945f
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2018
---
# <a name="how-to-add-listobject-controls-to-worksheets"></a>Porady: dodawanie formantów ListObject do arkuszy
  Możesz dodać <xref:Microsoft.Office.Tools.Excel.ListObject> formantów do arkusza w czasie projektowania i w czasie wykonywania w projektach na poziomie dokumentu programu Microsoft Office Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Można również dodać <xref:Microsoft.Office.Tools.Excel.ListObject> formantów w czasie wykonywania w projektach w dodatku VSTO.  
  
 W tym temacie opisano następujące zadania:  
  
-   [Dodawanie formantów ListObject w czasie projektowania](#designtime)  
  
-   [Dodawanie formantów ListObject w czasie wykonywania w projektach na poziomie dokumentu](#runtimedoclevel)  
  
-   [Dodawanie formantów ListObject w czasie wykonywania w projekcie dodatku narzędzi VSTO](#runtimeaddin)  
  
 Aby uzyskać więcej informacji na temat <xref:Microsoft.Office.Tools.Excel.ListObject> formantów, zobacz [ListObject — formant](../vsto/listobject-control.md).  
  
##  <a name="designtime"></a> Dodawanie formantów ListObject w czasie projektowania  
 Istnieje kilka sposobów, aby dodać <xref:Microsoft.Office.Tools.Excel.ListObject> formantów do arkusza w projektach na poziomie dokumentu w czasie projektowania: Z programu Excel w programie Visual Studio **przybornika**i z **źródeł danych** okna.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-use-the-ribbon-in-excel"></a>Aby użyć na Wstążce w programie Excel  
  
1.  Na **Wstaw** karcie **tabel** kliknij przycisk **tabeli**.  
  
2.  Zaznacz komórkę lub komórki, które mają być uwzględnione na liście i kliknij przycisk **OK**.  
  
#### <a name="to-use-the-toolbox"></a>Aby użyć przybornika  
  
1.  Z **formanty Excel** karcie **przybornika**, przeciągnij <xref:Microsoft.Office.Tools.Excel.ListObject> w arkuszu.  
  
     **Dodaj formant ListObject** zostanie wyświetlone okno dialogowe.  
  
2.  Zaznacz komórkę lub komórki, które mają być uwzględnione na liście i kliknij przycisk **OK**.  
  
     Jeśli nie chcesz zachować domyślną nazwę, można zmienić nazwę w **właściwości** okna.  
  
#### <a name="to-use-the-data-sources-window"></a>Aby korzystanie z okna źródeł danych  
  
1.  Otwórz **źródeł danych** okna i Utwórz źródło danych dla projektu. Aby uzyskać więcej informacji, zobacz [dodać nowe połączenia](../data-tools/add-new-connections.md).  
  
2.  Przeciągnij tabelę z **źródeł danych** okna do arkusza.  
  
     Z danymi <xref:Microsoft.Office.Tools.Excel.ListObject> formant został dodany do arkusza. Aby uzyskać więcej informacji, zobacz [powiązania danych i formularze systemu Windows](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
##  <a name="runtimedoclevel"></a> Dodawanie formantów ListObject w czasie wykonywania w projektach na poziomie dokumentu  
 Możesz dodać <xref:Microsoft.Office.Tools.Excel.ListObject> kontroli dynamicznie w czasie wykonywania. Dzięki temu można utworzyć kontrolki hosta w odpowiedzi na zdarzenia. Lista utworzony dynamicznie obiektów nie są zachowywane w arkuszu zgodnie z formanty hosta po zamknięciu arkusza. Aby uzyskać więcej informacji, zobacz [dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>Aby programowo Dodaj formant ListObject do arkusza  
  
1.  W <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> obsługi zdarzeń `Sheet1`, Wstaw następujący kod, aby dodać <xref:Microsoft.Office.Tools.Excel.ListObject> formantu do komórek **A1** za pośrednictwem **A4**.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#2)]  
  
##  <a name="runtimeaddin"></a> Dodawanie formantów ListObject w czasie wykonywania w projekcie dodatku narzędzi VSTO  
 Możesz dodać <xref:Microsoft.Office.Tools.Excel.ListObject> programowo sterowania wszystkie otwarte arkusza w projekcie dodatku narzędzi VSTO. Lista utworzony dynamicznie obiektów nie są zachowywane w arkuszu zgodnie z formanty hosta podczas arkusz jest zapisane, a następnie zamknięte. Aby uzyskać więcej informacji, zobacz [dokumentów rozszerzania programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>Aby programowo Dodaj formant ListObject do arkusza  
  
1.  Poniższy kod wywoła element hosta arkusza, który jest oparty na otwieranie arkusza, a następnie dodanie <xref:Microsoft.Office.Tools.Excel.ListObject> formantu do komórek **A1** za pośrednictwem **A4**.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#8](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#8)]
     [!code-vb[Trin_Excel_Dynamic_Controls#8](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#8)]  
  
## <a name="see-also"></a>Zobacz także  
 [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)   
 [ListObject — formant](../vsto/listobject-control.md)   
 [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)   
 [Obiekty hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md)   
 [Porady: zmiana rozmiaru formantów ListObject](../vsto/how-to-resize-listobject-controls.md)   
 [Wiązanie danych do formantów w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Ograniczenia programowe elementów hosta i formantów hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  