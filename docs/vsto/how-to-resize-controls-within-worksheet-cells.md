---
title: "Porady: zmiana rozmiaru formantów w komórkach arkusza | Dokumentacja firmy Microsoft"
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
- controls [Office development in Visual Studio], resizing
- managed controls, resizing
- worksheets, resizing
- Windows Forms controls [Office development in Visual Studio], resizing
ms.assetid: 1439db4a-e64b-4381-a6e6-605ba94db3de
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 035021b3a49bd3fb2af2863e3c8a9b2f88c56077
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-resize-controls-within-worksheet-cells"></a>Porady: zmiana rozmiaru formantów w komórkach arkusza
  Podczas zmiany rozmiaru kolumn lub wierszy w arkuszu, wszystkie formanty hosta zawartych w komórkach automatycznie Zmień rozmiar wysokość lub szerokość komórki zmiany rozmiaru. Formanty formularzy systemu Windows nie zmieniać rozmiar automatycznie domyślnie.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Jeśli dodasz formantów w czasie projektowania, należy ustawić pozycjonowanie opcje dla każdego formantu.  
  
 Jeśli programowane Dodawanie formantu formularzy systemu Windows i podać argument zakresu formant automatycznie zmienia rozmiar, gdy zmieniany jest rozmiar komórki znajdującej się w zakresie. Aby uzyskać więcej informacji, zobacz [dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
## <a name="resizing-controls-at-design-time"></a>Zmiana rozmiaru formantów w czasie projektowania  
  
#### <a name="to-make-controls-resize-with-cells-at-design-time"></a>Aby wyświetlić formanty zmiana rozmiaru komórek w czasie projektowania  
  
1.  Z **przybornika**, przeciągnij formant formularzy systemu Windows do arkusza.  
  
2.  Kliknij prawym przyciskiem myszy formantu, a następnie kliknij przycisk **Formatuj formant**.  
  
3.  W **Formatuj formant** okno dialogowe, kliknij przycisk **właściwości** kartę.  
  
4.  W obszarze **Pozycjonowanie obiektu**, wybierz pozycję **Przenieś i rozmiaru z komórek** , a następnie kliknij przycisk **OK**.  
  
     Podczas zmiany rozmiaru komórki, który zawiera formant do rozmiaru komórki zmienia rozmiar formantu.  
  
## <a name="resizing-controls-at-run-time"></a>Zmiana rozmiaru formantów w czasie wykonywania  
 Jeśli dodawanie formantu formularzy systemu Windows w czasie wykonywania i podaj <xref:Microsoft.Office.Interop.Excel.Range> jako lokalizację dla formantu formant będzie automatycznie zmieniać rozmiar gdy zmieniany jest rozmiar komórki arkusza, który zawiera zakres.  
  
#### <a name="to-make-controls-resize-with-cells-at-run-time"></a>Aby wyświetlić formanty zmiana rozmiaru komórek w czasie wykonywania  
  
1.  Dodawanie formantu do zakresu A1.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#5)]  
  
     Podczas zmiany rozmiaru komórki, który zawiera formant do rozmiaru komórki zmienia rozmiar formantu.  
  
## <a name="resetting-control-placement"></a>Resetowanie położenia kontrolki  
 Można przywrócić położenia i rozmiaru formantu przez ustawienie `Placement` jedną z następujących właściwości <xref:Microsoft.Office.Interop.Excel.XlPlacement> wartości:  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMove>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMoveAndSize>  
  
#### <a name="to-change-the-behavior-of-a-control-so-that-it-does-not-resize-or-move-with-the-cell"></a>Aby zmienić zachowanie formantu, aby zmienić rozmiar lub nie są przenoszone wraz z komórki  
  
1.  Właściwości umieszczania formantu wywołania i ustaw wartość <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#6)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#6)]  
  
## <a name="see-also"></a>Zobacz też  
 [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)   
 [Porady: dodawanie formantów do dokumentów pakietu Office formularzy systemu Windows](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Porady: ukrywanie formantów w arkuszu podczas drukowania](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Ograniczenia formantów formularzy systemu Windows w dokumentach pakietu Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  