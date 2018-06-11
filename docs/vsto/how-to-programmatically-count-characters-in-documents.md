---
title: 'Porady: programowane zliczanie znaków w dokumentach'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- characters, counting in documents
- counting characters in documents
- documents [Office development in Visual Studio], counting characters
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d74a44b57a4d51690af3cadda62b8849a55363e0
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256360"
---
# <a name="how-to-programmatically-count-characters-in-documents"></a>Porady: programowane zliczanie znaków w dokumentach
  Pierwszy znak w dokumencie wynosi znaku na pozycji 0, który reprezentuje punkt wstawienia. Ostatnie położenie znaku jest równa całkowita liczba znaków w dokumencie. Można określić liczbę znaków w dokumencie przy użyciu <xref:Microsoft.Office.Interop.Word.Characters.Count%2A> właściwość <xref:Microsoft.Office.Interop.Word.Characters> kolekcji.  
  
 Uwzględniane są wszystkie znaki w dokumencie, łącznie ze spacjami, znaczników akapitu i innych znaków, które zwykle są ukryte. Nawet nowy pusty dokument zwraca liczbę o jeden znak, ponieważ zawiera on akapitu.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="to-display-the-number-of-characters-in-a-document-level-customization"></a>Aby wyświetlić liczbę znaków w dostosowaniu poziomie dokumentu  
  
1.  Zaznacza cały dokument.  
  
     [!code-vb[Trin_VstcoreWordAutomation#98](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#98)]
     [!code-csharp[Trin_VstcoreWordAutomation#98](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#98)]  
  
2.  Wyświetl liczbę znaków w dokumencie w oknie komunikatu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#99](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#99)]
     [!code-csharp[Trin_VstcoreWordAutomation#99](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#99)]  
  
## <a name="to-display-the-number-of-characters-in-an-vsto-add-in"></a>Aby wyświetlić liczbę znaków w dodatku VSTO  
  
1.  Zaznacza cały dokument. Poniższy przykład wybiera aktywny dokument.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#98](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#98)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#98](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#98)]  
  
2.  Wyświetl liczbę znaków w dokumencie w oknie komunikatu.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#99](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#99)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#99](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#99)]  
  
## <a name="see-also"></a>Zobacz także  
 [Porady: programowane pobieranie znaków początkowych i końcowych w zakresach](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Porady: programowane definiowanie i zaznaczanie zakresów w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)  
  
  