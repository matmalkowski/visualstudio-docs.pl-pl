---
title: 'Porady: programowane Ustawianie opcji wyszukiwania w programie Word | Dokumentacja firmy Microsoft'
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
- settings, Word search options
- documents [Office development in Visual Studio], search options
- Word, searching options
- searching, Word options
ms.assetid: 4412b4e8-2868-4afb-a593-983603ef9b02
caps.latest.revision: "46"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: b6bd57dfbb7cec6075d72b80228e77669e365dd2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-set-search-options-in-word"></a>Porady: Programowane ustawianie opcji wyszukiwania w programie Word
  Istnieją dwa sposoby ustawiania opcji wyszukiwania dla zaznaczenia w dokumentach programu Microsoft Office Word:  
  
-   Ustawianie właściwości poszczególnych <xref:Microsoft.Office.Interop.Word.Find> obiektu.  
  
-   Używać argumentów <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metody <xref:Microsoft.Office.Interop.Word.Find> obiektu.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="using-properties-of-a-find-object"></a>Za pomocą właściwości obiektu Znajdź  
 Poniższy kod ustawia właściwości <xref:Microsoft.Office.Interop.Word.Find> obiektu wyszukiwania tekstu w bieżącym zaznaczeniu. Zwróć uwagę, że kryteria wyszukiwania, takie jak wyszukiwanie do przodu, zawijania i tekst do wyszukania, to właściwości <xref:Microsoft.Office.Interop.Word.Find> obiektu.  
  
 Ustawienie każdej z właściwości <xref:Microsoft.Office.Interop.Word.Find> obiekt nie jest przydatne podczas pisania kodu C#, ponieważ należy określić jako parametry w tej samej właściwości <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metody. Dlatego w tym przykładzie zawiera tylko kod Visual Basic.  
  
#### <a name="to-set-search-options-using-a-find-object"></a>Aby ustawić opcje wyszukiwania przy użyciu obiektu Znajdź  
  
1.  Ustawianie właściwości <xref:Microsoft.Office.Interop.Word.Find> obiektu do wyszukiwania do przodu do zaznaczenia tekstu **mnie znaleźć**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#76](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#76)]  
  
## <a name="using-execute-method-arguments"></a>Za pomocą wykonać argumentów — metoda  
 Poniższy kod używa <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metody <xref:Microsoft.Office.Interop.Word.Find> obiektu wyszukiwania tekstu w bieżącym zaznaczeniu. Należy zauważyć, że kryteria wyszukiwania, takie jak wyszukiwanie do przodu, zawijania i tekst do wyszukania, są przekazywane jako parametry <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metody.  
  
#### <a name="to-set-search-options-using-execute-method-arguments"></a>Aby ustawić opcje wyszukiwania przy użyciu argumentów metody Execute  
  
1.  Przekaż kryteria wyszukiwania jako parametry <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metodę wyszukiwania do przodu przez zaznaczenie tekstu **mnie znaleźć**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#77)]
     [!code-csharp[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#77)]  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: programowane wyszukiwanie i zastępowanie tekstu w dokumentach](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [Porady: programowane przechodzenie w pętli poprzez znalezione elementy w dokumentach](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Instrukcje: Programowe przywracanie zaznaczenia po wyszukiwaniu](../vsto/how-to-programmatically-restore-selections-after-searches.md)  
  
  