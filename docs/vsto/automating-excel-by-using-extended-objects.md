---
title: Automatyzowanie programu Excel za pomocą obiektów rozszerzonych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], automating
- automation [Office development in Visual Studio], Excel
- host controls, Excel
- Excel [Office development in Visual Studio], host controls
- extended objects [Office development in Visual Studio], Excel
- host controls [Office development in Visual Studio], Excel
- automating Excel
- host items [Office development in Visual Studio], Excel
- controls [Office development in Visual Studio], Excel host controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 63c200a3d3a6a64dfc100cc9365f142a8dddae4c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="automating-excel-by-using-extended-objects"></a>Automatyzowanie programu Excel za pomocą obiektów rozszerzonych
  Podczas opracowywania rozwiązań programu Excel w programie Visual Studio, można użyć *hosta elementów* i *kontrolki hosta*s w ramach rozwiązań. Są to obiekty, które rozszerzają niektórych obiektów często używane w modelu obiektów programu Excel (to znaczy obiektu modelu udostępnianym przez podstawowy zestaw międzyoperacyjny dla programu Excel), takich jak <xref:Microsoft.Office.Interop.Excel.Worksheet> i <xref:Microsoft.Office.Interop.Excel.Range> obiektów. Obiekty rozszerzone przypominają obiektami programu Excel, które są oparte na, ale ich dodać dodatkowe funkcje, takie jak nowe zdarzenia i możliwości wiązania danych do obiektów.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Obiekty hosta i formantów hosta są dostępne w obu dodatku VSTO i poziomie dokumentu dostosowania, mimo że kontekst, w którym mogą być one używane jest różne dla każdego typu rozwiązania. Aby uzyskać więcej informacji, zobacz [elementów hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md).  
  
## <a name="excel-host-items"></a>Obiekty hosta programu Excel  
 Projekty programu Excel umożliwiają dostęp do wielu elementów hosta:  
  
-   <xref:Microsoft.Office.Tools.Excel.Worksheet>. Reprezentuje zawiera ten element hosta arkusza w projekcie. Działa również jako kontener dla zarządzane formanty, łącznie z formantami hosta i formantów formularzy systemu Windows i przechowuje informacje o formantach w jego powierzchnię. Aby uzyskać więcej informacji, zobacz [element hosta arkusza](../vsto/worksheet-host-item.md).  
  
-   <xref:Microsoft.Office.Tools.Excel.Workbook>. Ten element hosta reprezentuje skoroszytu w projekcie i działa jako kontener dla składników, które są udostępniane przez wszystkich arkuszy w skoroszycie. Aby uzyskać więcej informacji, zobacz [element hosta skoroszytu](../vsto/workbook-host-item.md).  
  
-   <xref:Microsoft.Office.Tools.Excel.ChartSheet>. Ten host elementu arkuszu programu Excel, która zawiera tylko wykres i opisuje zdarzenia.  
  
     Po dodaniu wykresu w arkuszu w czasie projektowania, jako nowego arkusza w projekcie dostosowania na poziomie dokumentu programu Microsoft Office Excel Visual Studio automatycznie tworzy <xref:Microsoft.Office.Tools.Excel.ChartSheet> element hosta.  
  
     Mimo że <xref:Microsoft.Office.Tools.Excel.ChartSheet> element hosta ma postać arkusza w programie Excel, nie można dodać wszystkich formantów do arkusza wykresu. Jeśli chcesz, aby inne formanty w arkuszu z wykresem, nie należy używać wykresu w arkuszu. Zamiast tego możesz umieścić wykres jako obiekt osadzony w arkuszu za pomocą <xref:Microsoft.Office.Tools.Excel.Chart> kontrolki hosta. Aby uzyskać więcej informacji, zobacz [formantu wykresu](../vsto/chart-control.md).  
  
## <a name="excel-host-controls"></a>Formanty hosta programu Excel  
 Istnieje kilka hosta formantów dla programu Excel, które ułatwiają tworzenie, organizowanie i automatyzowanie skoroszyty i arkusze. Te kontrolki hosta podaj zdarzenia oraz funkcje wiązania danych, które nie mają ich odpowiedniki w macierzystym modelu obiektów programu Excel.  
  
 Aby uzyskać więcej informacji o formantach hosta można użyć w projekty programu Excel, zobacz następujące tematy:  
  
-   [Kontrolka wykresu](../vsto/chart-control.md)  
  
-   [ListObject, kontrolka](../vsto/listobject-control.md)  
  
-   [NamedRange, kontrolka](../vsto/namedrange-control.md)  
  
-   [XmlMappedRange, kontrolka](../vsto/xmlmappedrange-control.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: wypełnianie formantów ListObject danymi](../vsto/how-to-fill-listobject-controls-with-data.md)   
 [Porady: dodawanie formantów wykresu do arkuszy](../vsto/how-to-add-chart-controls-to-worksheets.md)   
 [Porady: dodawanie formantów ListObject do arkuszy](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [Porady: dodawanie formantów NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Porady: dodawanie formantów XMLMappedRange do arkuszy](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)   
 [Porady: zmiana rozmiaru formantów NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Porady: zmiana rozmiaru formantów ListObject](../vsto/how-to-resize-listobject-controls.md)   
 [Porady: Sprawdzanie poprawności danych po dodaniu nowego rzędu do formantu ListObject](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)   
 [Porady: mapowanie kolumn ListObject do danych](../vsto/how-to-map-listobject-columns-to-data.md)   
 [Wskazówki: Programowanie w odniesieniu do zdarzeń formantu NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)   
 [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Obiekty hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md)   
 [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  