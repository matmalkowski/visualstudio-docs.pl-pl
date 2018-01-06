---
title: "Porady: zmiana rozmiaru formantów zakładki | Dokumentacja firmy Microsoft"
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
- controls [Office development in Visual Studio], resizing
- Bookmark control, resizing
ms.assetid: 3de1c774-921a-4113-a54a-e3b8d4a65d53
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 4129e7405422f5b9490965e658caebce216db1e2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-resize-bookmark-controls"></a>Porady: zmiana rozmiaru formantów zakładki
  Ustawianie rozmiaru <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolować po dodaniu go do dokumentu programu Microsoft Office Word. Można również zmienić w późniejszym czasie.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Istnieją trzy sposoby zmiany rozmiaru zakładki:  
  
-   Dodaj lub usuń tekst w <xref:Microsoft.Office.Tools.Word.Bookmark> formantu.  
  
     Po dodaniu tekstu w zakładce Rozmiar zakładki automatycznie zwiększany zawiera nowego tekstu. Kiedy usuniesz tekst, rozmiar zakładki będzie automatycznie zmniejszany.  
  
-   Zmień <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> i <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> właściwości <xref:Microsoft.Office.Tools.Word.Bookmark> formantu.  
  
     Jest to przydatne w przypadku zmiany rozmiaru tylko kilku znaków.  
  
-   Utwórz ponownie <xref:Microsoft.Office.Tools.Word.Bookmark> formantu.  
  
     Jest to przydatne, jeśli istnieje istotną zmianę rozmiaru lub położenia zakładki.  
  
 W projektach na poziomie dokumentu, można dodać <xref:Microsoft.Office.Tools.Word.Bookmark> formantów do dokumentów w projekcie w czasie projektowania lub w czasie wykonywania. W dodatku VSTO projektów, można dodać <xref:Microsoft.Office.Tools.Word.Bookmark> formantów do otwartego dokumentu w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [porady: dodawanie formantów zakładek do dokumentów programu Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="changing-the-start-and-end-properties"></a>Zmiana rozpoczęcia i zakończenia właściwości  
  
#### <a name="to-resize-a-bookmark-in-a-document-level-project-at-design-time"></a>Aby zmienić rozmiar zakładki w projektach na poziomie dokumentu w czasie projektowania  
  
1.  Wybierz zakładki w **właściwości** okna.  
  
2.  Zwiększa lub zmniejsza wartość <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> właściwości.  
  
3.  Zwiększa lub zmniejsza wartość <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> właściwości.  
  
#### <a name="to-resize-a-bookmark-in-a-document-level-project-at-run-time"></a>Aby zmienić rozmiar zakładki w projektach na poziomie dokumentu w czasie wykonywania  
  
1.  Modyfikowanie <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> i <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> właściwości <xref:Microsoft.Office.Tools.Word.Bookmark> utworzone w czasie wykonywania, lub w czasie projektowania.  
  
     Poniższy przykładowy kod dodaje pięć znaków do początku zakładki o nazwie `SampleBookmark`. Ten kod przyjęto założenie, że istnieje co najmniej pięć znaków tekstu przed zakładką.  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#2](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#2)]  
  
     Poniższy przykładowy kod dodaje pięć znaków na końcu tego samego zakładki. Ten kod przyjęto założenie, że po zakładki są co najmniej pięć znaków tekstu.  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#3](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#3)]  
  
#### <a name="to-resize-a-bookmark-in-an-vsto-add-in-project-at-run-time"></a>Aby zmienić rozmiar zakładki w projekcie dodatku narzędzi VSTO w czasie wykonywania  
  
1.  Modyfikowanie <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> i <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> właściwości <xref:Microsoft.Office.Tools.Word.Bookmark> utworzone w czasie wykonywania.  
  
     Poniższy przykład kodu tworzy <xref:Microsoft.Office.Tools.Word.Bookmark> zawiera tekst w pierwszym akapicie aktywnego dokumentu, a następnie usuwa pięć znaków od początku i końcu <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     [!code-vb[Trin_WordAddInDynamicControls#16](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#16)]
     [!code-csharp[Trin_WordAddInDynamicControls#16](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#16)]  
  
## <a name="recreating-the-bookmark"></a>Ponowne tworzenie zakładki  
 Można zmienić rozmiar zakładki w projektach na poziomie dokumentu, dodając nową zakładkę, która ma taką samą nazwę jak istniejącej zakładki, ale nie ma inny rozmiar.  
  
#### <a name="to-recreate-a-bookmark-in-a-document-level-project-at-design-time"></a>Aby odtworzyć zakładki w projektach na poziomie dokumentu w czasie projektowania  
  
1.  Zaznacz tekst, który ma być uwzględniony w nowym <xref:Microsoft.Office.Tools.Word.Bookmark> formantu.  
  
2.  Na **Wstaw** menu, kliknij przycisk **zakładki**.  
  
3.  W **zakładki** oknie dialogowym Wybierz nazwę zakładki, który chcesz zmienić rozmiar, a następnie kliknij przycisk **Dodaj**.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: dodawanie formantów zakładek do dokumentów programu Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)   
 [Obiekty hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md)   
 [Porady: zmiana rozmiaru formantów NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Porady: zmiana rozmiaru formantów ListObject](../vsto/how-to-resize-listobject-controls.md)   
 [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  