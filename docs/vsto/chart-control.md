---
title: Formant wykresu
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.ExcelChart
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], events
- Chart control [Office development in Visual Studio]
- Chart control [Office development in Visual Studio], data binding
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b1adf0d961489b09a9dc01775148636e6d2d231a
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34267733"
---
# <a name="chart-control"></a>Formant wykresu
  <xref:Microsoft.Office.Tools.Excel.Chart> Kontroli jest obiektem wykresu, który opisuje zdarzenia. Po dodaniu wykresu w arkuszu programu Visual Studio tworzy <xref:Microsoft.Office.Tools.Excel.Chart> obiekt można umieszczonych przed bezpośrednio, bez konieczności przechodzenia modelu obiektu programu Microsoft Office Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="create-the-control"></a>Tworzenie formantu  
 Możesz dodać <xref:Microsoft.Office.Tools.Excel.Chart> formantów do arkusza w czasie projektowania lub w czasie wykonywania w projektach na poziomie dokumentu programu Microsoft Office Excel.  
  
 Możesz dodać <xref:Microsoft.Office.Tools.Excel.Chart> formantów do arkusza w czasie wykonywania w dodatku VSTO. Aby uzyskać więcej informacji, zobacz [porady: formanty dodawania wykresu do arkuszy](../vsto/how-to-add-chart-controls-to-worksheets.md).  
  
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
  
## <a name="see-also"></a>Zobacz także  
 [Office development ― przykłady i wskazówki](../vsto/office-development-samples-and-walkthroughs.md)   
 [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)   
 [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)   
 [Porady: dodawanie formantów wykresu do arkuszy](../vsto/how-to-add-chart-controls-to-worksheets.md)   
 [Wiązanie danych do formantów w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Ograniczenia programowe elementów hosta i formantów hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  