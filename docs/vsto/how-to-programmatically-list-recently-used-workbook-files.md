---
title: 'Porady: programowane listy ostatnio używanych plików skoroszytu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: d3e909ad3e1509689d953e0ad6c6b8346ff97f91
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257592"
---
# <a name="how-to-programmatically-list-recently-used-workbook-files"></a>Porady: programowane listy ostatnio używanych plików skoroszytu
  <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A> Właściwość zwraca kolekcję zawierającą nazwy wszystkich plików, które znajdują się na liście programu Microsoft Office Excel ostatnio używanych plików. Długość listy może być różna w zależności od liczby plików, które użytkownik wybrał opcję zachowania. Można wyświetlić wyniki w zakresie.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="to-list-recently-used-workbooks-in-a-range-object"></a>Skoroszyty listy ostatnio używanych w obiekcie range  
  
1.  Pętli listy ostatnio używanych plików i wyświetlić nazwy w komórkach względem <xref:Microsoft.Office.Interop.Excel.Range> obiektu.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#9)]  
  
## <a name="see-also"></a>Zobacz także  
 [Praca ze skoroszytami](../vsto/working-with-workbooks.md)   
 [Namedrange — formant](../vsto/namedrange-control.md)   
 [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  