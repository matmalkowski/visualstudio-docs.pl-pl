---
title: 'Porady: programowane używanie okien dialogowych programu Word w trybie ukrytym'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden dialog boxes
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, hidden mode in Word
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d5b123f1b58e61dffc64b5df912092edfd3fbf53
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "35677228"
---
# <a name="how-to-programmatically-use-word-dialog-boxes-in-hidden-mode"></a>Porady: programowane używanie okien dialogowych programu Word w trybie ukrytym
  Złożonych operacji za pomocą jednego wywołania metody można wykonywać za pomocą wbudowanych okien dialogowych w programie Microsoft Office Word bez wyświetlania ich do użytkownika. Można to zrobić za pomocą <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> metody <xref:Microsoft.Office.Interop.Word.Dialog> obiektu bez wywoływania <xref:Microsoft.Office.Interop.Word.Dialog.Display%2A> metody.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="examples"></a>Przykłady  
 Poniższe przykłady kodu przedstawiają sposoby użycia **ustawienia strony** okno dialogowe w trybie ukrytym, aby ustawić stronę wiele właściwości instalacji bez udziału użytkownika. W przykładach użyto <xref:Microsoft.Office.Interop.Word.Dialog> obiektu, aby skonfigurować niestandardowy rozmiar strony. Określone ustawienia strony, takie jak górny margines, dolny margines i tak dalej, są dostępne jako właściwości późnego wiązania <xref:Microsoft.Office.Interop.Word.Dialog> obiektu. Te właściwości są tworzone przez program Word dynamicznie w czasie wykonywania.  
  
 Poniższy przykład przedstawia sposób wykonania tego zadania w projektach języka Visual Basic gdzie **Option Strict** jest wyłączona i w projektach Visual C#, których platformą docelową [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. W tych projektach można użyć późne powiązania funkcji w Kompilatory języka Visual Basic i Visual C#. Aby użyć tego przykładu, należy uruchomić go z `ThisDocument` lub `ThisAddIn` klasy w projekcie.  
  
 [!code-vb[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#123)]
 [!code-csharp[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#123)]  
  
 Poniższy przykład przedstawia sposób wykonania tego zadania w projektach języka Visual Basic gdzie **Option Strict** znajduje się na. W tych projektach należy użyć odbicia, uzyskiwania dostępu do właściwości późnego wiązania. Aby użyć tego przykładu, należy uruchomić go z `ThisDocument` lub `ThisAddIn` klasy w projekcie.  
  
 [!code-vb[Trin_VstcoreWordAutomation#104](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#104)]  
  
## <a name="see-also"></a>Zobacz także  
 [Porady: programowane używanie wbudowanych okien dialogowych w programie Word](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)   
 [Model obiektu Word — omówienie](../vsto/word-object-model-overview.md)   
 [Późne powiązania w rozwiązaniach pakietu Office](../vsto/late-binding-in-office-solutions.md)   
 [Odbicie (C#)](/dotnet/csharp/programming-guide/concepts/reflection)  
 [Odbicie (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)  
  
  