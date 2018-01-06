---
title: 'Porady: programowane kopiowanie arkuszy | Dokumentacja firmy Microsoft'
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
- worksheets, copying
- Excel [Office development in Visual Studio], copying worksheets
ms.assetid: e49e03f5-7b2f-416b-b5fe-0965336c47e1
caps.latest.revision: "31"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: f78f4272eb42440c2ddf9ade423ceef9364f75e6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-copy-worksheets"></a>Porady: Programowane kopiowanie arkuszy
  Utwórz kopię arkusza i Wstaw arkusza przed lub po istniejącego arkusza w skoroszycie. Jeśli nie określisz miejsca do wstawienia w arkuszu programu Excel tworzy nowy skoroszyt zawierający nowego arkusza.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
> [!NOTE]  
>  Czy programowane Kopiowanie arkusza lub użytkownik końcowy kopiuje arkusza ręcznie, nie jest wykonywany kod za nowego arkusza i formantów na nowy arkusz nie działają. Jest to spowodowane jest nowo skopiowany arkusza <xref:Microsoft.Office.Interop.Excel.Worksheet> obiektu i nie <xref:Microsoft.Office.Tools.Excel.Worksheet> element hosta. Formanty formularzy systemu Windows i formantów hosta można dodać tylko do elementów hosta. Aby uzyskać więcej informacji, zobacz [programowe ograniczenia elementów hosta i formantów hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
### <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-document-level-customization"></a>Aby dodać arkusz skopiowane do skoroszytu w dostosowaniu poziomie dokumentu  
  
1.  Użyj <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> metodę, aby skopiować pierwszego arkusza w bieżącym skoroszycie i umieścić kopię po trzeci arkusza.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#16](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomation#16](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#16)]  
  
### <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-vsto-add-in"></a>Aby dodać arkusz skopiowane do skoroszytu w dodatku VSTO  
  
1.  Użyj <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> metodę, aby skopiować pierwszego arkusza w bieżącym skoroszycie i umieścić kopię po trzeci arkusza.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#12)]  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z arkuszami](../vsto/working-with-worksheets.md)   
 [Obiekty hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md)   
 [Porady: programowane Dodawanie nowych arkuszy ze skoroszytami](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Porady: programowane usuwanie arkuszy ze skoroszytu](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Porady: programowane Zaznaczanie arkuszy](../vsto/how-to-programmatically-select-worksheets.md)   
 [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)   
 [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Ograniczenia programowe elementów hosta i formantów hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parametry opcjonalne w rozwiązaniach Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  