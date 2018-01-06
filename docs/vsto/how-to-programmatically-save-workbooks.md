---
title: "Porady: programowane zapisywanie skoroszytów | Dokumentacja firmy Microsoft"
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
- workbooks, saving in XML format
- workbooks, saving
- workbooks, saving backup copies
ms.assetid: 991ccf9b-5213-4094-9030-284ec167bdcc
caps.latest.revision: "50"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: d0aa6421893c9d930f917e98fb8aa85b6ceb28d0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-save-workbooks"></a>Porady: Programowane zapisywanie skoroszytów
  Istnieje kilka sposobów, aby zapisać skoroszyt. Skoroszyt programu bez zmiany ścieżki. Jeśli przed nie zapisano skoroszyt, należy zapisać skoroszyt, określając ścieżkę. Bez jawnego ścieżki program Microsoft Office Excel zapisuje plik w bieżącym folderze o nazwie, które podano podczas jej tworzenia. Można także zapisać kopię skoroszytu bez modyfikowania Otwórz skoroszyt w pamięci.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="saving-a-workbook-without-changing-the-path"></a>Zapisywanie skoroszytu bez zmiany ścieżki  
  
#### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Aby zapisać skoroszyt, skojarzone z dostosowywania poziomie dokumentu  
  
1.  Wywołanie <xref:Microsoft.Office.Tools.Excel.Workbook.Save%2A> metody klasy ThisWorkbook.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#4](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomation#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#4)]  
  
#### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Aby zapisać aktywnym skoroszycie w dodatku VSTO  
  
1.  Wywołanie <xref:Microsoft.Office.Interop.Excel._Workbook.Save%2A> metodę, aby zapisać aktywnym skoroszycie. Aby użyć w poniższym przykładzie kodu, uruchom go `ThisAddIn` klasy w projekcie dodatku narzędzi VSTO dla programu Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#3)]  
  
## <a name="saving-a-workbook-with-a-new-path"></a>Zapisywanie skoroszytu z nową ścieżkę  
 Możesz zapisać skoroszyt określony do nowej lokalizacji lub pod nową nazwą, opcjonalnie określając format pliku, hasła, tryb dostępu i.  
  
> [!NOTE]  
>  Należy ustawić <xref:Microsoft.Office.Interop.Excel._Application.DisplayAlerts%2A> właściwości **False** przed zapisanie skoroszytu z nową ścieżkę, ponieważ zapisanie w niektóre formaty wymaga interakcji. Ustawienie tej właściwości na **False** powoduje, że użyć wszystkich wartości domyślnych.  
  
#### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Aby zapisać skoroszyt, skojarzone z dostosowywania poziomie dokumentu  
  
1.  Wywołanie <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> metody `ThisWorkbook` klasy. Aby użyć w poniższym przykładzie kodu, uruchom go `ThisWorkbook` klasy.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#5)]  
  
#### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Aby zapisać aktywnym skoroszycie w dodatku VSTO  
  
1.  Wywołanie <xref:Microsoft.Office.Interop.Excel._Workbook.SaveAs%2A> metody, aby zapisać nową ścieżkę aktywnym skoroszycie. Aby użyć w poniższym przykładzie kodu, uruchom go `ThisAddIn` klasy w projekcie dodatku narzędzi VSTO dla programu Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#4)]  
  
## <a name="saving-a-copy-of-the-workbook"></a>Zapisywanie kopię skoroszytu  
 Można zapisać kopię skoroszytu do pliku bez modyfikowania Otwórz skoroszyt w pamięci. Jest to przydatne, gdy chcesz utworzyć kopię zapasową bez modyfikowania lokalizacji skoroszytu.  
  
#### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Aby zapisać skoroszyt, skojarzone z dostosowywania poziomie dokumentu  
  
1.  Wywołanie <xref:Microsoft.Office.Tools.Excel.Workbook.SaveCopyAs%2A> metody `ThisWorkbook` klasy. Aby użyć w poniższym przykładzie kodu, uruchom go `ThisWorkbook` klasy.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#6)]  
  
#### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Aby zapisać aktywnym skoroszycie w dodatku VSTO  
  
1.  Wywołanie <xref:Microsoft.Office.Interop.Excel._Workbook.SaveCopyAs%2A> metodę, aby zapisać kopię aktywnego skoroszytu. Aby użyć w poniższym przykładzie kodu, uruchom go `ThisAddIn` klasy w projekcie dodatku narzędzi VSTO dla programu Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#5)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Interaktywnie anulowanie dowolnej z metod, które Zapisz lub skopiuj skoroszyt zgłasza błąd w czasie wykonywania w kodzie. Na przykład, jeśli procedura wymaga <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> metoda, ale ma nie Wyłącz monity z programu Excel, a Twoje użytkownik klika polecenie **anulować** po wyświetleniu monitu Excel zgłasza błąd wykonania.  
  
## <a name="see-also"></a>Zobacz też  
 [Praca ze skoroszytami](../vsto/working-with-workbooks.md)   
 [Element hosta skoroszytu](../vsto/workbook-host-item.md)   
 [Porady: programowane zamykanie skoroszytów](../vsto/how-to-programmatically-close-workbooks.md)   
 [Ograniczenia programowe elementów hosta i formantów hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Przegląd obiektów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)  
  
  