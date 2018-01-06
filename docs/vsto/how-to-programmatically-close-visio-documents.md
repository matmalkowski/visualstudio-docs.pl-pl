---
title: "Porady: programowane zamykanie dokumentów programu Visio | Dokumentacja firmy Microsoft"
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
- documents [Office development in Visual Studio], closing Visio documents
- Visio [Office development in Visual Studio], closing Visio documents
ms.assetid: 59c0e215-a4c1-4b39-a491-37534f172705
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: cbb848c07828b8581a71e57fbeee411404632f31
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-close-visio-documents"></a>Porady: Programowane zamykanie dokumentów programu Visio
  Aktywny dokument programu Microsoft Office Visio można zamknąć przy użyciu metody Microsoft.Office.Interop.Visio.Document.Close.  
  
 Szczegółowe informacje na temat tej metody, zobacz dokumentację referencyjną VBA, aby uzyskać [Microsoft.Office.Interop.Visio.Document.Close](http://msdn.microsoft.com/library/office/ff767415.aspx) metody.  
  
## <a name="closing-the-active-document"></a>Zamykanie dokumentów aktywnych  
  
#### <a name="to-close-the-active-document"></a>Aby zamknąć aktywny dokument.  
  
-   Wywołaj metodę Microsoft.Office.Interop.Visio.Document.Close do Zamyka aktywny dokument.  
  
     Aby użyć w poniższym przykładzie kodu, uruchom go `ThisAddIn` klasy w projekcie dodatku narzędzi VSTO dla programu Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#7)]  
  
## <a name="see-also"></a>Zobacz też  
 [Rozwiązania programu Visio](../vsto/visio-solutions.md)   
 [Model obiektu Visio ― omówienie](../vsto/visio-object-model-overview.md)   
 [Porady: programowane tworzenie nowych dokumentów programu Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Porady: programowane otwieranie dokumentów Visio](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Porady: programowane zapisywanie dokumentów Visio](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Instrukcje: Programowe drukowanie dokumentów programu Visio](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  