---
title: Element hosta arkusza | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- host items [Office development in Visual Studio], Worksheet
- Excel [Office development in Visual Studio], worksheets
- Worksheet host items
- worksheets, events
- Worksheet host items, events
- Excel worksheets
- worksheets, Excel
- worksheets
- events [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c89fa79a73393afa2919554de790c307b2ea68b5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="worksheet-host-item"></a>Element hosta arkusza
  <xref:Microsoft.Office.Tools.Excel.Worksheet> Element hosta jest typem, rozszerzający <xref:Microsoft.Office.Interop.Excel.Worksheet> typu z podstawowego zestawu międzyoperacyjnego dla programu Excel. <xref:Microsoft.Office.Tools.Excel.Worksheet> Element hosta zawiera wszystkie właściwości, metod i zdarzeń jako <xref:Microsoft.Office.Interop.Excel.Worksheet> obiekt, ale także przedstawia dodatkowe zdarzenia i działa jako kontener dla kontrolki hosta i formantów formularzy systemu Windows.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 W projektach na poziomie dokumentu, można dodać <xref:Microsoft.Office.Tools.Excel.Worksheet> hosta elementy do projektu w czasie projektowania. W dodatku VSTO projektów, można wygenerować <xref:Microsoft.Office.Tools.Excel.Worksheet> hosta elementów w czasie wykonywania.  
  
## <a name="understanding-worksheet-host-items-in-document-level-projects"></a>Opis obiekty hosta arkusza w projektach na poziomie dokumentu  
 Podczas tworzenia projektu poziomie dokumentu dla programu Excel, programu Visual Studio automatycznie tworzy trzy <xref:Microsoft.Office.Tools.Excel.Worksheet> hosta elementów w projekcie. Domyślne nazwy arkuszy są `Sheet1`, `Sheet2`, i `Sheet3`. Jeśli tworzysz projekt oparty na podstawie istniejącego skoroszytu, liczba elementów hosta zależy od liczby arkuszy w skoroszycie.  
  
 Te klasy arkusza uzyskania dostępu do elementów członkowskich <xref:Microsoft.Office.Tools.Excel.Worksheet> element hosta do wykonywania podstawowych zadań w dostosowaniu, takie jak modyfikowanie zawartość arkusza. Te klasy umożliwia także dodawanie formantów do arkuszy. Łącząc różne zestawy formantów i pisanie kodu, formanty można powiązać z danymi, zbiera informacje o użytkowniku i odpowiadania na działania użytkownika. Aby uzyskać więcej informacji, zobacz [programowania dostosowań na poziome dokumentu](../vsto/programming-document-level-customizations.md).  
  
 Klasy arkusza podaj lokalizację, w którym można rozpocząć pisanie kodu w projekcie. Ponieważ klasa zawiera wszystkie właściwości, metod i zdarzeń jako <xref:Microsoft.Office.Interop.Excel.Worksheet> obiektu w podstawowego zestawu międzyoperacyjnego dla programu Excel, można również użyć tych klas dostępu do modelu obiektów programu Excel. Aby uzyskać więcej informacji, zobacz [Model obiektu Excel ― omówienie](../vsto/excel-object-model-overview.md).  
  
 W projektach na poziomie dokumentu, można dodać dodatkowe <xref:Microsoft.Office.Tools.Excel.Worksheet> hosta elementy do projektu w czasie projektowania przez dodanie nowego arkusza w skoroszycie w projektancie.  
  
### <a name="renaming-worksheets"></a>Zmiana nazwy arkuszy  
 W projekcie poziomie dokumentu można zmienić nazwy arkuszy w projektancie programu Visual Studio, ale spowoduje to zmianę tylko nazwa wyświetlana arkusza. Nazwa programowa nadal jest domyślna nazwa arkusza. Jeśli zmienisz nazwę arkusza w **właściwości** okna, programowa nazwa zostanie zmieniona.  
  
### <a name="limitations-of-the-worksheet-host-item-in-document-level-projects"></a>Ograniczenia element hosta arkusza w projektach na poziomie dokumentu  
 Nie można utworzyć nowego <xref:Microsoft.Office.Tools.Excel.Worksheet> hosta elementów w czasie wykonywania w projektach na poziomie dokumentu. Jeśli tworzysz nowy arkusz programu Excel w czasie wykonywania, będzie typu <xref:Microsoft.Office.Interop.Excel.Worksheet>. Ponieważ nie jest elementem hosta, nie może zawierać żadnych kontrolki hosta lub formanty formularzy systemu Windows. Aby uzyskać więcej informacji o tworzeniu dokumentów w czasie wykonywania, zobacz [porady: programowane Dodawanie nowych arkuszy ze skoroszytami](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md).  
  
## <a name="understanding-worksheet-host-items-in-vsto-add-in-projects"></a>Obiekty hosta arkusza opis w projektów dodatku VSTO  
 W projektach na poziomie aplikacji, można wygenerować <xref:Microsoft.Office.Tools.Excel.Worksheet> element hosta w czasie wykonywania żadnych arkusz, który jest otwarty w programie Excel. Można użyć <xref:Microsoft.Office.Tools.Excel.Worksheet> element hosta do dodawania formantów do arkusza skojarzony, lub do obsługi zdarzeń, które nie są dostępne na <xref:Microsoft.Office.Interop.Excel.Worksheet> obiektów.  
  
 Aby wygenerować <xref:Microsoft.Office.Tools.Excel.Worksheet> hosta elementu, użyj metody GetVstoObject. Aby uzyskać więcej informacji, zobacz [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Office Development ― przykłady i wskazówki](../vsto/office-development-samples-and-walkthroughs.md)   
 [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)   
 [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Obiekty hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md)   
 [Element hosta skoroszytu](../vsto/workbook-host-item.md)   
 [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)   
 [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  