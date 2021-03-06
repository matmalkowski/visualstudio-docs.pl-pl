---
title: 'Porady: programowane grupowanie wierszy w arkuszu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, creating groups
- groups, creating in worksheets
- ranges, creating groups
- worksheets, clearing groups
- groups
- groups [Office development in Visual Studio], clearing in worksheets
- worksheets, ungrouping rows and columns
- rows [Office development in Visual Studio], ungrouping
- columns [Office development in Visual Studio], ungrouping
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: aa9624f90a337fb85ba2868b3b5c4f3cb1553ffb
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35258739"
---
# <a name="how-to-programmatically-group-rows-in-a-worksheet"></a>Porady: programowane grupowanie wierszy w arkuszu
  Co najmniej jeden wiersz całego można grupować. Aby utworzyć grupę w arkuszu, należy użyć <xref:Microsoft.Office.Tools.Excel.NamedRange> formant lub obiekt zakresu natywnego programu Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="use-a-namedrange-control"></a>Użyj formantu NamedRange  
 Jeśli dodasz <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrola na poziomie dokumentu projekt w czasie projektowania, umożliwia formantu programowo Utwórz grupę. W poniższym przykładzie założono, że istnieją trzy <xref:Microsoft.Office.Tools.Excel.NamedRange> formantów na tym samym arkuszu: `data2001`, `data2002`, i `dataAll`. Każdy nazwany zakres odwołuje się do całego wiersza w arkuszu.  
  
### <a name="to-create-a-group-of-namedrange-controls-on-a-worksheet"></a>Aby utworzyć grupę formantów NamedRange w arkuszu  
  
1.  Grupa trzech nazwane zakresy przez wywołanie metody <xref:Microsoft.Office.Tools.Excel.NamedRange.Group%2A> metody każdego zakresu. Ten kod muszą znajdować się w klasie arkusza nie znajduje się w `ThisWorkbook` klasy.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#32)]
     [!code-vb[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#32)]  
  
    > [!NOTE]  
    >  Aby Rozgrupowywanie wierszy, należy wywołać <xref:Microsoft.Office.Tools.Excel.NamedRange.Ungroup%2A> metody.  
  
## <a name="use-native-excel-ranges"></a>Użyj natywnego zakresów programu Excel  
 Kod założono, że trzech zakresów programu Excel o nazwie `data2001`, `data2002`, i `dataAll` w arkuszu.  
  
### <a name="to-create-a-group-of-excel-ranges-in-a-worksheet"></a>Aby utworzyć grupę zakresów programu Excel w arkuszu  
  
1.  Grupa trzech nazwane zakresy przez wywołanie metody <xref:Microsoft.Office.Interop.Excel.Range.Group%2A> metody każdego zakresu. W poniższym przykładzie założono, że istnieją trzy <xref:Microsoft.Office.Interop.Excel.Range> formantów `data2001`, `data2002`, i `dataAll` na tym samym arkuszu. Każdy nazwany zakres odwołuje się do całego wiersza w arkuszu.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#33)]
     [!code-vb[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#33)]  
  
    > [!NOTE]  
    >  Aby Rozgrupowywanie wierszy, należy wywołać <xref:Microsoft.Office.Interop.Excel.Range.Ungroup%2A> metody.  
  
## <a name="see-also"></a>Zobacz także  
 [Praca z arkuszami](../vsto/working-with-worksheets.md)   
 [Namedrange — formant](../vsto/namedrange-control.md)   
 [Porady: dodawanie formantów NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  