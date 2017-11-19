---
title: "Porady: programowane Włączanie ochrony dokumentów i części dokumentów | Dokumentacja firmy Microsoft"
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
- document protection
- documents [Office development in Visual Studio], document protection
- Word documents, protection
ms.assetid: af8390fc-c4c7-48c7-94b8-4fedbaac0757
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0d696b0a7bc910d984494e2730b2a959fc3b301c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-protect-documents-and-parts-of-documents"></a>Porady: Programowane włączanie ochrony dokumentów i części dokumentów
  Można dodać ochrony do dokumentów pakietu Microsoft Office Word, aby zabezpieczyć przed wprowadzaniem zmian w dokumencie.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Można również oznaczyć niektórych obszarach dokumentu jako wyjątki, aby określeni użytkownicy mogą edytować tylko te części dokumentu. Na przykład można chronić całego dokumentu z wyjątkiem określonym zakładki. Można opcjonalnie dodawać hasła, tak aby użytkownicy nie można usunąć ochrony dokumentu bez znajomości hasła.  
  
> [!NOTE]  
>  Poniższy przykład nie używaj ochrony hasłem; Warto jednak wziąć pod uwagę przy użyciu hasła podczas dodawania ochrony dokumentu. Aby uzyskać więcej informacji, zobacz przykład ochrony dokumentu w [Office Development ― przykłady i wskazówki](../vsto/office-development-samples-and-walkthroughs.md).  
  
 Formanty zawartości umożliwia również ochrona części dokumentów. Aby uzyskać więcej informacji, zobacz [porady: ochrona części dokumentów za pomocą formantów zawartości](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).  
  
## <a name="protecting-a-document-that-is-part-of-a-document-level-customization"></a>Ochrona dokumentu, który jest częścią dostosowania poziomie dokumentu  
  
#### <a name="to-protect-a-document-that-is-part-of-a-document-level-customization"></a>Aby chronić dokument, który jest częścią dostosowania poziomie dokumentu  
  
1.  Wywołanie <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> metody `ThisDocument` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#111)]  
  
#### <a name="to-exclude-a-bookmark-control-from-document-protection"></a>Aby wykluczyć formant zakładki z ochrona dokumentu  
  
1.  Ochrona za pomocą całego dokumentu <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> metody.  
  
     [!code-vb[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#111)]  
  
2.  Wyklucz `Bookmark1` z ochrony dokumentu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#112](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#112)]
     [!code-csharp[Trin_VstcoreWordAutomation#112](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#112)]  
  
### <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby użyć tych przykładów kodu, należy uruchomić je z `ThisDocument` klasy w projekcie. Te przykłady kodu założono, że masz istniejące <xref:Microsoft.Office.Tools.Word.Bookmark> formantu o nazwie `Bookmark1` w dokumencie, w której znajduje się ten kod.  
  
## <a name="protecting-a-document-by-using-an-vsto-add-in"></a>Ochrona dokumentu przy użyciu dodatku narzędzi VSTO  
  
#### <a name="to-protect-a-document-by-using-an-application-level-vsto-add-in"></a>Aby chronić dokument za pomocą dodatku VSTO poziomie aplikacji  
  
1.  Wywołanie <xref:Microsoft.Office.Interop.Word._Document.Protect%2A> metody <xref:Microsoft.Office.Interop.Word.Document> , który chcesz chronić.  
  
     Poniższy przykładowy kod chroni aktywny dokument. Aby użyć w tym przykładzie kodu, uruchom go z `ThisAddIn` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#111)]  
  
## <a name="see-also"></a>Zobacz też  
 [Ochrona dokumentów w rozwiązaniach na poziomie dokumentu](../vsto/document-protection-in-document-level-solutions.md)   
 [Ochrona za pomocą hasła w dokumentach pakietu Office](../vsto/password-protection-on-office-documents.md)   
 [Porady: zezwalanie na uruchamianie w tle dokumentów z ograniczonymi uprawnieniami kodu](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Porady: dodawanie formantów zakładek do dokumentów programu Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)  
  
  