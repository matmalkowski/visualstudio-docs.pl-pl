---
title: 'Porady: programowane drukowanie dokumentów Visio'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], printing Visio documents
- documents [Office development in Visual Studio], printing Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4caf48d0268e653b7ce6f7a5c8e7efb1e2ec39e6
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257508"
---
# <a name="how-to-programmatically-print-visio-documents"></a>Porady: programowane drukowanie dokumentów Visio
  Można drukować pełną dokumentu Microsoft Office Visio lub określonej strony.  
  
 Aby uzyskać szczegółowe informacje o metodach wydruku, zobacz dokumentację odwołania VBA dla [Microsoft.Office.Interop.Visio.Document.Print](https://msdn.microsoft.com/library/office/ff767996.aspx) — metoda i [Microsoft.Office.Interop.Visio.Page.Print](https://msdn.microsoft.com/library/office/ff765064.aspx) — metoda .  
  
## <a name="print-a-visio-document"></a>Drukowanie dokumentów Visio  
  
### <a name="to-print-a-complete-document"></a>Aby wydrukować dokument ukończone  
  
-   Wywołanie `Microsoft.Office.Interop.Visio.Document.Print` metody `Microsoft.Office.Interop.Visio.Document` obiekt, który chcesz wydrukować.  
  
     Poniższy przykład kodu Drukuje aktywny dokument. Aby użyć tego przykładu, należy uruchomić kod z `ThisAddIn` klasy w projekcie.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#8)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#8)]  
  
## <a name="print-a-page-of-a-visio-document"></a>Wydrukować strony z dokumentu programu Visio  
  
### <a name="to-print-a-page-of-a-document"></a>Aby wydrukować stronę z dokumentu  
  
-   Wywołanie `Microsoft.Office.Interop.Visio.Pages.Print` metody `Microsoft.Office.Interop.Visio.Pages` obiekt, który chcesz wydrukować.  
  
     Poniższy przykład kodu Drukuje aktywny dokument na pierwszej stronie. Aby użyć tego przykładu, należy uruchomić kod z `ThisAddIn` klasy w projekcie.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#9)]  
  
## <a name="see-also"></a>Zobacz także  
 [Rozwiązania programu Visio](../vsto/visio-solutions.md)   
 [Model obiektu Visio ― omówienie](../vsto/visio-object-model-overview.md)   
 [Porady: programowane tworzenie nowych dokumentów programu Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Porady: programowane otwieranie dokumentów Visio](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Porady: programowane zamykanie dokumentów Visio](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Porady: programowane zapisywanie dokumentów Visio](../vsto/how-to-programmatically-save-visio-documents.md)  
  
  