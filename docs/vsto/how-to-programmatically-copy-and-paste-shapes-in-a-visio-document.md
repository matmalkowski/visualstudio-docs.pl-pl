---
title: 'Porady: programowane kopiowanie i wklejanie kształtów w dokumencie programu Visio | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- shapes [Office development in Visual Studio], copying and pasting Visio shapes
- Visio [Office development in Visual Studio], copying and pasting Visio shapes
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 488cda5519a211754498b50a88995de64a8ed366
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-copy-and-paste-shapes-in-a-visio-document"></a>Porady: Programowane kopiowanie i wklejanie kształtów w dokumencie programu Visio
  Można programowo kształtów na jednej stronie dokumentu skopiować i wkleić je do nowej strony, w tym samym dokumencie. Można wkleić je do domyślnej lokalizacji (center aktywne okno) lub te same lokalizacje współrzędnych jak miało na stronie oryginalnej.  
  
## <a name="copying-and-pasting-shapes"></a>Kopiowanie i wklejanie kształtów  
 Aby uzyskać szczegółowe informacje o modelu obiektów, zobacz dokumentację odwołania VBA dla [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](https://msdn.microsoft.com/library/office/ff765757.aspx), [Microsoft.Office.Interop.Visio.Shape.DrawOval](https://msdn.microsoft.com/library/office/ff767121.aspx), [ Microsoft.Office.Interop.Visio.Shape.Copy](https://msdn.microsoft.com/library/office/ff765638.aspx), i [Microsoft.Office.Interop.Visio.Shape.Paste](https://msdn.microsoft.com/library/office/ff768361.aspx) metod i [ Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNormal](https://msdn.microsoft.com/library/office/ff765187.aspx) flagi.  
  
#### <a name="to-copy-shapes-to-the-center-of-another-page"></a>Aby skopiować kształty do Centrum innej strony  
  
-   W poniższym przykładzie pokazano sposób kopiowania kształty z pierwszej strony i wklej je do Centrum drugiej strony.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#14)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#14)]  
  
## <a name="copying-and-pasting-shapes-with-the-same-positions"></a>Kopiowanie i wklejanie kształtów do tej samej pozycji  
 Aby uzyskać szczegółowe informacje o modelu obiektów, zobacz dokumentację odwołania VBA dla [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](https://msdn.microsoft.com/library/office/ff765757.aspx), [Microsoft.Office.Interop.Visio.Shape.DrawOval](https://msdn.microsoft.com/library/office/ff767121.aspx), [ Microsoft.Office.Interop.Visio.Shape.Copy](https://msdn.microsoft.com/library/office/ff765638.aspx), i [Microsoft.Office.Interop.Visio.Shape.Paste](https://msdn.microsoft.com/library/office/ff768361.aspx) metod i [ Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNoTranslate](https://msdn.microsoft.com/library/office/ff765187.aspx) flagi.  
  
 Jeśli chcesz kontrolować format informacji wklejonych i (opcjonalnie) ustanawiania łącza do pliku źródłowego (na przykład dokument programu Microsoft Word pakietu Office), należy użyć metody PasteSpecial.  
  
#### <a name="to-copy-shapes-and-shape-locations-to-another-page"></a>Aby skopiować kształty i lokalizacje kształtu do innej strony  
  
-   W poniższym przykładzie pokazano sposób kopiowania kształty z pierwszej strony i wklej je do drugiej stronie z ich oryginalnych lokalizacji współrzędnych.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#15)]  
  
## <a name="see-also"></a>Zobacz też  
 [Rozwiązania programu Visio](../vsto/visio-solutions.md)   
 [Model obiektu Visio ― omówienie](../vsto/visio-object-model-overview.md)   
 [Praca z kształtów Visio](../vsto/working-with-visio-shapes.md)   
 [Instrukcje: Programowe dodawanie kształtów do dokumentu programu Visio](../vsto/how-to-programmatically-add-shapes-to-a-visio-document.md)  
  
  