---
title: "Porady: dodawanie formantów wykresu do arkuszy | Dokumentacja firmy Microsoft"
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
- Chart control [Office development in Visual Studio], adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
ms.assetid: f02568e7-5caa-45b4-aa2a-4f73b0565d4e
caps.latest.revision: "44"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 53b30bb62e4c4f4146b1c43b6fe08f9683ba4867
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-chart-controls-to-worksheets"></a>Porady: dodawanie formantów wykresu do arkuszy
  Możesz dodać <xref:Microsoft.Office.Tools.Excel.Chart> formantów do arkusza w czasie projektowania i w czasie wykonywania w dostosowaniach na poziomie dokumentu programu Microsoft Office Excel. Można również dodać <xref:Microsoft.Office.Tools.Excel.Chart> formantów w czasie wykonywania w dodatkach VSTO.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 W tym temacie opisano następujące zadania:  
  
-   [Dodawanie formantów wykresu w czasie projektowania](#designtime)  
  
-   [Dodawanie formantów wykresu w czasie wykonywania w projektach na poziomie dokumentu](#runtimedoclevel)  
  
-   [Dodawanie formantów wykresu w czasie wykonywania w projekcie dodatku narzędzi VSTO](#runtimeaddin)  
  
 Aby uzyskać więcej informacji na temat <xref:Microsoft.Office.Tools.Excel.Chart> formantów, zobacz [formantu wykresu](../vsto/chart-control.md).  
  
##  <a name="designtime"></a>Dodawanie formantów wykresu w czasie projektowania  
 Możesz dodać <xref:Microsoft.Office.Tools.Excel.Chart> formantu do arkusza w taki sam sposób, należy dodać wykres z poziomu aplikacji.  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Excel.Chart> Formant nie jest dostępny z **przybornika** lub **źródeł danych** okna.  
  
#### <a name="to-add-a-chart-host-control-to-a-worksheet-in-excel"></a>Aby dodać kontrolkę hosta wykresu w arkuszu programu Excel  
  
1.  Na **Wstaw** karcie **wykresów** kliknij przycisk **kolumny**, kliknij kategorię wykresy, a następnie kliknij typ wykresu.  
  
2.  W **Wstaw wykres** okno dialogowe, kliknij przycisk **OK**.  
  
3.  Na **projekt** karcie **danych** kliknij przycisk **danych wybierz**.  
  
4.  W **wybierz źródło danych** okno dialogowe, kliknij w **wykresu** **zakres danych** i wyczyść wszystkie wybór domyślny.  
  
5.  W **danych wykresu** arkusza, zaznacz zakres komórek, który zawiera dane wykresu (komórek **A5** za pośrednictwem **D8**).  
  
6.  W **wybierz źródło danych** okno dialogowe, kliknij przycisk **OK**.  
  
##  <a name="runtimedoclevel"></a>Dodawanie formantów wykresu w czasie wykonywania w projektach na poziomie dokumentu  
 Możesz dodać <xref:Microsoft.Office.Tools.Excel.Chart> kontroli dynamicznie w czasie wykonywania. Utworzony dynamicznie wykresów nie są zachowywane w dokumencie jako host Określa, kiedy dokument zostanie zamknięty. Aby uzyskać więcej informacji, zobacz [dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Aby programowo Dodaj formant wykresu do arkusza  
  
1.  W <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> obsługi zdarzeń `Sheet1`, Wstaw następujący kod, aby dodać <xref:Microsoft.Office.Tools.Excel.Chart> formantu.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#1)]  
  
##  <a name="runtimeaddin"></a>Dodawanie formantów wykresu w czasie wykonywania w projekcie dodatku narzędzi VSTO  
 Możesz dodać <xref:Microsoft.Office.Tools.Excel.Chart> programowo sterowania wszystkie otwarte arkusza w projekcie dodatku narzędzi VSTO. Aby uzyskać więcej informacji, zobacz [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
 Kontrolki wykresów utworzony dynamicznie nie są zachowywane w arkuszu zgodnie z formanty hosta po zamknięciu arkusza. Aby uzyskać więcej informacji, zobacz [dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Aby programowo Dodaj formant wykresu do arkusza  
  
1.  Poniższy kod wywoła element hosta arkusza, który jest oparty na otwieranie arkusza, a następnie dodanie <xref:Microsoft.Office.Tools.Excel.Chart> formantu.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#9)]
     [!code-vb[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#9)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 W tym przykładzie ma następujące wymagania:  
  
-   Dane na wykresie, przechowywane w zakresie od A5 do D8 w arkuszu.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)   
 [Formant wykresu](../vsto/chart-control.md)   
 [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)   
 [Obiekty hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md)   
 [Wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  