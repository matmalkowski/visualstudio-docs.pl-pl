---
title: "Porady: programowane otwieranie istniejących dokumentów | Dokumentacja firmy Microsoft"
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
- documents [Office development in Visual Studio], opening
- Word [Office development in Visual Studio], opening documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 151571ace6790f05c067f8dff641988301bc1b0e
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-open-existing-documents"></a>Porady: Programowane otwieranie istniejących dokumentów
  <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> Metody otwiera istniejący dokument programu Microsoft Office Word określony przez w pełni kwalifikowana nazwa i ścieżka pliku. Ta metoda zwraca <xref:Microsoft.Office.Interop.Word.Document> reprezentujący otwarty dokument.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-open-a-document"></a>Aby otworzyć dokument  
  
-   Wywołanie <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> metody <xref:Microsoft.Office.Interop.Word.Documents> kolekcji i podaj ścieżkę do dokumentu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#5)]  
  
### <a name="to-open-a-document-as-read-only"></a>Aby otworzyć dokument jako tylko do odczytu  
  
-   Wywołanie <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> metody, podaj ścieżkę do dokumentu i ustaw *tylko do odczytu* argument **True** w wywołaniu metody.  
  
     [!code-vb[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#6)]
     [!code-csharp[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#6)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 W tym przykładzie kodu wymaga następujących elementów:  
  
-   Dokument o nazwie NewDocument.doc musi istnieć w katalogu o nazwie Test na dysku C.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: programowane tworzenie nowych dokumentów](../vsto/how-to-programmatically-create-new-documents.md)   
 [Porady: programowane zamykanie dokumentów](../vsto/how-to-programmatically-close-documents.md)   
 [Parametry opcjonalne w rozwiązaniach Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  