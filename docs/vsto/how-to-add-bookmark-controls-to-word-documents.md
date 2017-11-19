---
title: "Porady: dodawanie formantów zakładek do dokumentów programu Word | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VST.Bookmark.Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Bookmark control, adding to documents
- Create Bookmark Control dialog box
- controls [Office development in Visual Studio], adding to documents
ms.assetid: 2940704e-31f5-4486-854e-76298a9e2ee4
caps.latest.revision: "52"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7da98e9d013f131e889c287cd1d158b3fb25e814
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-bookmark-controls-to-word-documents"></a>Porady: dodawanie formantów zakładek do dokumentów programu Word
  W projektach na poziomie dokumentu, można dodać <xref:Microsoft.Office.Tools.Word.Bookmark> formantów do dokumentów w projekcie w czasie projektowania lub w czasie wykonywania. W dodatku VSTO projektów, można dodać <xref:Microsoft.Office.Tools.Word.Bookmark> formantów do otwartego dokumentu w czasie wykonywania.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 W tym temacie opisano następujące zadania:  
  
-   [Dodawanie formantów zakładek w czasie projektowania](#designtime)  
  
-   [Dodawanie formantów zakładek w czasie wykonywania w projektach na poziomie dokumentu](#runtimedoclevel)  
  
-   [Dodawanie formantów zakładek w czasie wykonywania w projekcie dodatku narzędzi VSTO](#runtimeaddin)  
  
 Aby uzyskać więcej informacji na temat <xref:Microsoft.Office.Tools.Word.Bookmark> formantów, zobacz [formant zakładki](../vsto/bookmark-control.md).  
  
##  <a name="designtime"></a>Dodawanie formantów zakładek w czasie projektowania  
 Istnieje kilka sposobów, aby dodać <xref:Microsoft.Office.Tools.Word.Bookmark> formantów do dokumentów w projektach na poziomie dokumentu w czasie projektowania:  
  
-   W programie Visual Studio **przybornika**.  
  
     Możesz przeciągnąć <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolować z **przybornika** do dokumentu. Należy wybrać w ten sposób, jeśli korzystasz już z **przybornika** do dodawania formantów formularzy systemu Windows do dokumentu.  
  
-   Z poziomu programu Word.  
  
     Możesz dodać <xref:Microsoft.Office.Tools.Word.Bookmark> formantu do dokumentu w taki sam sposób należy dodać natywnego zakładki. Zaletą dodanie go w ten sposób jest nazwę formantu w momencie jego tworzenia.  
  
-   Z **źródeł danych** okna.  
  
     Możesz przeciągnąć <xref:Microsoft.Office.Tools.Word.Bookmark> formantu do dokumentu z **źródeł danych** okna. Jest to przydatne, jeśli chcesz powiązać formant danych w tym samym czasie. Można dodać kontrolki hosta w taki sam sposób, należy dodać formantu formularzy systemu Windows z **źródeł danych** okna. Aby uzyskać więcej informacji, zobacz [powiązania danych i formularze systemu Windows](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### <a name="to-add-a-bookmark-control-to-a-document-from-the-toolbox"></a>Aby dodać kontrolkę zakładki w dokumencie z przybornika  
  
1.  Otwórz **przybornika** i kliknij przycisk **formanty Word** kartę.  
  
2.  Przeciągnij <xref:Microsoft.Office.Tools.Word.Bookmark> formantu do dokumentu.  
  
     **Dodaj zakładkę** zostanie wyświetlone okno dialogowe.  
  
3.  Zaznacz tekst lub innych elementów, które chcesz dołączyć do zakładki.  
  
4.  Kliknij przycisk **OK**.  
  
     Jeśli nie chcesz zachować domyślną nazwę zakładki, można zmienić nazwę w **właściwości** okna.  
  
#### <a name="to-add-a-bookmark-control-to-a-document-in-word"></a>Aby dodać kontrolkę zakładki w dokumencie programu Word  
  
1.  W dokumencie, który znajduje się w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektanta, umieść kursor, której chcesz dodać zakładki, lub zaznacz tekst, który ma zakładki, należy ująć.  
  
2.  Na **Wstaw** karty wstążki w **łącza** kliknij przycisk **zakładki** przycisku.  
  
3.  W **zakładki** okno dialogowe, wpisz nazwę nowej zakładki, a następnie kliknij przycisk **Dodaj**.  
  
##  <a name="runtimedoclevel"></a>Dodawanie formantów zakładek w czasie wykonywania w projektach na poziomie dokumentu  
 Możesz dodać <xref:Microsoft.Office.Tools.Word.Bookmark> steruje programowo do dokumentu w czasie wykonywania za pomocą metody <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> właściwość `ThisDocument` klasy w projekcie. Istnieją dwa przeciążenia metody, których można dodać <xref:Microsoft.Office.Tools.Word.Bookmark> kontroli w następujący sposób:  
  
-   Dodaj <xref:Microsoft.Office.Tools.Word.Bookmark> w określonym zakresie.  
  
-   Dodaj <xref:Microsoft.Office.Tools.Word.Bookmark> opartego na natywnego zakładki w dokumencie (czyli <xref:Microsoft.Office.Interop.Word.Bookmark>).  
  
 Tworzone dynamicznie <xref:Microsoft.Office.Tools.Word.Bookmark> formanty nie są zachowywane w dokumencie, gdy dokument zostanie zamknięty. Jednak natywny <xref:Microsoft.Office.Interop.Word.Bookmark> pozostaje w dokumencie. Można ponownie utworzyć <xref:Microsoft.Office.Tools.Word.Bookmark> opartego na natywnego zakładki przy następnym otwarciu dokumentu. Aby uzyskać więcej informacji, zobacz [dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-bookmark-control-to-a-document-programmatically"></a>Aby dodać kontrolkę zakładki w dokumencie programowo  
  
1.  W `ThisDocument_Startup` obsługi zdarzeń w projekcie, Wstaw następujący kod, aby dodać <xref:Microsoft.Office.Tools.Word.Bookmark> kontroli w pierwszym akapicie w dokumencie.  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#1](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#1)]  
  
    > [!NOTE]  
    >  Jeśli chcesz utworzyć <xref:Microsoft.Office.Tools.Word.Bookmark> kontroli z istniejącego <xref:Microsoft.Office.Interop.Word.Bookmark>, użyj <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> — metoda i przekaż istniejące <xref:Microsoft.Office.Interop.Word.Bookmark>.  
  
##  <a name="runtimeaddin"></a>Dodawanie formantów zakładek w czasie wykonywania w projekcie dodatku narzędzi VSTO  
 Możesz dodać <xref:Microsoft.Office.Tools.Word.Bookmark> formantów programowo do otwartego dokumentu w czasie wykonywania za pomocą dodatku VSTO. W tym celu należy wygenerować <xref:Microsoft.Office.Tools.Word.Document> hosta elementu, który jest oparta na otwartego dokumentu, a następnie użyj metod <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> właściwości tego elementu host. Istnieją dwa przeciążenia metody, których można dodać <xref:Microsoft.Office.Tools.Word.Bookmark> kontroli w następujący sposób:  
  
-   Dodaj <xref:Microsoft.Office.Tools.Word.Bookmark> w określonym zakresie.  
  
-   Dodaj <xref:Microsoft.Office.Tools.Word.Bookmark> opartego na natywnego zakładki w dokumencie (czyli <xref:Microsoft.Office.Interop.Word.Bookmark>).  
  
 Tworzone dynamicznie <xref:Microsoft.Office.Tools.Word.Bookmark> formanty nie są zachowywane w dokumencie, gdy dokument zostanie zamknięty. Jednak natywny <xref:Microsoft.Office.Interop.Word.Bookmark> pozostaje w dokumencie. Można ponownie utworzyć <xref:Microsoft.Office.Tools.Word.Bookmark> opartego na natywnego zakładki przy następnym otwarciu dokumentu. Aby uzyskać więcej informacji, zobacz [przechowywanie formantów dynamicznych w dokumentach pakietu Office](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
 Aby uzyskać więcej informacji na temat generowania elementów hosta w projektów dodatku VSTO zobacz [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
#### <a name="to-add-a-bookmark-control-at-a-specified-range"></a>Aby dodać kontrolkę zakładki w określonym zakresie  
  
1.  Użyj <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> — metoda i przekaż <xref:Microsoft.Office.Interop.Word.Range> , w którym ma zostać dodany <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     Poniższy przykładowy kod dodaje nową <xref:Microsoft.Office.Tools.Word.Bookmark> na początku aktywny dokument. Aby użyć tego przykładu, należy uruchomić kod z `ThisAddIn_Startup` obsługi zdarzeń w projekcie dodatku narzędzi VSTO programu Word.  
  
     [!code-vb[Trin_WordAddInDynamicControls#4](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDynamicControls#4](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#4)]  
  
#### <a name="to-add-a-bookmark-control-that-is-based-on-a-native-bookmark-control"></a>Aby dodać kontrolkę zakładki, która jest oparta na macierzystego formantu zakładki  
  
1.  Użyj <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> — metoda i przekaż istniejące <xref:Microsoft.Office.Interop.Word.Bookmark> , który ma zostać wykorzystany jako podstawa dla nowego <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     Poniższy przykładowy kod tworzy nową <xref:Microsoft.Office.Tools.Word.Bookmark> czyli na podstawie pierwszego <xref:Microsoft.Office.Interop.Word.Bookmark> w aktywnym dokumencie. Aby użyć tego przykładu, należy uruchomić kod z `ThisAddIn_Startup` obsługi zdarzeń w projekcie dodatku narzędzi VSTO programu Word.  
  
     [!code-vb[Trin_WordAddInDynamicControls#5](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#5)]
     [!code-csharp[Trin_WordAddInDynamicControls#5](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#5)]  
  
## <a name="see-also"></a>Zobacz też  
 [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)   
 [Obiekty hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md)   
 [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Ograniczenia programowe elementów hosta i formantów hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Programowanie dodatków VSTO](../vsto/programming-vsto-add-ins.md)   
 [Programowania dostosowań na poziomie dokumentu](../vsto/programming-document-level-customizations.md)   
 [Porady: zmiana rozmiaru formantów zakładki](../vsto/how-to-resize-bookmark-controls.md)  
  
  