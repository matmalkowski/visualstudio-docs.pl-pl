---
title: "Porady: dodawanie formantów NamedRange do arkuszy | Dokumentacja firmy Microsoft"
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
- ranges, adding to worksheets
- NamedRange control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
ms.assetid: da7ec48f-92cb-4fa3-b3e2-447c238d17a8
caps.latest.revision: "54"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 44aefbbce0d910efc6e92f2acb75993598f098ab
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-namedrange-controls-to-worksheets"></a>Porady: dodawanie formantów NamedRange do arkuszy
  Możesz dodać <xref:Microsoft.Office.Tools.Excel.NamedRange> formantów do arkusza w czasie projektowania i w czasie wykonywania w projektach na poziomie dokumentu programu Microsoft Office Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Można również dodać <xref:Microsoft.Office.Tools.Excel.NamedRange> formantów w czasie wykonywania w projektach w dodatku VSTO.  
  
 W tym temacie opisano następujące zadania:  
  
-   [Dodawanie formantów NamedRange w czasie projektowania](#designtime)  
  
-   [Dodawanie formantów NamedRange w czasie wykonywania w projektach na poziomie dokumentu](#runtimedoclevel)  
  
-   [Dodawanie formantów NamedRange w czasie wykonywania w projekcie dodatku narzędzi VSTO](#runtimeaddin)  
  
 Aby uzyskać więcej informacji na temat <xref:Microsoft.Office.Tools.Excel.NamedRange> formantów, zobacz [namedrange — formant](../vsto/namedrange-control.md).  
  
##  <a name="designtime"></a>Dodawanie formantów NamedRange w czasie projektowania  
 Istnieje kilka sposobów, aby dodać <xref:Microsoft.Office.Tools.Excel.NamedRange> formantów do arkusza w projektach na poziomie dokumentu w czasie projektowania: z programu Excel w programie Visual Studio **przybornika**i z **źródeł danych** okna.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-name-box-in-excel"></a>Aby dodać formantu NamedRange do arkusza w polu nazwy w programie Excel  
  
1.  Zaznacz komórkę lub komórki, które chcesz uwzględnić w nazwanego zakresu.  
  
2.  W **nazwa**, wpisz nazwę zakresu, i naciśnij klawisz ENTER.  
  
     **Nazwa** znajduje się obok pasku formuły, nad kolumny **A** arkusza.  
  
#### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-toolbox"></a>Aby dodać formantu NamedRange do arkusza, korzystając z przybornika  
  
1.  Otwórz **przybornika** i kliknij przycisk **formanty Excel** kartę.  
  
2.  Kliknij przycisk <xref:Microsoft.Office.Tools.Excel.NamedRange> i przeciągnij go do arkusza.  
  
     **Dodawanie nazwanego zakresu** zostanie wyświetlone okno dialogowe.  
  
3.  Zaznacz komórkę lub komórki, które chcesz uwzględnić w nazwanego zakresu.  
  
4.  Kliknij przycisk **OK**.  
  
     Jeśli nie chcesz, aby domyślna nazwa znajduje się do formantu, można zmienić nazwę w **właściwości** okna.  
  
#### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-data-sources-window"></a>Aby dodać formantu NamedRange do arkusza w oknie źródeł danych  
  
1.  Otwórz **źródeł danych** okna i Utwórz źródło danych dla projektu. Aby uzyskać więcej informacji, zobacz [dodać nowe połączenia](../data-tools/add-new-connections.md).  
  
2.  Przeciągnij pojedyncze pole z **źródeł danych** okna do arkusza.  
  
     Z danymi <xref:Microsoft.Office.Tools.Excel.NamedRange> formant został dodany do arkusza. Aby uzyskać więcej informacji, zobacz [powiązania danych i formularze systemu Windows](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
##  <a name="runtimedoclevel"></a>Dodawanie formantów NamedRange w czasie wykonywania w projektach na poziomie dokumentu  
 Możesz dodać <xref:Microsoft.Office.Tools.Excel.NamedRange> kontroli programowo do arkusza w czasie wykonywania. Dzięki temu można utworzyć kontrolki hosta w odpowiedzi na zdarzenia. Utworzony dynamicznie nazwane zakresy nie są zachowywane w arkuszu zgodnie z formanty hosta po zamknięciu arkusza. Aby uzyskać więcej informacji, zobacz [dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-namedrange-control-to-a-worksheet-programmatically"></a>Aby programowo dodać formantu NamedRange do arkusza  
  
1.  W <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> obsługi zdarzeń `Sheet1`, Wstaw następujący kod, aby dodać <xref:Microsoft.Office.Tools.Excel.NamedRange> formant w komórce **A1** i ustawić jej <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> właściwości`Hello world!`  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#3)]  
  
##  <a name="runtimeaddin"></a>Dodawanie formantów NamedRange w czasie wykonywania w projekcie dodatku narzędzi VSTO  
 Możesz dodać <xref:Microsoft.Office.Tools.Excel.NamedRange> programowo sterowania wszystkie otwarte arkusza w projekcie dodatku narzędzi VSTO. Utworzony dynamicznie nazwane zakresy nie są zachowywane w arkuszu zgodnie z formanty hosta po zamknięciu arkusza. Aby uzyskać więcej informacji, zobacz [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
#### <a name="to-add-a-namedrange-control-to-a-worksheet-programmatically"></a>Aby programowo dodać formantu NamedRange do arkusza  
  
1.  Poniższy kod wywoła element hosta arkusza, który jest oparty na otwieranie arkusza, a następnie dodanie <xref:Microsoft.Office.Tools.Excel.NamedRange> formant w komórce **A1** i ustawia jej <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> właściwości `Hello world`.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#7](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#7)]
     [!code-vb[Trin_Excel_Dynamic_Controls#7](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#7)]  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)   
 [Namedrange — formant](../vsto/namedrange-control.md)   
 [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)   
 [Obiekty hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md)   
 [Porady: zmiana rozmiaru formantów NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Ograniczenia programowe elementów hosta i formantów hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  