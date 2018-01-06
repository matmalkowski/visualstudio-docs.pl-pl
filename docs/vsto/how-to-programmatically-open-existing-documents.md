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
ms.assetid: 08f7fe4b-d96d-4a0c-b32a-aa7fd7992316
caps.latest.revision: "44"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 991a282cb3fc8a34f3434c9cdb0a9be214c9e3bf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
  
  