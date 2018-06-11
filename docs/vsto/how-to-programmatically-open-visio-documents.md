---
title: 'Porady: programowane otwieranie dokumentów Visio'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening Visio documents
- Visio [Office development in Visual Studio], opening Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a3a7d2a9855abef0415661798c8a213eb748e22f
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257855"
---
# <a name="how-to-programmatically-open-visio-documents"></a>Porady: programowane otwieranie dokumentów Visio
  Istnieją dwie metody otwieranie istniejących dokumentów Microsoft Office Visio: otwarte i OpenEx. Metoda OpenEx jest taki sam jak metody Open, ale zawiera argumenty, w których element wywołujący można określić sposób otwierania dokumentu.  
  
 Aby uzyskać szczegółowe informacje o modelu obiektów, zobacz dokumentację odwołania VBA dla [Microsoft.Office.Interop.Visio.Documents.Open](https://msdn.microsoft.com/library/office/ff765240.aspx) — metoda i [Microsoft.Office.Interop.Visio.Documents.OpenEx](https://msdn.microsoft.com/library/office/ff767229.aspx) Metoda.  
  
## <a name="open-a-visio-document"></a>Otwórz dokument programu Visio  
  
### <a name="to-open-a-visio-document"></a>Aby otworzyć dokument programu Visio  
  
-   Wywołanie `Microsoft.Office.Interop.Visio.Documents.Open` — metoda i podaj w pełni kwalifikowaną ścieżkę dokumentu programu Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#5)]  
  
## <a name="open-a-visio-document-with-specified-arguments"></a>Otwórz dokument programu Visio z określonymi argumentami  
  
### <a name="to-open-a-visio-document-as-read-only-and-docked"></a>Aby otworzyć dokument programu Visio jako tylko do odczytu i jest zadokowane  
  
-   Wywołanie `Microsoft.Office.Interop.Visio.Documents.OpenEx` metody, podaj pełną ścieżkę dokumentu programu Visio i zawierać argumenty, którego chcesz użyć — w takim przypadku, zadokowanych i tylko do odczytu.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#6)]  
  
## <a name="compile-the-code"></a>Kompilowanie kodu  
 W tym przykładzie kodu wymaga następujących elementów:  
  
-   Dokument programu Visio o nazwie `myDrawing.vsd` musi znajdować się w katalogu o nazwie `Test` w *Moje dokumenty* folder (dla systemu Windows XP i starszych) lub *dokumenty* folder (dla systemu Windows Vista).  
  
## <a name="see-also"></a>Zobacz także  
 [Rozwiązania programu Visio](../vsto/visio-solutions.md)   
 [Model obiektu Visio ― omówienie](../vsto/visio-object-model-overview.md)   
 [Porady: programowane tworzenie nowych dokumentów programu Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Porady: programowane zamykanie dokumentów Visio](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Porady: programowane zapisywanie dokumentów Visio](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Porady: programowane drukowanie dokumentów Visio](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  