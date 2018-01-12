---
title: "Porady: programowane listy ostatnio używanych plików skoroszytu | Dokumentacja firmy Microsoft"
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
- workbooks, listing recently used
- RecentFiles property
- Excel [Office development in Visual Studio], recently used files listing
- recent file list, Excel
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: e8a64f8a934e8cd7cdbbed11a87d15e795d19d0f
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-list-recently-used-workbook-files"></a>Porady: Programowane wyświetlanie listy niedawno używanych plików skoroszytu
  <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A> Właściwość zwraca kolekcję zawierającą nazwy wszystkich plików, które znajdują się na liście programu Microsoft Office Excel ostatnio używanych plików. Długość listy może być różna w zależności od liczby plików, które użytkownik wybrał opcję zachowania. Można wyświetlić wyniki w zakresie.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-list-recently-used-workbooks-in-a-range-object"></a>Skoroszyty listy ostatnio używanych w obiekcie range  
  
1.  Pętli listy ostatnio używanych plików i wyświetlić nazwy w komórkach względem <xref:Microsoft.Office.Interop.Excel.Range> obiektu.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#9)]  
  
## <a name="see-also"></a>Zobacz też  
 [Praca ze skoroszytami](../vsto/working-with-workbooks.md)   
 [Namedrange — formant](../vsto/namedrange-control.md)   
 [Parametry opcjonalne w rozwiązaniach Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  