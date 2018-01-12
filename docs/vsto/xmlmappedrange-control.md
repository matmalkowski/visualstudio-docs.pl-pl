---
title: "Xmlmappedrange — formant | Dokumentacja firmy Microsoft"
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
- XMLMappedRange control, data binding
- XMLMappedRange control
- XMLMappedRange control, events
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: f4b78da11efafff45f34b3dc4ab9e7f1349a2e8a
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="xmlmappedrange-control"></a>XmlMappedRange — Formant
  <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Formant jest zakres, który jest tworzony tylko wtedy, gdy element schematu niepowtarzającymi jest zamapowane do komórki w programie Microsoft Office Excel. Na przykład, jeśli `maxOccurs` atrybut elementu schematu jest równa 1. Po Visual Studio tworzy zakres XML zamapowane, można program na nim bezpośrednio, bez konieczności przechodzenia modelu obiektów programu Excel. Można usunąć tylko <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> kontroli w ramach programu Excel po usunięciu mapowania elementu.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 ![łącze do wideo](../vsto/media/playvideo.gif "łącze do wideo") dla powiązanych pokaz wideo, zobacz [jak czy I: Użyj XML mapowanie w programie Excel?](http://go.microsoft.com/fwlink/?LinkID=130288).  
  
## <a name="binding-data-to-the-control"></a>Wiązanie danych do kontrolki  
 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Sterowanie obsługuje powiązanie danych jednego pola (proste powiązanie danych). <xref:Microsoft.Office.Tools.Excel.ListObject> Formant może obsługuje złożone powiązanie danych i jest tworzone automatycznie, gdy powtarzający się element schematu jest mapowany na komórkę. Aby uzyskać więcej informacji, zobacz [ListObject — formant](../vsto/listobject-control.md).  
  
 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Formantu są powiązane z źródła danych przy użyciu <xref:System.Windows.Forms.Control.DataBindings%2A> właściwości. Gdy <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> jest dodawany do komórki arkusza programu Visual Studio automatycznie generuje zestaw danych z danych w komórkach mapowane, a powiąże go z tego zestawu danych. Domyślna właściwość powiązania danych z <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> jest <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A>.  
  
 Jeśli dane w zestawie danych powiązane są aktualizowane przy użyciu dowolnego mechanizmu <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> kontroli odzwierciedla zmiany.  
  
## <a name="formatting"></a>Formatowanie  
 Można zastosować to samo formatowanie <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> formant, który można zastosować do <xref:Microsoft.Office.Interop.Excel.Range>. W tym obramowania, czcionki, format liczbowy i style.  
  
## <a name="events"></a>Zdarzenia  
 Dostępne dla zdarzeń <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> formantu są:  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Change>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Selected>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Deselected>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.SelectionChange>  
  
## <a name="see-also"></a>Zobacz też  
 [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)   
 [Porady: dodawanie formantów XMLMappedRange do arkuszy](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)   
 [Wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Porady: mapowanie schematów z arkuszami w programie Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  