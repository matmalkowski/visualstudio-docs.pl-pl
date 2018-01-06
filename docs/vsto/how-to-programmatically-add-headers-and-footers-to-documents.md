---
title: "Porady: programowane Dodawanie nagłówków i stopek do dokumentów | Dokumentacja firmy Microsoft"
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
- headers, adding to Office documents
- documents [Office development in Visual Studio], adding headers
- documents [Office development in Visual Studio], adding footers
- footers, adding to documents
ms.assetid: c7a5cc8a-d8c0-48e9-81d3-108aa6bfbb74
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: b0f2651fc4bfedab3c7308c7fa7e8cef604666f0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-add-headers-and-footers-to-documents"></a>Porady: Programowane dodawanie nagłówków i stopek do dokumentów
  Możesz dodać tekst nagłówki i stopki w dokumencie przy użyciu <xref:Microsoft.Office.Interop.Word.Section.Headers%2A> właściwości i <xref:Microsoft.Office.Interop.Word.Section.Footers%2A> właściwość <xref:Microsoft.Office.Interop.Word.Section>. Każda sekcja dokumentu zawiera trzy nagłówki i stopki:  
  
-   <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterPrimary>  
  
-   <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterEvenPages>  
  
-   <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterFirstPage>  
  
 Dostosowywanie na poziomie dokumentu i dodatków VSTO różnią się procedury.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="document-level-customizations"></a>Dostosowania na poziomie dokumentów  
 Aby użyć następujące przykłady kodu, należy uruchomić je z `ThisDocument` klasy w projekcie.  
  
#### <a name="to-add-text-to-footers-in-the-document"></a>Aby dodać tekst do stopki w dokumencie  
  
1.  Poniższy przykład kodu Ustawia czcionkę tekstu ma zostać wstawiony do głównej stopki każdej sekcji dokumentu, a następnie wstawia tekst do stopki.  
  
     [!code-vb[Trin_VstcoreWordAutomation#114](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#114)]
     [!code-csharp[Trin_VstcoreWordAutomation#114](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#114)]  
  
#### <a name="to-add-text-to-headers-in-the-document"></a>Aby dodać tekst do nagłówków w dokumencie  
  
1.  Poniższy przykładowy kod dodaje pole, aby wyświetlić numer strony w każdy nagłówek w dokumencie, a następnie Ustawia wyrównanie akapitu, aby tekst jest wyrównany do prawej nagłówka.  
  
     [!code-vb[Trin_VstcoreWordAutomation#116](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#116)]
     [!code-csharp[Trin_VstcoreWordAutomation#116](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#116)]  
  
## <a name="vsto-add-ins"></a>Dodatków VSTO  
 Aby użyć następujące przykłady kodu, należy uruchomić je z `ThisAddIn` klasy w projekcie.  
  
#### <a name="to-add-text-to-footers-in-a-document"></a>Aby dodać tekst do stopki w dokumencie  
  
1.  Poniższy przykład kodu Ustawia czcionkę tekstu ma zostać wstawiony do głównej stopki każdej sekcji dokumentu, a następnie wstawia tekst do stopki. W tym przykładzie kodu używane aktywny dokument.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#114](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#114)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#114](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#114)]  
  
#### <a name="to-add-text-to-headers-in-the-document"></a>Aby dodać tekst do nagłówków w dokumencie  
  
1.  Poniższy przykładowy kod dodaje pole, aby wyświetlić numer strony w każdy nagłówek w dokumencie, a następnie Ustawia wyrównanie akapitu, aby tekst jest wyrównany do prawej nagłówka. W tym przykładzie kodu używane aktywny dokument.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#116](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#116)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#116](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#116)]  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: programowane tworzenie nowych dokumentów](../vsto/how-to-programmatically-create-new-documents.md)   
 [Porady: programowane rozszerzanie zakresów w dokumentach](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Instrukcje: Programowe przechodzenie w pętli poprzez znalezione elementy w dokumentach](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)  
   