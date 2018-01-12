---
title: 'Porady: programowane Zaznaczanie arkuszy | Dokumentacja firmy Microsoft'
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
- worksheets, selecting
- Excel projects, selecting worksheets
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: dfd3c56ab51cc0e1d1fb1521640497f4748195cc
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-select-worksheets"></a>Porady: Programowane zaznaczanie arkuszy
  <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> Metody wybiera określony obiekt, który przenosi do nowego obiektu określonego przez użytkownika. Użyj <xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A> metodę, jeśli chcesz przejść do obiektu bez zmiany określonego przez użytkownika.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Jeśli chcesz wybrać istniejący arkusz w dodatku VSTO lub jeśli arkusz został utworzony w czasie wykonywania w dostosowaniu poziomie dokumentu, należy uruchomić je przy użyciu programu Excel <xref:Microsoft.Office.Interop.Excel.Sheets> kolekcji skoroszytu programu Excel; w przeciwnym razie dostęp można uzyskać <xref:Microsoft.Office.Tools.Excel.Worksheet>bezpośrednio element hosta.  
  
## <a name="using-the-worksheet-host-item"></a>Przy użyciu element hosta arkusza  
 W dostosowanie poziomie dokumentu, Dodaj następujący kod, aby **Sheet1.vb** lub **Sheet1.cs**.  
  
#### <a name="to-select-the-first-worksheet-in-a-workbook-using-a-host-item"></a>Aby wybrać pierwszego arkusza w skoroszycie przy użyciu elementu hosta  
  
1.  Wywołanie <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> metody `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#19)]  
  
## <a name="using-the-sheets-collection-of-the-excel-workbook"></a>Przy użyciu kolekcji arkuszy skoroszytu programu Excel  
 Dostęp do arkusza przy użyciu programu Excel <xref:Microsoft.Office.Interop.Excel.Sheets> kolekcji.  
  
#### <a name="to-select-the-first-worksheet-in-a-workbook-using-the-sheets-collection-of-the-excel-workbook"></a>Aby wybrać pierwszego arkusza w skoroszycie przy użyciu kolekcji arkuszy skoroszytu programu Excel  
  
1.  Wywołanie <xref:Microsoft.Office.Interop.Excel.Sheets.Select%2A> metody <xref:Microsoft.Office.Interop.Excel.Sheets> kolekcji do wybrania pierwszego arkusza aktywnym skoroszycie.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#20)]  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z arkuszami](../vsto/working-with-worksheets.md)   
 [Porady: programowane Drukowanie arkuszy](../vsto/how-to-programmatically-print-worksheets.md)   
 [Porady: programowane usuwanie arkuszy ze skoroszytu](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Porady: programowane ukrywanie arkuszy](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Porady: programowane Włączanie ochrony arkuszy](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Element hosta arkusza](../vsto/worksheet-host-item.md)   
 [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Ograniczenia programowe elementów hosta i formantów hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Przegląd obiektów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)  
  
  