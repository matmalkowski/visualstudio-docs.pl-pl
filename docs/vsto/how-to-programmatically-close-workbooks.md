---
title: 'Porady: programowane zamykanie skoroszytów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, closing
- Excel [Office development in Visual Studio], closing workbooks
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d63c2e3245a49ea7cf8615d485ccaed2eb3031a0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-close-workbooks"></a>Porady: Programowane zamykanie skoroszytów
  Możesz zamknąć aktywnym skoroszycie lub można określić skoroszytu, aby zamknąć.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="closing-the-active-workbook"></a>Zamknięcie aktywnego skoroszytu  
 Istnieją dwie procedury zamknięcia aktywnym skoroszycie: jeden dla Dostosowywanie na poziomie dokumentu i jeden dla dodatków VSTO.  
  
#### <a name="to-close-the-active-workbook-in-a-document-level-customization"></a>Aby zamknąć aktywnym skoroszycie w dostosowaniu poziomie dokumentu  
  
1.  Wywołanie <xref:Microsoft.Office.Tools.Excel.Workbook.Close%2A> metodę, aby zamknąć skoroszytu służącej do dostosowywania. Aby użyć w poniższym przykładzie kodu, uruchom go `Sheet1` klasy w projektach na poziomie dokumentu dla programu Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#3](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#3)]
     [!code-vb[Trin_VstcoreExcelAutomation#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#3)]  
  
#### <a name="to-close-the-active-workbook-in-a-vsto-add-in"></a>Aby zamknąć aktywny skoroszyt w dodatku VSTO  
  
1.  Wywołanie <xref:Microsoft.Office.Interop.Excel._Workbook.Close%2A> metody, aby zamknąć aktywny skoroszyt. Aby użyć w poniższym przykładzie kodu, uruchom go `ThisAddIn` klasy w projekcie dodatku narzędzi VSTO dla programu Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#1](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#1](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#1)]  
  
## <a name="closing-a-workbook-that-you-specify-by-name"></a>Zamykanie skoroszytu, który określisz według nazwy  
 Sposób, w jaki zamknięciu skoroszytu, który jest określany na podstawie nazwy jest taki sam dla dodatków VSTO i dostosowywanie na poziomie dokumentu.  
  
#### <a name="to-close-a-workbook-that-you-specify-by-name"></a>Aby zamknąć skoroszytu, który jest określany na podstawie nazwy  
  
1.  Określ nazwę skoroszytu jako argument <xref:Microsoft.Office.Interop.Excel.Workbooks> kolekcji. Poniższy przykład kodu zakłada, że skoroszytu o nazwie **NewWorkbook** jest otwarty w programie Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#2](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#2](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 [Praca ze skoroszytami](../vsto/working-with-workbooks.md)   
 [Porady: programowane zapisywanie skoroszytów](../vsto/how-to-programmatically-save-workbooks.md)   
 [Porady: programowane otwieranie skoroszytów](../vsto/how-to-programmatically-open-workbooks.md)   
 [Ograniczenia programowe elementów hosta i formantów hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Przegląd obiektów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)  
  
  