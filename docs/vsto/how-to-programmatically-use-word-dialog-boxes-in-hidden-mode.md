---
title: "Porady: programowane używanie okien dialogowych programu Word w trybie ukrytym | Dokumentacja firmy Microsoft"
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
- hidden dialog boxes
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, hidden mode in Word
ms.assetid: a5619325-8b54-41f1-becb-3f6eae7e4a6b
caps.latest.revision: "48"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3d36bb9342c1db3fcf0fe007b87831b8c921af6d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-use-word-dialog-boxes-in-hidden-mode"></a>Porady: Programowane używanie okien dialogowych programu Word w trybie ukrytym
  Złożone operacje przy użyciu wywołania metody co można wykonać za pomocą wbudowanych okien dialogowych w programie Microsoft Word pakietu Office bez wyświetlania ich do użytkownika. Można to zrobić za pomocą <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> metody <xref:Microsoft.Office.Interop.Word.Dialog> obiektu bez wywoływania elementu <xref:Microsoft.Office.Interop.Word.Dialog.Display%2A> metody.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="examples"></a>Przykłady  
 W poniższych przykładach kodu pokazano sposób użycia **ustawienia strony** okno dialogowe w trybie ukrytym, aby ustawić stronę wiele właściwości instalacji bez udziału użytkownika. W przykładach użyto <xref:Microsoft.Office.Interop.Word.Dialog> obiekt, aby skonfigurować niestandardowy rozmiar strony. Ustawienia specyficzne dla ustawienia strony, takie jak górny margines, dolny margines i tak dalej, są dostępne jako właściwości późnym wiązaniem <xref:Microsoft.Office.Interop.Word.Dialog> obiektu. Te właściwości są tworzone dynamicznie według słów w czasie wykonywania.  
  
 Poniższy przykład przedstawia sposób wykonania tego zadania w projektach Visual Basic gdzie **Option Strict** jest wyłączone, a w projektach Visual C# kierowanych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. W tych projektach późne powiązania funkcji można użyć w Kompilatory języka Visual Basic i Visual C#. Aby użyć tego przykładu, uruchom go z `ThisDocument` lub `ThisAddIn` klasy w projekcie.  
  
 [!code-vb[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#123)]
 [!code-csharp[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#123)]  
  
 Poniższy przykład przedstawia sposób wykonania tego zadania w projektach Visual Basic gdzie **Option Strict** znajduje się na. W tych projektów należy użyć odbicia uzyskać dostęp do właściwości z późnym wiązaniem. Aby użyć tego przykładu, uruchom go z `ThisDocument` lub `ThisAddIn` klasy w projekcie.  
  
 [!code-vb[Trin_VstcoreWordAutomation#104](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#104)]  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: programowane używanie wbudowanych okien dialogowych w programie Word](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)   
 [Przegląd modelu obiektów programu Word](../vsto/word-object-model-overview.md)   
 [Późne wiązania w rozwiązaniach pakietu Office](../vsto/late-binding-in-office-solutions.md)   
 [Odbicie (C#)](/dotnet/csharp/programming-guide/concepts/reflection)  
 [Odbicie (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)  
  
  