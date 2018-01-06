---
title: "Porady: programowane używanie wbudowanych okien dialogowych w programie Word | Dokumentacja firmy Microsoft"
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
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, Word
ms.assetid: 0c7e4338-dead-4444-868b-3b0212368455
caps.latest.revision: "54"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 25353b95a997380ea682059a43494cc2a977f943
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-use-built-in-dialog-boxes-in-word"></a>Porady: Programowane używanie wbudowanych okien dialogowych w programie Word
  Podczas pracy z programem Microsoft Office Word, są potrzebne do wyświetlenia okna dialogowe dla danych wejściowych użytkownika. Mimo że można tworzyć własne, można także podjęcie podejście przy użyciu wbudowanych oknach dialogowych w programie Word, które są widoczne w <xref:Microsoft.Office.Interop.Word.Dialogs> Kolekcja <xref:Microsoft.Office.Interop.Word.Application> obiektu. Dzięki temu można uzyskać dostępu do ponad 200 wbudowanych okien dialogowych, które są reprezentowane jako wyliczenia.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="displaying-dialog-boxes"></a>Wyświetlanie okien dialogowych  
 Aby wyświetlić okno dialogowe, użyj jednej z wartości <xref:Microsoft.Office.Interop.Word.WdWordDialog> wyliczeniu, aby utworzyć <xref:Microsoft.Office.Interop.Word.Dialog> obiekt reprezentujący okno dialogowe, które mają być wyświetlane. Następnie wywołaj metodę <xref:Microsoft.Office.Interop.Word.Dialog.Show%2A> metody <xref:Microsoft.Office.Interop.Word.Dialog> obiektu.  
  
 Poniższy przykład kodu pokazuje sposób wyświetlania **Otwórz plik** okno dialogowe. Aby użyć tego przykładu, uruchom go z `ThisDocument` lub `ThisAddIn` klasy w projekcie.  
  
 [!code-vb[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#100)]
 [!code-csharp[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#100)]  
  
### <a name="accessing-dialog-box-members-that-are-available-through-late-binding"></a>Uzyskiwanie dostępu do elementów członkowskich okno dialogowe, które są dostępne za pośrednictwem późne wiązanie  
 Niektóre właściwości i metody okien dialogowych w programie Word są dostępne tylko za pośrednictwem późne wiązanie. W języku Visual Basic, projekty where **Option Strict** jest włączone, aby dostęp do tych elementów członkowskich, należy użyć odbicia. Aby uzyskać więcej informacji, zobacz [późne wiązania w rozwiązaniach pakietu Office](../vsto/late-binding-in-office-solutions.md).  
  
 Poniższy przykład kodu pokazuje sposób użycia **nazwa** właściwość **Otwórz plik** okno dialogowe w języku Visual Basic, projekty where **Option Strict** jest wyłączony lub języka Visual C# projektów przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Aby użyć tego przykładu, uruchom go z `ThisDocument` lub `ThisAddIn` klasy w projekcie.  
  
 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]  
  
 Poniższy przykład kodu pokazuje, jak uzyskać dostęp za pomocą odbicia **nazwa** właściwość **Otwórz plik** okno dialogowe w języku Visual Basic, projekty where **Option Strict** jest na serwerze. Aby użyć tego przykładu, uruchom go z `ThisDocument` lub `ThisAddIn` klasy w projekcie.  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: programowane używanie okien dialogowych programu Word w trybie ukrytym](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)   
 [Przegląd modelu obiektów programu Word](../vsto/word-object-model-overview.md)   
 [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Option Strict — instrukcja](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Odbicie (C#)](/dotnet/csharp/programming-guide/concepts/reflection)  
 [Odbicie (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)  
  
  