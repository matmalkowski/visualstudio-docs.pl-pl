---
title: Namedrange — formant | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.Toolbox.Range
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, named
- NamedRange control, events
- NamedRange control, data binding
- NamedRange control
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7ea0b0f59731f711dc32258aea31358626825f5d
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34573092"
---
# <a name="namedrange-control"></a>NamedRange — formant
  <xref:Microsoft.Office.Tools.Excel.NamedRange> Kontroli jest zakresem, który ma unikatową nazwę, opisuje zdarzenia i może być powiązany z danymi. Aby uzyskać więcej informacji, zobacz [model obiektu Excel ― omówienie](../vsto/excel-object-model-overview.md).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="create-the-control"></a>Tworzenie formantu  
 Możesz dodać <xref:Microsoft.Office.Tools.Excel.NamedRange> formantów do arkusza w czasie projektowania lub w czasie wykonywania w projektach na poziomie dokumentu programu Microsoft Office Excel.  
  
 Możesz dodać <xref:Microsoft.Office.Tools.Excel.NamedRange> formantów do arkusza w czasie wykonywania w dodatku VSTO. Aby uzyskać więcej informacji, zobacz [porady: formanty dodać NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md).  
  
> [!NOTE]  
>  Domyślnie utworzony dynamicznie nazwane zakresy nie są zachowywane w arkuszu zgodnie z formanty hosta po zamknięciu arkusza. Aby uzyskać więcej informacji, zobacz [dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 <xref:Microsoft.Office.Tools.Excel.NamedRange> Formanty może zawierać tylko zakresów określonych arkuszy. <xref:Microsoft.Office.Tools.Excel.NamedRange> formanty nie może mieć nazwy względne, które są stosowane do wszystkich arkuszy, a nie składają się z zakresów, obejmującej dwa lub więcej arkuszy w skoroszycie (zakresy 3-).  
  
## <a name="bind-data-to-the-control"></a>Wiązanie danych do kontrolki  
 Nazwany zakres wydają się być odpowiednimi kandydatami do złożonych danych powiązania, ponieważ może mieć wiele komórek. jednak zakres jest tylko Kolekcja komórek, których nie można łatwo można zamapować do określonej kolumny z zestawu danych. W związku z tym <xref:Microsoft.Office.Tools.Excel.NamedRange> formanty obsługują tylko proste powiązanie danych. <xref:Microsoft.Office.Tools.Excel.ListObject> Formantu można używać dla złożone powiązanie danych. Aby uzyskać więcej informacji, zobacz [ListObject — formant](../vsto/listobject-control.md).  
  
 <xref:Microsoft.Office.Tools.Excel.NamedRange> Formantu można powiązać źródła danych przy użyciu <xref:System.Windows.Forms.Control.DataBindings%2A> właściwości. Domyślna właściwość powiązania danych z <xref:Microsoft.Office.Tools.Excel.NamedRange> formant jest <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A>.  
  
 Jeśli dane w zestawie danych powiązane są aktualizowane przy użyciu dowolnego mechanizmu <xref:Microsoft.Office.Tools.Excel.NamedRange> kontroli odzwierciedla zmiany.  
  
## <a name="formatting"></a>Formatowanie  
 Formatowanie, które mogą być stosowane do <xref:Microsoft.Office.Interop.Excel.Range> można zastosować do <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu. W tym obramowania, czcionki i formatu liczbowego style.  
  
## <a name="rename-the-control"></a>Nazwy formantu  
 Po dodaniu <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu do arkusza z **przybornika**, Visual Studio automatycznie generuje nazwę dla formantu. Można zmienić nazwę w **właściwości** okna.  
  
## <a name="events"></a>Zdarzenia  
 Następujące zdarzenia są dostępne dla <xref:Microsoft.Office.Tools.Excel.NamedRange> sterowania:  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.Change>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.Deselected>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.Selected>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange>  
  
## <a name="see-also"></a>Zobacz także  
 [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)   
 [Office development ― przykłady i wskazówki](../vsto/office-development-samples-and-walkthroughs.md)   
 [Wiązanie danych do formantów w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)   
 [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Porady: dodawanie formantów NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Porady: zmiana rozmiaru formantów NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Wiązanie danych do formantów w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Wskazówki: Program w odniesieniu do zdarzeń formantu NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [Ograniczenia programowe elementów hosta i formantów hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  