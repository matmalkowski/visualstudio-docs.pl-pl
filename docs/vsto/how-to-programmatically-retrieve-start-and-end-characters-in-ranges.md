---
title: 'Porady: programowane pobieranie znaków początkowych i końcowych w zakresach'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1244fb2ba0a9e902d4dd853e7bef25376a205a0e
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "35676367"
---
# <a name="how-to-programmatically-retrieve-start-and-end-characters-in-ranges"></a>Porady: programowane pobieranie znaków początkowych i końcowych w zakresach
  W tym przykładzie pokazano, jak można pobrać pozycji znaku pozycji początkowej i końcowej zakresu.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="to-retrieve-start-and-end-characters-of-a-range-in-a-document-level-customization"></a>Aby pobrać znaków początkowych i końcowych zakresu w dostosowaniu na poziomie dokumentu  
  
1.  Pobierz wartości <xref:Microsoft.Office.Interop.Word.Range.Start%2A> i <xref:Microsoft.Office.Interop.Word.Range.End%2A> właściwości <xref:Microsoft.Office.Interop.Word.Range> obiektu. Poniższy przykładowy kod pobiera położenie początkowe i końcowe drugiego zdania w dokumencie. Aby wykorzystać ten przykład kodu, należy uruchomić go z `ThisDocument` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#25)]  
  
## <a name="to-retrieve-start-and-end-characters-of-a-range-by-using-a-vsto-add-in"></a>Aby pobrać znaków początkowych i końcowych zakresu przy użyciu dodatku narzędzi VSTO  
  
1.  Pobierz wartości <xref:Microsoft.Office.Interop.Word.Range.Start%2A> i <xref:Microsoft.Office.Interop.Word.Range.End%2A> właściwości <xref:Microsoft.Office.Interop.Word.Range> obiektu. Poniższy przykładowy kod pobiera położenie początkowe i końcowe drugiego zdania w aktywnym dokumencie. Aby wykorzystać ten przykład kodu, należy uruchomić go z `ThisAddIn` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#25)]  
  
## <a name="see-also"></a>Zobacz także  
 [Porady: programowane definiowanie i zaznaczanie zakresów w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Porady: programowane rozszerzanie zakresów w dokumentach](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Porady: programowane Resetowanie zakresów w dokumentach programu Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Porady: programowane zwijanie zakresów lub zaznaczenia w dokumentach](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Porady: programowane wykluczanie znaczników akapitu podczas tworzenia zakresów](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)   
 [Porady: programowane zliczanie znaków w dokumentach](../vsto/how-to-programmatically-count-characters-in-documents.md)  
  
  