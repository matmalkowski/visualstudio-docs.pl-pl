---
title: "Porady: programowane odwoływanie do zakresów arkusza w kodzie | Dokumentacja firmy Microsoft"
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
- ranges, referring to
- worksheets, referring to ranges
- referring to worksheet ranges
- Excel [Office development in Visual Studio], referring to worksheet ranges
ms.assetid: 113633b8-426a-4d02-b6b8-d459d1f110ea
caps.latest.revision: "46"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 829cd94dc97d91afc9f3f991d088627ac9e1ccdc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-refer-to-worksheet-ranges-in-code"></a>Porady: Programowane odwoływanie do zakresów arkusza w kodzie
  Podobnej procedurze jest używana do odwoływania się do zawartości <xref:Microsoft.Office.Tools.Excel.NamedRange> formant lub obiekt zakresu natywnego programu Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="using-a-namedrange-control"></a>Używanie formantu NamedRange  
 Poniższy przykład umożliwia dodanie <xref:Microsoft.Office.Tools.Excel.NamedRange> w arkuszu, a następnie dodaje tekst do komórki w zakresie.  
  
#### <a name="to-refer-to-a-namedrange-control"></a>Aby odwołać się do formantu NamedRange  
  
1.  Ciąg, aby przypisać <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> właściwość <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu. Ten kod muszą znajdować się w klasie arkusza nie znajduje się w `ThisWorkbook` klasy.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#46)]
     [!code-vb[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#46)]  
  
## <a name="using-native-excel-ranges"></a>Za pomocą natywnego zakresów programu Excel  
 Poniższy przykład dodaje natywny zakresu programu Excel do arkusza, a następnie dodaje tekst do komórki w zakresie.  
  
#### <a name="to-refer-to-a-native-range-object"></a>Aby odwołać się do obiektu zakresu natywnego  
  
1.  Ciąg, aby przypisać <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> właściwości zakresu.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#47)]
     [!code-vb[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#47)]  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z zakresami](../vsto/working-with-ranges.md)   
 [Porady: programowane sprawdzanie pisowni w arkuszach](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)   
 [Porady: programowane stosowanie stylów do zakresów arkusza w skoroszycie](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Porady: programowane automatyczne wypełnianie zakresów przyrostowo zmieniającymi się danymi](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [Porady: programowane wyszukiwanie tekstu w zakresach arkusza](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)   
 [Namedrange — formant](../vsto/namedrange-control.md)   
 [Obiekty hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md)   
 [Ograniczenia programowe elementów hosta i formantów hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parametry opcjonalne w rozwiązaniach Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  