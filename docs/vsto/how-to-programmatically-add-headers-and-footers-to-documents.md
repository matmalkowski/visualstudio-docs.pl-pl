---
title: 'Porady: programowane Dodawanie nagłówków i stopek do dokumentów'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- headers, adding to Office documents
- documents [Office development in Visual Studio], adding headers
- documents [Office development in Visual Studio], adding footers
- footers, adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 98f9ed1025c264b4fa7432e2ce397e988e6795f4
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256035"
---
# <a name="how-to-programmatically-add-headers-and-footers-to-documents"></a>Porady: programowane Dodawanie nagłówków i stopek do dokumentów
  Możesz dodać tekst nagłówki i stopki w dokumencie przy użyciu <xref:Microsoft.Office.Interop.Word.Section.Headers%2A> właściwości i <xref:Microsoft.Office.Interop.Word.Section.Footers%2A> właściwość <xref:Microsoft.Office.Interop.Word.Section>. Każda sekcja dokumentu zawiera trzy nagłówki i stopki:  
  
-   <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterPrimary>  
  
-   <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterEvenPages>  
  
-   <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterFirstPage>  
  
 Dostosowywanie na poziomie dokumentu i dodatków VSTO różnią się procedury.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="document-level-customizations"></a>Dostosowania na poziomie dokumentów  
 Aby użyć następujące przykłady kodu, należy uruchomić je z `ThisDocument` klasy w projekcie.  
  
### <a name="to-add-text-to-footers-in-the-document"></a>Aby dodać tekst do stopki w dokumencie  
  
1.  Poniższy przykład kodu Ustawia czcionkę tekstu ma zostać wstawiony do głównej stopki każdej sekcji dokumentu, a następnie wstawia tekst do stopki.  
  
     [!code-vb[Trin_VstcoreWordAutomation#114](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#114)]
     [!code-csharp[Trin_VstcoreWordAutomation#114](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#114)]  
  
### <a name="to-add-text-to-headers-in-the-document"></a>Aby dodać tekst do nagłówków w dokumencie  
  
1.  Poniższy przykładowy kod dodaje pole, aby wyświetlić numer strony w każdy nagłówek w dokumencie, a następnie Ustawia wyrównanie akapitu, aby tekst jest wyrównany do prawej nagłówka.  
  
     [!code-vb[Trin_VstcoreWordAutomation#116](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#116)]
     [!code-csharp[Trin_VstcoreWordAutomation#116](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#116)]  
  
## <a name="vsto-add-ins"></a>Dodatków VSTO  
 Aby użyć następujące przykłady kodu, należy uruchomić je z `ThisAddIn` klasy w projekcie.  
  
### <a name="to-add-text-to-footers-in-a-document"></a>Aby dodać tekst do stopki w dokumencie  
  
1.  Poniższy przykład kodu Ustawia czcionkę tekstu ma zostać wstawiony do głównej stopki każdej sekcji dokumentu, a następnie wstawia tekst do stopki. W tym przykładzie kodu używane aktywny dokument.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#114](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#114)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#114](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#114)]  
  
### <a name="to-add-text-to-headers-in-the-document"></a>Aby dodać tekst do nagłówków w dokumencie  
  
1.  Poniższy przykładowy kod dodaje pole, aby wyświetlić numer strony w każdy nagłówek w dokumencie, a następnie Ustawia wyrównanie akapitu, aby tekst jest wyrównany do prawej nagłówka. W tym przykładzie kodu używane aktywny dokument.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#116](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#116)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#116](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#116)]  
  
## <a name="see-also"></a>Zobacz także  
 [Porady: programowane tworzenie nowych dokumentów](../vsto/how-to-programmatically-create-new-documents.md)   
 [Porady: programowane rozszerzanie zakresów w dokumentach](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Porady: programowane przechodzenie w pętli poprzez znalezione elementy w dokumentach](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)  
   