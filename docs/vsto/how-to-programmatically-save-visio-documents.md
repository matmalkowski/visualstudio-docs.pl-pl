---
title: 'Porady: programowane zapisywanie dokumentów programu Visio | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving Visio documents
- Visio [Office development in Visual Studio], saving Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7a98ff5a7b7df6e2e609ac2d3bf89d7fd4b23648
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-save-visio-documents"></a>Porady: Programowane zapisywanie dokumentów programu Visio
  Istnieje kilka sposobów zapisywania dokumentów Microsoft Office Visio:  
  
-   Zapisz zmiany w istniejącego dokumentu.  
  
-   Zapisz nowy dokument, lub zapisać dokument pod nową nazwą.  
  
-   Zapisz dokument z określonymi argumentami.  
  
 Aby uzyskać więcej informacji, zobacz dokumentację referencyjną VBA, aby uzyskać [Microsoft.Office.Interop.Visio.Document.Save](https://msdn.microsoft.com/library/office/ff766478.aspx) metody [Microsoft.Office.Interop.Visio.Document.SaveAs](https://msdn.microsoft.com/library/office/ff765824.aspx) — metoda i [ Microsoft.Office.Interop.Visio.Document.SaveAsEx](https://msdn.microsoft.com/library/office/ff768149.aspx) metody.  
  
## <a name="saving-an-existing-document"></a>Zapisywanie istniejącego dokumentu  
  
#### <a name="to-save-a-document"></a>Aby zapisać dokument  
  
-   Wywołaj metodę Microsoft.Office.Interop.Visio.Document.Save klasy Microsoft.Office.Tools.Visio.Document dokumentu, który został wcześniej zapisany.  
  
     Aby użyć w tym przykładzie kodu, uruchom go z `ThisAddIn` klasy w projekcie.  
  
    > [!NOTE]  
    >  Metoda Microsoft.Office.Interop.Visio.Document.Save zgłasza wyjątek, jeśli nowy dokument programu Visio nie został jeszcze zapisany.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#11)]  
  
## <a name="saving-a-document-with-a-new-name"></a>Zapisanie dokumentu za pomocą nowej nazwy  
 Użyj metody Microsoft.Office.Interop.Visio.Document.SaveAs Aby zapisać nowy dokument lub dokument, który ma nową nazwę. Ta metoda wymaga, aby określić nową nazwę pliku.  
  
#### <a name="to-save-the-active-visio-document-with-a-new-name"></a>Aby zapisać pod nową nazwą aktywny dokument programu Visio  
  
-   Wywołanie metody Microsoft.Office.Interop.Visio.Document.SaveAs Microsoft.Office.Tools.Visio.Document, który ma zostać zapisany przy użyciu w pełni kwalifikowaną ścieżkę, łącznie z nazwą pliku. Jeśli plik o tej nazwie już istnieje w tym folderze, jest zastąpione w trybie dyskretnym.  
  
     Aby użyć w tym przykładzie kodu, uruchom go z `ThisAddIn` klasy w projekcie.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#10)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#10)]  
  
## <a name="saving-a-document-with-a-new-name-and-specified-arguments"></a>Zapisanie dokumentu z nową nazwą i określonych argumentów  
 Użyj metody Microsoft.Office.Interop.Visio.Document.SaveAsEx, aby zapisać dokument pod nową nazwą, a następnie określ argumenty mające zastosowanie do zastosowania w dokumencie.  
  
#### <a name="to-save-document-with-a-new-name-and-specified-arguments"></a>Aby zapisać dokument z nową nazwą i określonych argumentów  
  
-   Wywołanie metody Microsoft.Office.Interop.Visio.Document.SaveAsEx Microsoft.Office.Tools.Visio.Document, który ma zostać zapisany przy użyciu w pełni kwalifikowaną ścieżkę, łącznie z nazwą pliku. Jeśli plik o tej nazwie już istnieje w tym folderze, zostanie zgłoszony wyjątek.  
  
     Poniższy przykład kodu Zapisuje aktywny dokument pod nową nazwą, oznacza dokument w trybie tylko do odczytu i zawiera dokument w listy ostatnio używanych dokumentów. Aby użyć w tym przykładzie kodu, uruchom go z `ThisAddIn` klasy w projekcie.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#12)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 W tym przykładzie kodu wymaga następujących elementów:  
  
-   Aby zapisać dokument, który ma nową nazwę, katalog o nazwie `Test` musi znajdować się w folderze Moje dokumenty (dla systemu Windows XP i starszych) lub w folderze dokumenty (dla systemu Windows Vista).  
  
## <a name="see-also"></a>Zobacz też  
 [Rozwiązania programu Visio](../vsto/visio-solutions.md)   
 [Model obiektu Visio ― omówienie](../vsto/visio-object-model-overview.md)   
 [Porady: programowane tworzenie nowych dokumentów programu Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Porady: programowane otwieranie dokumentów Visio](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Porady: programowane zamykanie dokumentów Visio](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Instrukcje: Programowe drukowanie dokumentów programu Visio](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  