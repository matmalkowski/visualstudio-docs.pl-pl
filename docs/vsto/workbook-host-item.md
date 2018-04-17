---
title: Element hosta skoroszytu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel workbooks
- Workbook host items
- host items [Office development in Visual Studio], Workbook
- workbooks, Excel
- Workbook host items, events
- workbooks
- Excel [Office development in Visual Studio], workbooks
- workbooks, events
- events [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a5cf1281e084a5ffc51f06b35e3b1c68b2745c43
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="workbook-host-item"></a>Element hosta skoroszytu
  <xref:Microsoft.Office.Tools.Excel.Workbook> Element hosta jest typem, rozszerzający <xref:Microsoft.Office.Interop.Excel.Workbook> typu z podstawowego zestawu międzyoperacyjnego dla programu Excel. <xref:Microsoft.Office.Tools.Excel.Workbook> Element hosta zawiera wszystkie właściwości, metod i zdarzeń jako <xref:Microsoft.Office.Interop.Excel.Workbook> obiekt, ale również zapewnia dodatkowe funkcje.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 W projektach na poziomie dokumentu, jest domyślnie <xref:Microsoft.Office.Tools.Excel.Workbook> element hosta, który reprezentuje skoroszytu w projekcie. W dodatku VSTO projektów, można wygenerować <xref:Microsoft.Office.Tools.Excel.Workbook> hosta elementów w czasie wykonywania.  
  
## <a name="understanding-the-workbook-host-item-in-document-level-projects"></a>Opis element hosta skoroszytu w projektach na poziomie dokumentu  
 Aby uzyskać dostęp do skoroszytu w projekcie, należy użyć `ThisWorkbook` klasy. `ThisWorkbook` Klasy daje dostęp do elementów członkowskich <xref:Microsoft.Office.Tools.Excel.Workbook> element hosta do wykonywania podstawowych zadań w dostosowaniu, takie jak uruchamianie kodu, gdy skoroszyt jest otwarty lub zamknięty. Aby uzyskać więcej informacji, zobacz [programowania dostosowań na poziome dokumentu](../vsto/programming-document-level-customizations.md).  
  
 `ThisWorkbook` Klasa udostępnia lokalizacji, w którym można rozpocząć pisanie kodu w projekcie. Ponieważ klasa zawiera wszystkie właściwości, metod i zdarzeń jako <xref:Microsoft.Office.Interop.Excel.Workbook> obiektu w podstawowego zestawu międzyoperacyjnego dla programu Excel, można również użyć `ThisWorkbook` dostępu do modelu obiektów programu Excel. Aby uzyskać więcej informacji, zobacz [Model obiektu Excel ― omówienie](../vsto/excel-object-model-overview.md).  
  
 Kliknij dwukrotnie **ThisWorkbook** elementu projektu w **Eksploratora rozwiązań** do wyświetlania skoroszytu projektanta i wyświetlić właściwości i zdarzenia skoroszyt w **właściwości**okna.  
  
### <a name="limitations-of-the-workbook-host-item-in-document-level-projects"></a>Ograniczenia element hosta skoroszytu w projektach na poziomie dokumentu  
 Projekt poziomie dokumentu może zawierać tylko jeden <xref:Microsoft.Office.Tools.Excel.Workbook> element hosta (to znaczy `ThisWorkbook` klasy). Nie można dodać nowego <xref:Microsoft.Office.Tools.Excel.Workbook> hosta elementy do projektu w czasie projektowania i nie można utworzyć nowego <xref:Microsoft.Office.Tools.Excel.Workbook> hosta elementów w czasie wykonywania z dostosowywania poziomie dokumentu.  
  
 Jeśli tworzysz nowy skoroszyt programu Excel w czasie wykonywania, będzie typu <xref:Microsoft.Office.Interop.Excel.Workbook>. Ponieważ nie jest elementem hosta, nie może zawierać żadnych kontrolki hosta lub formanty formularzy systemu Windows. Aby uzyskać więcej informacji o tworzeniu skoroszytów w czasie wykonywania, zobacz [porady: programowane tworzenie nowych skoroszytów](../vsto/how-to-programmatically-create-new-workbooks.md).  
  
 <xref:Microsoft.Office.Tools.Excel.Workbook> Element hosta nie działa jako kontener dla kontrolki hosta. Dlatego nie można dodać żadnych widoczne formanty do skoroszytu, ale można dodać składniki, takie jak <xref:System.Data.DataSet>, dzięki czemu składniki mogą być współużytkowane przez wszystkie arkusze. W projekcie poziomie dokumentu, można znaleźć składników dostępnych w skoroszycie w **składnika** karcie **danych** karcie i **wszystkich formularzy systemu Windows** na karcie  **Przybornik**.  
  
> [!NOTE]  
>  Narzędzia Office development w Visual Studio nie obsługują skoroszytów udostępnionych.  
  
## <a name="understanding-workbook-host-items-in-vsto-add-in-projects"></a>Obiekty hosta skoroszytu opis w projektów dodatku VSTO  
 W dodatku VSTO projektów, można wygenerować <xref:Microsoft.Office.Tools.Excel.Workbook> element hosta w czasie wykonywania dla dowolnego skoroszytu, który jest otwarty w programie Excel. Aby wygenerować <xref:Microsoft.Office.Tools.Excel.Workbook> hosta elementu, użyj metody GetVstoObject. Aby uzyskać więcej informacji, zobacz [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Office Development ― przykłady i wskazówki](../vsto/office-development-samples-and-walkthroughs.md)   
 [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Obiekty hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md)   
 [Element hosta arkusza](../vsto/worksheet-host-item.md)   
 [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)   
 [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  