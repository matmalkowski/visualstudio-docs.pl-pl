---
title: "Porady: programowane wyszukiwanie i zastępowanie tekstu w dokumentach | Dokumentacja firmy Microsoft"
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
- documents [Office development in Visual Studio], searching
- text searches, replacing text
- text searches, documents
- text [Office development in Visual Studio], searching in documents
- text [Office development in Visual Studio], text searches
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 658da08ee7d61651b02d7d42158637dad7ab16c4
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-search-for-and-replace-text--in-documents"></a>Porady: Programowane wyszukiwanie i zastępowanie tekstu w dokumentach
  <xref:Microsoft.Office.Interop.Word.Find> Obiekt jest elementem członkowskim <xref:Microsoft.Office.Interop.Word.Selection> i <xref:Microsoft.Office.Interop.Word.Range> obiektów i można użyć dowolnego z nich do wyszukiwania tekstu w dokumentach programu Microsoft Office Word. Polecenie replace jest rozszerzeniem polecenie find.  
  
 Użyj <xref:Microsoft.Office.Interop.Word.Find> do pętli dokumentu Microsoft Office Word i wyszukać określonego tekstu, formatowanie lub style obiektu, a następnie użyj <xref:Microsoft.Office.Interop.Word.Find.Replacement%2A> właściwości, aby zastąpić dowolne elementy znalezione.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="using-a-selection-object"></a>Za pomocą obiektu zaznaczenia  
 Jeśli używasz <xref:Microsoft.Office.Interop.Word.Selection> obiekt, aby znaleźć tekstu, wyszukiwania kryteria są stosowane tylko względem aktualnie zaznaczonego tekstu. Jeśli <xref:Microsoft.Office.Interop.Word.Selection> jest punkt wstawienia, a następnie dokumentu jest przeszukiwany. Gdy element zostanie znaleziony, który jest zgodny z kryteriami wyszukiwania, jest automatycznie wybierany.  
  
 Należy zauważyć, że <xref:Microsoft.Office.Interop.Word.Find> kryteria kumulują się, co oznacza, że kryteria są dodawane do poprzednich kryteria wyszukiwania. Wyczyść formatowanie poprzednich wyników wyszukiwania za pomocą <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A> metoda przed wyszukiwania.  
  
#### <a name="to-find-text-using-a-selection-object"></a>Aby znaleźć za pomocą obiektu zaznaczenia tekstu  
  
