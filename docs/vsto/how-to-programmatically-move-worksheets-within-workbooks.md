---
title: 'Porady: programowane przenoszenie arkuszy w obrębie skoroszytu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, moving
- workbooks, moving worksheets in
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 45bc375a65ebc8519ec3127f67e2f31659738f33
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257803"
---
# <a name="how-to-programmatically-move-worksheets-within-workbooks"></a>Porady: programowane przenoszenie arkuszy w obrębie skoroszytu
  Programowo, można zmienić położenie arkuszy względem innych arkuszy w skoroszycie. Jeśli nie określisz lokalizacji dla przeniesionego arkusza programu Excel tworzy nowy skoroszyt, które zawierałoby proces.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="to-move-a-worksheet-in-a-document-level-customization"></a>Aby przenieść arkusza w dostosowaniu poziomie dokumentu  
  
1.  Przypisz łączna liczba arkuszy w skoroszycie do zmiennej, a następnie przenieść pierwszego arkusza tak, aby stał się ostatnio.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#24](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomation#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#24)]  
  
## <a name="to-move-a-worksheet-in-an-vsto-add-in"></a>Aby przenieść arkusza w dodatku VSTO  
  
1.  Przypisz łączna liczba arkuszy w skoroszycie do zmiennej, a następnie przenieść pierwszego arkusza tak, aby stał się ostatnio.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#16](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#16](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#16)]  
  
## <a name="see-also"></a>Zobacz także  
 [Praca z arkuszami](../vsto/working-with-worksheets.md)   
 [Porady: programowane ukrywanie arkuszy](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Porady: programowane usuwanie arkuszy ze skoroszytu](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Porady: programowane Włączanie ochrony arkuszy](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)  
  
  