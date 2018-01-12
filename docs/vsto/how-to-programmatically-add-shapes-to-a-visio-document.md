---
title: "Porady: programowane Dodawanie kształtów do dokumentu programu Visio | Dokumentacja firmy Microsoft"
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
- Visio [Office development in Visual Studio], adding Visio shapes
- shapes [Office development in Visual Studio], adding Visio shapes
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 4d73c59ac9ba89a5814a264bb8e8fe3c83b9789e
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-add-shapes-to-a-visio-document"></a>Porady: Programowane dodawanie kształtów do dokumentu programu Visio
  Pobieranie wzorców z wzornik i upuszczając kształtów na stronie aktywne, można dodać kształtów do dokumentu programu Microsoft Office Visio.  
  
 Aby uzyskać więcej informacji, zobacz dokumentację referencyjną VBA, aby uzyskać [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) metody [Microsoft.Office.Interop.Visio.Application.ActivePage](http://msdn.microsoft.com/library/office/ff765484.aspx) właściwość i [Microsoft.Office.Interop.Visio.Page.Drop](http://msdn.microsoft.com/library/office/ff765054.aspx) metody.  
  
## <a name="adding-shapes-to-a-visio-document"></a>Dodawanie kształtów do dokumentu programu Visio  
  
#### <a name="to-add-shapes-to-a-visio-document"></a>Aby dodać kształtów do dokumentu programu Visio  
  
-   Dla aktywnego dokumentu Pobierz wzorce z kolekcji Documents.Masters i Porzuć kształtów w aktywnym dokumencie. Wzorzec można pobrać za pomocą indeksu lub nazwę wzorca.  
  
     Poniższy przykład kodu tworzy pusty dokument programu Visio, a następnie otwiera je z **kształty podstawowe** wzornika zadokowane. Następnie kod pobiera kilka kształtów i porzuca je na stronie aktywne.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#13)]  
  
## <a name="see-also"></a>Zobacz też  
 [Rozwiązania programu Visio](../vsto/visio-solutions.md)   
 [Model obiektu Visio ― omówienie](../vsto/visio-object-model-overview.md)   
 [Praca z kształtów Visio](../vsto/working-with-visio-shapes.md)   
 [Instrukcje: Programowe kopiowanie i wklejanie kształtów w dokumencie programu Visio](../vsto/how-to-programmatically-copy-and-paste-shapes-in-a-visio-document.md)  
  
  