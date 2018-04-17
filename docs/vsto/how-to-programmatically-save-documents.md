---
title: 'Porady: programowane zapisywanie dokumentów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving
- Word [Office development in Visual Studio], saving documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 89e2a236d8755b764971b7823056edda3e944e65
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-save-documents"></a>Porady: Programowane zapisywanie dokumentów
  Istnieje kilka sposobów, aby zapisać dokumenty programu Microsoft Office Word. Można zapisać dokumentu bez zmiany nazwy dokumentu lub można zapisać dokument pod nową nazwą.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="saving-a-document-without-changing-the-name"></a>Zapisanie dokumentu bez zmiany nazwy  
  
#### <a name="to-save-the-document-associated-with-a-document-level-customization"></a>Aby zapisać dokument skojarzone z dostosowywania poziomie dokumentu  
  
1.  Wywołanie <xref:Microsoft.Office.Tools.Word.Document.Save%2A> metody <xref:Microsoft.Office.Tools.Word.Document> klasy. Aby użyć w tym przykładzie kodu, uruchom go z `ThisDocument` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#7)]  
  
#### <a name="to-save-the-active-document"></a>Aby zapisać aktywny dokument.  
  
1.  Wywołanie <xref:Microsoft.Office.Interop.Word._Document.Save%2A> metody dla aktywnego dokumentu. Aby użyć w tym przykładzie kodu, uruchom go z `ThisDocument` lub `ThisAddIn` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#8)]
     [!code-csharp[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#8)]  
  
 Jeśli nie masz pewności, czy dokument, który ma zostać zapisany jest aktywny dokument, musisz odwołuje się do niego według jego nazwy.  
  
#### <a name="to-save-a-document-specified-by-name"></a>Aby zapisać dokument określona na podstawie nazwy  
  
1.  Użyj nazwy dokumentu jako argument <xref:Microsoft.Office.Interop.Word.Documents> kolekcji. Aby użyć w tym przykładzie kodu, uruchom go z `ThisDocument` lub `ThisAddIn` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#9)]
     [!code-csharp[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#9)]  
  
## <a name="saving-a-document-with-a-new-name"></a>Zapisanie dokumentu za pomocą nowej nazwy  
 Metoda SaveAs Aby zapisać dokument pod nową nazwą. Można użyć tej metody <xref:Microsoft.Office.Tools.Word.Document> element hosta w projektach na poziomie dokumentu programu Word lub natywny <xref:Microsoft.Office.Interop.Word.Document> obiektu w przypadku projektów programu Word. Ta metoda wymaga, aby określić nową nazwę pliku, ale inne argumenty są opcjonalne.  
  
> [!NOTE]  
>  Jeśli możesz wyświetlić **SaveAs** okna dialogowego wewnątrz <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> obsługi zdarzeń `ThisDocument` i ustaw *anulować* parametr **false**, aplikacja może został nieoczekiwanie zakończony. Jeśli ustawisz *anulować* parametr **true**, wyświetlony komunikat o błędzie wskazujący, że Autosave został wyłączony.  
  
#### <a name="to-save-the-document-associated-with-a-document-level-customization-with-a-new-name"></a>Aby zapisać dokument skojarzone z dostosowanie poziomu dokument pod nową nazwą  
  
1.  Wywołanie <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> metody `ThisDocument` klasy w projekcie, przy użyciu w pełni kwalifikowana nazwa i ścieżka pliku. Jeśli plik o tej nazwie już istnieje w tym folderze, jest zastąpione w trybie dyskretnym. Aby użyć w tym przykładzie kodu, uruchom go z `ThisDocument` klasy.  
  
    > [!NOTE]  
    >  <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> Metoda zgłasza wyjątek, jeśli katalog docelowy nie istnieje lub jeśli występują inne problemy z zapisywaniem pliku. Dobrym rozwiązaniem do użycia jest **try... catch** zablokować wokół <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> metody lub wewnątrz wywołania metody.  
  
     [!code-vb[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#10)]  
  
#### <a name="to-save-a-native-document-with-a-new-name"></a>Aby zapisać natywny dokument pod nową nazwą  
  
1.  Wywołanie <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> metody <xref:Microsoft.Office.Interop.Word.Document> , który ma zostać zapisany, przy użyciu w pełni kwalifikowana nazwa i ścieżka pliku. Jeśli plik o tej nazwie już istnieje w tym folderze, jest zastąpione w trybie dyskretnym.  
  
     Poniższy przykład kodu Zapisuje aktywny dokument pod nową nazwą. Aby użyć w tym przykładzie kodu, uruchom go z `ThisDocument` lub `ThisAddIn` klasy w projekcie.  
  
    > [!NOTE]  
    >  <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> Metoda zgłasza wyjątek, jeśli katalog docelowy nie istnieje lub jeśli występują inne problemy z zapisywaniem pliku. Dobrym rozwiązaniem do użycia jest **try... catch** zablokować wokół <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> metody lub wewnątrz wywołania metody.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#10)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 W tym przykładzie kodu wymaga następujących elementów:  
  
-   Aby zapisać dokument według nazwy, dokument o nazwie NewDocument.doc musi istnieć w katalogu o nazwie Test na dysku C.  
  
-   Aby zapisać dokument pod nową nazwą, katalog o nazwie Test musi istnieć na dysku C.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: programowane zamykanie dokumentów](../vsto/how-to-programmatically-close-documents.md)   
 [Porady: programowane otwieranie istniejących dokumentów](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Element hosta dokumentu](../vsto/document-host-item.md)   
 [Parametry opcjonalne w rozwiązaniach Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  