1.  Ciąg wyszukiwania można przypisać do zmiennej.  
  
     [!code-vb[Trin_VstcoreWordAutomation#68](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#68)]
     [!code-csharp[Trin_VstcoreWordAutomation#68](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#68)]  
  
2.  Wyczyść formatowanie poprzednich wyników wyszukiwania.  
  
     [!code-vb[Trin_VstcoreWordAutomation#69](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#69)]
     [!code-csharp[Trin_VstcoreWordAutomation#69](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#69)]  
  
3.  Wykonaj wyszukiwanie i wyświetlać okno komunikatu z wynikami.  
  
     [!code-vb[Trin_VstcoreWordAutomation#70](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#70)]
     [!code-csharp[Trin_VstcoreWordAutomation#70](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#70)]  
  
 W poniższym przykładzie przedstawiono metody ukończenia.  
  
 [!code-vb[Trin_VstcoreWordAutomation#67](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#67)]
 [!code-csharp[Trin_VstcoreWordAutomation#67](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#67)]  
  
## <a name="using-a-range-object"></a>Obiekt zakresu  
 Przy użyciu <xref:Microsoft.Office.Interop.Word.Range> obiektu umożliwia wyszukiwanie tekstu bez wyświetlania niczego w interfejsie użytkownika. <xref:Microsoft.Office.Interop.Word.Find> Zwraca obiekt **True** Jeśli zostanie znaleziony tekst, który jest zgodny z kryteriami wyszukiwania i **False** jeśli jej nie ma. Również ponownie definiuje <xref:Microsoft.Office.Interop.Word.Range> obiektu zgodne z kryteriami wyszukiwania, jeśli zostanie znaleziony tekst.  
  
#### <a name="to-find-text-using-a-range-object"></a>Aby znaleźć tekst przy użyciu obiektu zakresu  
  
1.  Zdefiniuj <xref:Microsoft.Office.Interop.Word.Range> obiekt, który składa się z drugiego akapitu w dokumencie.  
  
     Poniższy przykład kodu może służyć w dostosowaniu poziomie dokumentu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#72](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#72)]
     [!code-csharp[Trin_VstcoreWordAutomation#72](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#72)]  
  
     Poniższy przykład kodu można używać w dodatku VSTO. W tym przykładzie użyto aktywny dokument.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#72](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#72)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#72](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#72)]  
  
2.  Przy użyciu <xref:Microsoft.Office.Interop.Word.Range.Find%2A> właściwość <xref:Microsoft.Office.Interop.Word.Range> obiektów, najpierw usuń wszystkie istniejące opcje formatowania, a następnie wyszukaj ciąg **mnie znaleźć**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#73](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#73)]
     [!code-csharp[Trin_VstcoreWordAutomation#73](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#73)]  
  
3.  Wyświetl wyniki wyszukiwania w oknie komunikatu, a następnie wybierz <xref:Microsoft.Office.Interop.Word.Range> aby go wyświetlić.  
  
     [!code-vb[Trin_VstcoreWordAutomation#74](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#74)]
     [!code-csharp[Trin_VstcoreWordAutomation#74](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#74)]  
  
     Jeśli wyszukiwanie nie powiedzie się, zostanie wybrane ust; Jeśli to się powiedzie, kryteria wyszukiwania są wyświetlane.  
  
 Poniższy przykład przedstawia kompletny kod dla dostosowania poziomie dokumentu. Aby użyć tego przykładu, należy uruchomić kod z `ThisDocument` klasy w projekcie.  
  
 [!code-vb[Trin_VstcoreWordAutomation#71](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#71)]
 [!code-csharp[Trin_VstcoreWordAutomation#71](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#71)]  
  
 Poniższy przykład przedstawia kompletny kod dla dodatku VSTO. Aby użyć tego przykładu, należy uruchomić kod z `ThisAddIn` klasy w projekcie.  
  
 [!code-vb[Trin_VstcoreWordAutomationAddIn#71](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#71)]
 [!code-csharp[Trin_VstcoreWordAutomationAddIn#71](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#71)]  
  
## <a name="searching-for-and-replacing-text-in-documents"></a>Wyszukiwanie i zastępowanie tekstu w dokumentach  
 Poniższy kod wyszukiwania w bieżącym zaznaczeniu i zastępuje wszystkie wystąpienia ciągu **mnie znaleźć** z ciągiem **znaleziono**.  
  
#### <a name="to-search-for-and-replace-text-in-documents"></a>Do wyszukiwania i zamieniania tekstu w dokumentach  
  
1.  Dodaj poniższy przykładowy kod do `ThisDocument` lub `ThisAddIn` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomation#75](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#75)]
     [!code-csharp[Trin_VstcoreWordAutomation#75](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#75)]  
  
     <xref:Microsoft.Office.Interop.Word.Find> Klasa ma <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A> metody i <xref:Microsoft.Office.Interop.Word.Replacement> klasy również ma własną <xref:Microsoft.Office.Interop.Word.Replacement.ClearFormatting%2A> metody. Przeprowadzając Znajdowanie i zamienianie operacji, należy użyć metody ClearFormatting obu obiektów. Jeśli można go używać tylko na <xref:Microsoft.Office.Interop.Word.Find> obiektu, może uzyskać nieprzewidziane wyniki w tekst zastępczy.  
  
2.  Użyj <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metody <xref:Microsoft.Office.Interop.Word.Find> obiekt, aby zastąpić każdego znalezionego elementu. Aby określić elementy, które można zastąpić, użyj *Zastąp* parametru. Ten parametr może mieć jedną z następujących <xref:Microsoft.Office.Interop.Word.WdReplace> wartości:  
  
    -   <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceAll>Zamienia wszystkie znalezione elementy.  
  
    -   <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceNone>zastępuje brak znaleziono elementów.  
  
    -   <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceOne>Zamienia pierwszy znaleziony element.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: programowane Ustawianie opcji wyszukiwania w programie Word](../vsto/how-to-programmatically-set-search-options-in-word.md)   
 [Porady: programowane przechodzenie w pętli poprzez znalezione elementy w dokumentach](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Porady: programowane definiowanie i zaznaczanie zakresów w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Porady: programowane Przywracanie zaznaczenia po wyszukiwaniu](../vsto/how-to-programmatically-restore-selections-after-searches.md)   
 [Parametry opcjonalne w rozwiązaniach Office](../vsto/optional-parameters-in-office-solutions.md)  
  