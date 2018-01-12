---
title: "Porady: programowane pobieranie początkowych i końcowych w zakresach | Dokumentacja firmy Microsoft"
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
- ranges, retrieving start and end characters
- end characters
- start characters
- documents [Office development in Visual Studio], retrieving ranges
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 51f88435a5dff346e3de793b408f67e2837478e8
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-retrieve-start-and-end-characters-in-ranges"></a>Porady: Programowane pobieranie znaczników początkowych i końcowych w zakresach
  W przykładzie pokazano, jak można pobrać pozycji znaku pozycji początkowej i końcowej zakresu.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-retrieve-start-and-end-characters-of-a-range-in-a-document-level-customization"></a>Aby pobrać znaków początkowych i końcowych zakresu w dostosowaniu poziomie dokumentu  
  
1.  Pobierz wartości <xref:Microsoft.Office.Interop.Word.Range.Start%2A> i <xref:Microsoft.Office.Interop.Word.Range.End%2A> właściwości <xref:Microsoft.Office.Interop.Word.Range> obiektu. Poniższy przykładowy kod pobiera położenie początkowe i końcowe drugiego zdania w dokumencie. Aby użyć w tym przykładzie kodu, uruchom go z `ThisDocument` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#25)]  
  
### <a name="to-retrieve-start-and-end-characters-of-a-range-by-using-an-vsto-add-in"></a>Aby pobrać znaków początkowych i końcowych zakresu przy użyciu dodatku narzędzi VSTO  
  
1.  Pobierz wartości <xref:Microsoft.Office.Interop.Word.Range.Start%2A> i <xref:Microsoft.Office.Interop.Word.Range.End%2A> właściwości <xref:Microsoft.Office.Interop.Word.Range> obiektu. Poniższy przykładowy kod pobiera położenie początkowe i końcowe drugiego zdania w aktywnym dokumencie. Aby użyć w tym przykładzie kodu, uruchom go z `ThisAddIn` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#25)]  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: programowane definiowanie i zaznaczanie zakresów w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Porady: programowane rozszerzanie zakresów w dokumentach](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Porady: programowane Resetowanie zakresów w programie Word dokumentów](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Porady: programowane zwijanie zakresów lub zaznaczenia w dokumentach](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Porady: programowane wykluczanie znaczników akapitu podczas tworzenia zakresów](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)   
 [Instrukcje: Programowe zliczanie znaków w dokumentach](../vsto/how-to-programmatically-count-characters-in-documents.md)  
  
  