---
title: "Porady: programowane wykluczanie znaczników akapitu podczas tworzenia zakresów | Dokumentacja firmy Microsoft"
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
- documents [Office development in Visual Studio], excluding paragraphs
- ranges, excluding paragraph marks in Word
- documents [Office development in Visual Studio], paragraph marks
- paragraphs, controlling structure
ms.assetid: 6d563834-34bd-4462-a556-4339d9277eee
caps.latest.revision: "50"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 5f726a30a7ae50e35726b67336ec41f50be60b24
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-exclude-paragraph-marks-when-creating-ranges"></a>Porady: Programowane wykluczanie znaczników akapitu podczas tworzenia zakresów
  Gdy utworzysz <xref:Microsoft.Office.Interop.Word.Range> obiektu akapitu, wszystkie znaki niedrukowalne, takie jak znaczników akapitu w oparciu znajdują się w zakresie. Możesz wstawić tekst z akapitu źródła do akapitu docelowego. Jeśli nie chcesz podzielić akapitu docelowego na oddzielnych akapitów, następnie należy najpierw usunąć znacznik akapitu z akapitu źródła. Ponadto ponieważ informacje dotyczące formatowania akapitu są przechowywane w ramach znak, nie można uwzględniać to po włożeniu zakres do istniejącego akapitu.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Na poniższej przykładowej procedurze deklaruje dwóch zmiennych ciągu, pobiera zawartość akapitów pierwszego i drugiego w aktywnym dokumencie, a następnie wymiany ich zawartość. W przykładzie pokazano następnie usuwając znacznik akapitu z zakresu przy użyciu <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> — metoda i wstawianie tekstu akapitu.  
  
### <a name="to-control-paragraph-structure-when-inserting-text"></a>Aby kontrolować struktury akapitu podczas wstawiania tekstu  
  
1.  Utwórz dwie zmienne zakresu akapitów pierwszego i drugiego i pobrać jego zawartość <xref:Microsoft.Office.Interop.Word.Range.Text%2A> właściwości.  
  
     Poniższy przykład kodu może służyć w dostosowaniu poziomie dokumentu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#27)]
     [!code-csharp[Trin_VstcoreWordAutomation#27](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#27)]  
  
     Poniższy przykład kodu można w dodatku VSTO poziomie aplikacji. Ten kod zawiera aktywny dokument.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#27)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#27](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#27)]  
  
2.  Przypisz <xref:Microsoft.Office.Interop.Word.Range.Text%2A> właściwości zamiana tekstu między dwoma akapitów.  
  
     [!code-vb[Trin_VstcoreWordAutomation#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#28)]
     [!code-csharp[Trin_VstcoreWordAutomation#28](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#28)]  
  
3.  Z kolei wybierz każdego zakresu i Wstrzymaj, aby wyświetlić wyniki w oknie komunikatu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#29)]
     [!code-csharp[Trin_VstcoreWordAutomation#29](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#29)]  
  
4.  Dostosuj `firstRange` przy użyciu <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> metody, aby znacznik akapitu nie jest już częścią `firstRange`.  
  
     [!code-vb[Trin_VstcoreWordAutomation#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#30)]
     [!code-csharp[Trin_VstcoreWordAutomation#30](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#30)]  
  
5.  Zastąp reszty tekstu w pierwszym akapicie przypisywanie nowe parametry do <xref:Microsoft.Office.Interop.Word.Range.Text%2A> właściwości zakresu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#31)]
     [!code-csharp[Trin_VstcoreWordAutomation#31](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#31)]  
  
6.  Zastąp tekst w `secondRange`, wraz ze znacznikiem.  
  
     [!code-vb[Trin_VstcoreWordAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#32)]
     [!code-csharp[Trin_VstcoreWordAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#32)]  
  
7.  Wybierz `firstRange` i Wstrzymaj, aby wyświetlić wyniki w oknie komunikatu, a następnie wykonaj taki sam jak `secondRange`.  
  
     Ponieważ `firstRange` została ponownie zdefiniowana do wykluczanie znaczników akapitu, jest zachowywana oryginalna formatowanie akapitu. Jednak zdania został wstawiony przez znak akapitu w `secondRange`, usuwanie oddzielny akapit.  
  
     [!code-vb[Trin_VstcoreWordAutomation#33](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#33)]
     [!code-csharp[Trin_VstcoreWordAutomation#33](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#33)]  
  
     Oryginalna zawartość obu zakresów zostały zapisane jako ciągi, aby przywrócić go do stanu.  
  
8.  Dopasuj `firstRange` dołączenie znak za pomocą <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> metody dla pozycji o jeden znak.  
  
     [!code-vb[Trin_VstcoreWordAutomation#34](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#34)]
     [!code-csharp[Trin_VstcoreWordAutomation#34](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#34)]  
  
9. Usuń folder `secondRange`. Spowoduje to przywrócenie akapitu trzech do oryginalnego położenia.  
  
     [!code-vb[Trin_VstcoreWordAutomation#35](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#35)]
     [!code-csharp[Trin_VstcoreWordAutomation#35](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#35)]  
  
10. Przywrócić oryginalny tekst akapitu w `firstRange`.  
  
     [!code-vb[Trin_VstcoreWordAutomation#36](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#36)]
     [!code-csharp[Trin_VstcoreWordAutomation#36](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#36)]  
  
11. Użyj <xref:Microsoft.Office.Interop.Word.Range.InsertAfter%2A> metody <xref:Microsoft.Office.Interop.Word.Range> obiekt do wstawienia oryginalnej zawartości dwóch akapitu po `firstRange`, a następnie wybierz `firstRange`.  
  
     [!code-vb[Trin_VstcoreWordAutomation#37](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#37)]
     [!code-csharp[Trin_VstcoreWordAutomation#37](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#37)]  
  
## <a name="document-level-customization-example"></a>Przykład dostosowania na poziomie dokumentu  
  
#### <a name="to-control-paragraph-structure-when-inserting-text-in-document-level-customizations"></a>Aby kontrolować struktury akapitu podczas wstawiania tekstu w dostosowaniach na poziomie dokumentu  
  
1.  W poniższym przykładzie przedstawiono metodę Zakończenie dostosowywania na poziomie dokumentu. Aby użyć tego kodu, uruchom go z `ThisDocument` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomation#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#26)]
     [!code-csharp[Trin_VstcoreWordAutomation#26](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#26)]  
  
## <a name="vsto-add-in-example"></a>Przykład dodatku narzędzi VSTO  
  
#### <a name="to-control-paragraph-structure-when-inserting-text-in-an-vsto-add-in"></a>Aby kontrolować struktury akapitu podczas wstawiania tekstu w dodatku VSTO  
  
1.  W poniższym przykładzie przedstawiono metodę pełną dodatku VSTO. Aby użyć tego kodu, uruchom go z `ThisAddIn` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#26)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#26](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#26)]  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: programowane rozszerzanie zakresów w dokumentach](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Porady: programowane zwijanie zakresów lub zaznaczenia w dokumentach](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Porady: programowane Wstawianie tekstu w dokumentach programu Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Porady: programowane Resetowanie zakresów w programie Word dokumentów](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Porady: programowane definiowanie i zaznaczanie zakresów w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Parametry opcjonalne w rozwiązaniach Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  