---
title: 'Porady: programowane automatyczne wypełnianie zakresów przyrostowo zmieniającymi się danymi | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Autofill method [Excel]
- filling ranges automatically
- ranges, automatically filling
- workbooks, filling ranges
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e358869dea101d0c0ca012acd46b7822e6cf5873
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data"></a>Porady: Programowane automatyczne wypełnianie zakresów przyrostowo zmieniającymi się danymi
  <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> Metody <xref:Microsoft.Office.Interop.Excel.Range> obiektu umożliwia automatyczne wypełnianie zakresu w arkuszu wartościami. W większości przypadków <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> metoda jest używana do przechowywania przyrostowo zwiększenie lub zmniejszenie wartości w zakresie. Można określić zachowanie, podając opcjonalne stałej z <xref:Microsoft.Office.Interop.Excel.XlAutoFillType> wyliczenia.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Należy określić dwa zakresy przy użyciu <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>:  
  
-   Zakres, który wywołuje <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> metodę, która określa punkt początkowy wypełnienia i zawiera wartość początkową.  
  
-   Zakres, który chcesz wypełnić, przekazany jako parametr <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> metody. Ten zakres docelowy musi zawierać zakres zawierający wartość początkowa.  
  
    > [!NOTE]  
    >  Nie można przekazać <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolować zamiast <xref:Microsoft.Office.Interop.Excel.Range>. Aby uzyskać więcej informacji, zobacz [programowe ograniczenia elementów hosta i formantów hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#49)]
 [!code-vb[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#49)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Pierwszą komórkę zakresu, który chcesz wypełnić musi zawierać wartość początkową.  
  
 Przykład wymaga, konieczne jest wypełnienie trzech obszarach:  
  
-   Kolumna B jest uwzględnienie pięć dni tygodnia. Jako wartości początkowej typu **poniedziałek** w komórce B1.  
  
-   Kolumna C jest uwzględnienie pięciu miesięcy. Jako wartości początkowej typu **stycznia** w komórce C1.  
  
-   Kolumna D jest uwzględnienie seria liczb, wartości przez dwa dla każdego wiersza. W przypadku wartości początkowej typu **4** w komórce D1 i **6** w komórce D2.  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z zakresami](../vsto/working-with-ranges.md)   
 [Porady: programowane odwoływanie do zakresów arkusza w kodzie](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Porady: programowane stosowanie stylów do zakresów arkusza w skoroszycie](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Porady: programowane wykonywanie obliczeń programu Excel](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)   
 [Obiekty hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md)   
 [Parametry opcjonalne w rozwiązaniach Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  