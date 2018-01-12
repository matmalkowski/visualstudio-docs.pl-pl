---
title: "Porady: programowane drukowanie dokumentów programu Visio | Dokumentacja firmy Microsoft"
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
- Visio [Office development in Visual Studio], printing Visio documents
- documents [Office development in Visual Studio], printing Visio documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: a2ce41f14758d1f34c3e8c31d2ec013fa24c27b1
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-print-visio-documents"></a>Porady: Programowane drukowanie dokumentów programu Visio
  Można drukować pełną dokumentu Microsoft Office Visio lub określonej strony.  
  
 Aby uzyskać szczegółowe informacje o metodach wydruku, zobacz dokumentację odwołania VBA dla [Microsoft.Office.Interop.Visio.Document.Print](https://msdn.microsoft.com/library/office/ff767996.aspx) — metoda i [Microsoft.Office.Interop.Visio.Page.Print](https://msdn.microsoft.com/library/office/ff765064.aspx) — metoda .  
  
## <a name="printing-a-visio-document"></a>Drukowanie dokumentów Visio  
  
#### <a name="to-print-a-complete-document"></a>Aby wydrukować dokument ukończone  
  
-   Wywołaj metodę Microsoft.Office.Interop.Visio.Document.Print obiektu Microsoft.Office.Interop.Visio.Document, który chcesz wydrukować.  
  
     Poniższy przykład kodu Drukuje aktywny dokument. Aby użyć tego przykładu, należy uruchomić kod z `ThisAddIn` klasy w projekcie.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#8)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#8)]  
  
## <a name="printing-a-page-of-a-visio-document"></a>Drukowanie strony z dokumentu programu Visio  
  
#### <a name="to-print-a-page-of-a-document"></a>Aby wydrukować stronę z dokumentu  
  
-   Wywołaj metodę Microsoft.Office.Interop.Visio.Pages.Print obiektu Microsoft.Office.Interop.Visio.Pages, który chcesz wydrukować.  
  
     Poniższy przykład kodu Drukuje aktywny dokument na pierwszej stronie. Aby użyć tego przykładu, należy uruchomić kod z `ThisAddIn` klasy w projekcie.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#9)]  
  
## <a name="see-also"></a>Zobacz też  
 [Rozwiązania programu Visio](../vsto/visio-solutions.md)   
 [Model obiektu Visio ― omówienie](../vsto/visio-object-model-overview.md)   
 [Porady: programowane tworzenie nowych dokumentów programu Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Porady: programowane otwieranie dokumentów Visio](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Porady: programowane zamykanie dokumentów Visio](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Instrukcje: Programowe zapisywanie dokumentów programu Visio](../vsto/how-to-programmatically-save-visio-documents.md)  
  
  