---
title: Formant wykresu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VST.ProjectItem.ExcelChart
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], events
- Chart control [Office development in Visual Studio]
- Chart control [Office development in Visual Studio], data binding
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 9acd6d07a44ce853bcf7330d16585e1231640d48
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="chart-control"></a>Formant wykresu
  <xref:Microsoft.Office.Tools.Excel.Chart> Kontroli jest obiektem wykresu, który opisuje zdarzenia. Po dodaniu wykresu w arkuszu programu Visual Studio tworzy <xref:Microsoft.Office.Tools.Excel.Chart> obiekt można umieszczonych przed bezpośrednio, bez konieczności przechodzenia modelu obiektu programu Microsoft Office Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="creating-the-control"></a>Tworzenie formantu  
 Możesz dodać <xref:Microsoft.Office.Tools.Excel.Chart> formantów do arkusza w czasie projektowania lub w czasie wykonywania w projektach na poziomie dokumentu programu Microsoft Office Excel.  
  
 Możesz dodać <xref:Microsoft.Office.Tools.Excel.Chart> formantów do arkusza w czasie wykonywania w dodatku VSTO. Aby uzyskać więcej informacji, zobacz [porady: dodawanie formantów wykresu do arkuszy](../vsto/how-to-add-chart-controls-to-worksheets.md).  
  
> [!NOTE]  
>  Wykres utworzony dynamicznie obiektów nie są zachowywane w arkuszu zgodnie z formanty hosta po zamknięciu arkusza. Aby uzyskać więcej informacji, zobacz [dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
## <a name="formatting"></a>Formatowanie  
 Wszelkie formatowanie, który można zastosować do <xref:Microsoft.Office.Interop.Excel.Chart> również będą stosowane do <xref:Microsoft.Office.Tools.Excel.Chart> formantu. W tym obramowania, czcionki, typ wykresu, linie siatki, legendy i etykiety danych.  
  
## <a name="events"></a>Zdarzenia  
 Następujące zdarzenia są dostępne dla <xref:Microsoft.Office.Tools.Excel.Chart> sterowania:  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.ActivateEvent>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.Calculate>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.Deactivate>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.DragOver>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.DragPlot>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.MouseDown>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.MouseMove>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.MouseUp>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.Resize>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.SelectEvent>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.SeriesChange>  
  
## <a name="see-also"></a>Zobacz też  
 [Office Development ― przykłady i wskazówki](../vsto/office-development-samples-and-walkthroughs.md)   
 [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)   
 [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)   
 [Porady: dodawanie formantów wykresu do arkuszy](../vsto/how-to-add-chart-controls-to-worksheets.md)   
 [Wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  