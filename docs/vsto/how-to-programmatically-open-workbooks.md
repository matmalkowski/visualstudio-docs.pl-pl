---
title: "Porady: programowane otwieranie skoroszytów | Dokumentacja firmy Microsoft"
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
- workbooks, opening
- Excel [Office development in Visual Studio], opening workbooks
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 11fe801cf80c15953056f4f6fdd50c5c4fadd3c9
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-open-workbooks"></a>Porady: Programowane otwieranie skoroszytów
  <xref:Microsoft.Office.Interop.Excel.Workbooks> Kolekcji w programie Microsoft Office Excel umożliwia pracę z wszystkich otwartych skoroszytów i otwieranie skoroszytów.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-open-an-existing-workbook"></a>Aby otworzyć istniejącego skoroszytu  
  
1.  Użyj <xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A> metody <xref:Microsoft.Office.Interop.Excel.Workbooks> kolekcji, przekazując ścieżkę do skoroszytu.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#2)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 W tym przykładzie kodu wymaga następujących elementów:  
  
-   Skoroszyt o nazwie `YourWorkbook.xls` musi istnieć w katalogu o nazwie `Test` na dysku C.  
  
## <a name="see-also"></a>Zobacz też  
 [Praca ze skoroszytami](../vsto/working-with-workbooks.md)   
 [Porady: programowane otwieranie plików tekstowych jako skoroszytu](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)   
 [Porady: programowane tworzenie nowych skoroszytów](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [Porady: programowane zapisywanie skoroszytów](../vsto/how-to-programmatically-save-workbooks.md)   
 [Porady: programowane zamykanie skoroszytów](../vsto/how-to-programmatically-close-workbooks.md)   
 [Ograniczenia programowe elementów hosta i formantów hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Przegląd obiektów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)  
  
  