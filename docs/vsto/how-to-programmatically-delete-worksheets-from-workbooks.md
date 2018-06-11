---
title: 'Porady: programowane usuwanie arkuszy ze skoroszytu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, deleting worksheets
- worksheets, deleting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1e937e1ec212ccefb32b62abfc9fa01421343070
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257312"
---
# <a name="how-to-programmatically-delete-worksheets-from-workbooks"></a>Porady: programowane usuwanie arkuszy ze skoroszytu
  Możesz usunąć wszelkie arkusza w skoroszycie. Aby usunąć arkusza, użyj element hosta arkusza lub dostęp do arkusza przy użyciu kolekcji arkuszy skoroszytu.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="use-the-worksheet-host-item"></a>Użyj element hosta arkusza  
 Jeśli arkusz został dodany w czasie projektowania w dostosowaniu poziomie dokumentu, użyj <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> metodę, aby usunąć określony arkusza. Następujący kod usuwa arkusz ze skoroszytu, umieszczając odwołanie do element hosta arkusza bezpośrednio.  
  
> [!IMPORTANT]  
>  Ten kod zadziała tylko w przypadku projektów utworzonych za pomocą dowolnej z następujących szablonów projektu:  
>   
> -   Skoroszyt programu Excel 2013  
> -   Szablon programu Excel 2013  
> -   Skoroszyt programu Excel 2010  
> -   Szablon programu Excel 2010  
>   
>  Jeśli chcesz wykonać tego zadania w żadnym innym typem projektu, należy dodać odwołanie do **Microsoft.Office.Interop.Excel** zestawu, a następnie użyć klasy z tego zestawu Otwórz skoroszyt i usuwanie arkusza. Aby uzyskać więcej informacji, zobacz [porady: aplikacje pakietu Office docelowym za pośrednictwem podstawowe zestawy międzyoperacyjne](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) i [odwołania podstawowego zestawu międzyoperacyjnego programu Excel 2010](http://go.microsoft.com/fwlink/?LinkId=189585).  
  
### <a name="to-delete-a-worksheet-by-using-a-worksheet-host-item"></a>Aby usunąć arkuszu za pomocą element hosta arkusza  
  
1.  Wywołanie <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> metody `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#17](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomation#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#17)]  
  
## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Korzystać z kolekcji arkuszy skoroszytu programu Excel  
 Dostęp do arkuszy za pomocą programu Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Sheets> kolekcji w następujących przypadkach:  
  
-   Chcesz usunąć arkusza w dodatku VSTO.  
  
-   Arkusz, który chcesz usunąć został utworzony w czasie wykonywania w dostosowaniu poziomie dokumentu.  
  
 Poniższy kod usuwa arkusz ze skoroszytu, umieszczając odwołanie do arkusza za pośrednictwem numer indeksu **arkusze** kolekcji. Ten kod zakłada nowego arkusza zostało utworzone programowo.  
  
> [!IMPORTANT]  
>  Jeśli chcesz wykonać tego zadania w żadnym innym typem projektu, należy dodać odwołanie do **Microsoft.Office.Interop.Excel** zestawu, a następnie użyć klasy z tego zestawu Otwórz skoroszyt i usuwanie arkusza. Aby uzyskać więcej informacji, zobacz [porady: aplikacje pakietu Office docelowym za pośrednictwem podstawowe zestawy międzyoperacyjne](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) i [odwołania podstawowego zestawu międzyoperacyjnego programu Excel 2010](http://go.microsoft.com/fwlink/?LinkId=189585).  
  
### <a name="to-delete-a-worksheet-by-using-the-sheets-collection-of-the-excel-workbook"></a>Aby usunąć arkuszu za pomocą kolekcji arkuszy skoroszytu programu Excel  
  
1.  Wywołanie <xref:Microsoft.Office.Interop.Excel._Worksheet.Delete%2A> metody <xref:Microsoft.Office.Interop.Excel.Sheets> kolekcji.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#18](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomation#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#18)]  
  
## <a name="see-also"></a>Zobacz także  
 [Praca z arkuszami](../vsto/working-with-worksheets.md)   
 [Porady: programowane ukrywanie arkuszy](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Porady: programowane przenoszenie arkuszy w obrębie skoroszytu](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [Porady: programowane Zaznaczanie arkuszy](../vsto/how-to-programmatically-select-worksheets.md)   
 [Porady: programowane Dodawanie nowych arkuszy ze skoroszytami](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Element hosta arkusza](../vsto/worksheet-host-item.md)   
 [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Ograniczenia programowe elementów hosta i formantów hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  