---
title: "Porady: programowane otwieranie dokumentów programu Visio | Dokumentacja firmy Microsoft"
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
- documents [Office development in Visual Studio], opening Visio documents
- Visio [Office development in Visual Studio], opening Visio documents
ms.assetid: bddb820c-bde7-4d21-a0b3-6d1968baccab
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1b2a6c395ed6dbfb8265ac131dd4318b590bf92e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-open-visio-documents"></a>Porady: Programowane otwieranie dokumentów programu Visio
  Istnieją dwie metody otwieranie istniejących dokumentów Microsoft Office Visio: otwarte i OpenEx. Metoda OpenEx jest taki sam jak metody Open, ale zawiera argumenty, w których element wywołujący można określić sposób otwierania dokumentu.  
  
 Aby uzyskać szczegółowe informacje o modelu obiektów, zobacz dokumentację odwołania VBA dla [Microsoft.Office.Interop.Visio.Documents.Open](https://msdn.microsoft.com/library/office/ff765240.aspx) — metoda i [Microsoft.Office.Interop.Visio.Documents.OpenEx](https://msdn.microsoft.com/library/office/ff767229.aspx) Metoda.  
  
## <a name="opening-a-visio-document"></a>Otwieranie dokumentów Visio  
  
#### <a name="to-open-a-visio-document"></a>Aby otworzyć dokument programu Visio  
  
-   Wywołaj metodę Microsoft.Office.Interop.Visio.Documents.Open i podaj pełną ścieżkę dokumentu programu Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#5)]  
  
## <a name="opening-a-visio-document-with-specified-arguments"></a>Otwieranie dokumentów programu Visio z określonymi argumentami  
  
#### <a name="to-open-a-visio-document-as-read-only-and-docked"></a>Aby otworzyć dokument programu Visio jako tylko do odczytu i jest zadokowane  
  
-   Wywołaj metodę Microsoft.Office.Interop.Visio.Documents.OpenEx, podaj pełną ścieżkę dokumentu programu Visio i obejmują argumentów ma być używany — w takim przypadku, zadokowanych i tylko do odczytu.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#6)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 W tym przykładzie kodu wymaga następujących elementów:  
  
-   Dokument programu Visio o nazwie `myDrawing.vsd` musi znajdować się w katalogu o nazwie `Test` w folderze Moje dokumenty (dla systemu Windows XP i starszych) lub w folderze dokumenty (dla systemu Windows Vista).  
  
## <a name="see-also"></a>Zobacz też  
 [Rozwiązania programu Visio](../vsto/visio-solutions.md)   
 [Model obiektu Visio ― omówienie](../vsto/visio-object-model-overview.md)   
 [Porady: programowane tworzenie nowych dokumentów programu Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Porady: programowane zamykanie dokumentów Visio](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Porady: programowane zapisywanie dokumentów Visio](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Instrukcje: Programowe drukowanie dokumentów programu Visio](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  