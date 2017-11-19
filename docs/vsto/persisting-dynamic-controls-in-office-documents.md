---
title: Utrwalanie dynamicznie formanty w dokumentach pakietu Office | Dokumentacja firmy Microsoft
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
- Office documents [Office development in Visual Studio, Windows Forms controls
- Office documents [Office development in Visual Studio, host controls
- controls [Office development in Visual Studio], persisting in the document
- Windows Forms controls [Office development in Visual Studio], persisting in the document
- documents [Office development in Visual Studio], Windows Forms controls
- documents [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], persisting in the document
ms.assetid: 200352d1-66aa-4156-9ecd-6fd8792974cd
caps.latest.revision: "38"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1e78fb90532cf75ca2e0f2a9dc6b6aa9759c75e3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="persisting-dynamic-controls-in-office-documents"></a>Przechowywanie formantów dynamicznych w dokumentach pakietu Office
  Formanty, które są dodawane w czasie wykonywania nie są zachowywane, gdy dokument lub skoroszyt jest zapisać i zamknąć. Dokładne jest różny dla kontrolki hosta i formantów formularzy systemu Windows. W obu przypadkach można dodać kod do rozwiązania, aby ponownie utworzyć formantów, gdy użytkownik ponownie otwiera dokument.  
  
 Formanty dodane do dokumentów w czasie wykonywania są nazywane *formantów dynamicznych*. Aby uzyskać więcej informacji dotyczących formantów dynamicznych, zobacz [dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="persisting-host-controls-in-the-document"></a>Utrwalanie formanty hosta w dokumencie  
 Gdy dokumentu jest zapisane, a następnie zamknięte, wszystkie formanty hosta dynamiczne są usuwane z dokumentu. Tylko podstawowy natywny obiektów pakietu Office pozostają za. Na przykład <xref:Microsoft.Office.Tools.Excel.ListObject> kontroli hosta staje się <xref:Microsoft.Office.Interop.Excel.ListObject>. Natywny obiektów pakietu Office nie są podłączone do zdarzeń formantu, hosta i nie mają funkcji wiązania danych formantu hosta.  
  
 W poniższej tabeli wymieniono natywnego obiekt pakietu Office, który jest pozostawione w dokumencie dla każdego typu kontroli hosta.  
  
|Typ kontrolki hosta|Natywny typ obiektu pakietu Office|  
|-----------------------|-------------------------------|  
|<xref:Microsoft.Office.Tools.Excel.Chart>|<xref:Microsoft.Office.Interop.Excel.Chart>|  
|<xref:Microsoft.Office.Tools.Excel.ListObject>|<xref:Microsoft.Office.Interop.Excel.ListObject>|  
|<xref:Microsoft.Office.Tools.Excel.NamedRange>|<xref:Microsoft.Office.Interop.Excel.Range>|  
|<xref:Microsoft.Office.Tools.Word.Bookmark>|<xref:Microsoft.Office.Interop.Word.Bookmark>|  
|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DropDownListContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.GroupContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PictureContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|<xref:Microsoft.Office.Interop.Word.ContentControl>|  
  
### <a name="re-creating-dynamic-host-controls-when-documents-are-opened"></a>Ponowne tworzenie formantów Dynamic Host po otwarciu dokumentów  
 Za każdym razem, gdy użytkownik otwiera dokument, można ponownie utworzyć kontrolki dynamicznej hosta zamiast istniejącego kontrolki natywne. Tworzenie formantów hosta w taki sposób, po otwarciu dokumentu symuluje środowisko, które użytkownicy mogą wymagać.  
  
 Ponownie utworzyć kontroli hosta dla programu Word, lub <xref:Microsoft.Office.Tools.Excel.NamedRange> lub <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolki hosta dla programu Excel, użyj `Add` \< *kontrolować klasy*> Metoda <xref:Microsoft.Office.Tools.Excel.ControlCollection> lub <xref:Microsoft.Office.Tools.Word.ControlCollection> obiektu. Użyj metody, która ma parametr dla obiekt natywny pakietu Office.  
  
 Na przykład, jeśli chcesz utworzyć <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolki z istniejących native hosta <xref:Microsoft.Office.Interop.Excel.ListObject> po otwarciu dokumentu, użyj <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddListObject%2A> — metoda i przekaż istniejące <xref:Microsoft.Office.Interop.Excel.ListObject>. W poniższym przykładzie kodu pokazano to w projektach na poziomie dokumentu dla programu Excel. Ten kod ponownie tworzy dynamiczny <xref:Microsoft.Office.Tools.Excel.ListObject> opartego na istniejącym <xref:Microsoft.Office.Interop.Excel.ListObject> o nazwie `MyListObject` w `Sheet1` klasy.  
  
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#6](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/Sheet1.cs#6)]
 [!code-vb[Trin_ExcelWorkbookDynamicControls#6](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/Sheet1.vb#6)]  
  
### <a name="re-creating-charts"></a>Ponowne tworzenie wykresów  
 Ponownie utworzyć <xref:Microsoft.Office.Tools.Excel.Chart> kontrolki, hosta, należy najpierw usunąć natywnego <xref:Microsoft.Office.Interop.Excel.Chart>, a następnie ponownie utwórz <xref:Microsoft.Office.Tools.Excel.Chart> za pomocą <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddChart%2A> lub <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddChart%2A> — metoda. Brak nie `Add` \< *kontrolować klasy*> metodę, która umożliwia utworzenie nowego <xref:Microsoft.Office.Tools.Excel.Chart> oparte na istniejącym <xref:Microsoft.Office.Interop.Excel.Chart>.  
  
 Jeśli nie najpierw usunąć natywnego <xref:Microsoft.Office.Interop.Excel.Chart>, a następnie utworzysz wykres drugiego, zduplikowany po ponownym utworzeniu <xref:Microsoft.Office.Tools.Excel.Chart>.  
  
## <a name="persisting-windows-forms-controls-in-documents"></a>Formanty formularzy systemu Windows utrwalanie w dokumentach  
 Po zapisaniu dokumentu i następnie zamknięte [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] automatycznie usuwa wszystkie formanty formularzy systemu Windows utworzony dynamicznie dokumentu. Jednak proces jest różny na poziomie dokumentu i projektów dodatku VSTO.  
  
 W dostosowaniach na poziomie dokumentu formantów i ich podstawowej otoki ActiveX (które są używane do hostowania formantów w dokumencie) zostały usunięte przy następnym otwarciu dokumentu. Nie są oznaki, które kontrolki były nigdy.  
  
 W dodatków VSTO kontrolki są usuwane, przy zachowaniu otoki ActiveX w dokumencie. Przy następnym otwarciu dokumentu, otoki ActiveX są widoczne. W programie Excel otoki ActiveX wyświetlanie obrazów formantów znalazły się podczas ostatniego zapisywania dokumentu. W programie Word otoki ActiveX są niewidoczne, chyba że użytkownik kliknie je, w którym to przypadku one wyświetlana linia kropkowana reprezentujący obramowania formantów. Istnieje kilka sposobów usuwania otoki ActiveX. Aby uzyskać więcej informacji, zobacz [usuwanie otoki ActiveX w dodatku](#removingActiveX).  
  
### <a name="re-creating-windows-forms-controls-when-documents-are-opened"></a>Ponowne tworzenie okien formularzy formantów podczas otwierania dokumentów  
 Można ponownie utworzyć usuniętego formanty formularzy systemu Windows, gdy użytkownik ponownie otwiera dokument. Aby to zrobić, rozwiązanie musi wykonywać następujące zadania:  
  
1.  Przechowywanie informacji dotyczących rozmiar, lokalizacja i stan formantów podczas zapisywania dokumentu lub zamknięty. W dostosowanie poziomie dokumentu można zapisać danych w pamięci podręcznej danych w dokumencie. W dodatku VSTO można zapisać tych danych z niestandardowym elementem XML w dokumencie.  
  
2.  Utwórz ponownie formantów w zdarzenie jest zgłaszane, gdy dokument jest otwarty. W projektach na poziomie dokumentu, możesz to zrobić w `Sheet`  *n*  `_Startup` lub `ThisDocument_Startup` procedury obsługi zdarzeń. W projektów dodatku VSTO można wykonać w przypadku tego programy obsługi <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> lub <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> zdarzenia.  
  
###  <a name="removingActiveX"></a>Usuwanie otoki ActiveX w dodatku  
 Po dodaniu dynamiczne formanty formularzy systemu Windows do dokumentów za pomocą dodatku VSTO uniemożliwia otoki ActiveX dla formantów znajdujących się w dokumencie przy następnym otwarciu w następujący sposób.  
  
#### <a name="removing-activex-wrappers-when-the-document-is-opened"></a>Usuwanie otoki ActiveX po otwarciu dokumentu  
 Aby usunąć wszystkie otoki ActiveX, należy wywołać metodę GetVstoObject, aby element host służący do generowania <xref:Microsoft.Office.Interop.Word.Document> lub <xref:Microsoft.Office.Interop.Excel.Workbook> reprezentujący nowo otwartego dokumentu. Na przykład, aby usunąć wszystkie otoki ActiveX z dokumentu programu Word, można wywołać metodę GetVstoObject do generowania elementu hosta dla <xref:Microsoft.Office.Interop.Word.Document> obiekt, który zostanie przekazany do programu obsługi zdarzeń dla <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> zdarzeń.  
  
 Ta procedura jest przydatna, gdy wiesz, że dokument zostanie otwarty tylko na komputerach wyposażonych w dodatku VSTO zainstalowane. Jeśli dokumentu mogą być przekazywane do innych użytkowników, którzy nie mają dodatku VSTO zainstalowany, należy rozważyć usunięcie formantów przed zamknięciem dokumentu, zamiast tego.  
  
 W poniższym przykładzie pokazano, jak wywołać metodę GetVstoObject po otwarciu dokumentu.  
  
 [!code-vb[Trin_WordAddInDynamicControls#11](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#11)]
 [!code-csharp[Trin_WordAddInDynamicControls#11](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#11)]  
  
 Mimo że GetVstoObject — metoda jest używany głównie w celu generowania nowego elementu hosta w czasie wykonywania, ta metoda także czyści wszystkie otoki ActiveX z dokumentu po raz pierwszy jest ona wywoływana dla określonego dokumentu. Aby uzyskać więcej informacji o sposobie używania GetVstoObject — metoda, zobacz [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
 Należy pamiętać, że jeśli dodatek VSTO tworzy formantów dynamicznych po otwarciu dokumentu, dodatek VSTO już wywoła GetVstoObject — metoda jako część procesu tworzenia kontrolki. Dodawanie wymaga oddzielnego wywołania do metody GetVstoObject usunąć otoki ActiveX w tym scenariuszu nie jest konieczne.  
  
#### <a name="removing-the-dynamic-controls-before-the-document-is-closed"></a>Usuwanie formantów dynamicznych przed zamknięciem dokumentu  
 Dodatek VSTO jawnie usunąć każdego dynamicznej kontroli z dokumentu przed zamknięciem dokumentu. Ta procedura jest przydatne w przypadku dokumentów, które mogą być przekazywane do innych użytkowników, którzy nie mają dodatku VSTO zainstalowane.  
  
 Poniższy przykład kodu pokazuje, jak usunąć wszystkie formanty formularzy systemu Windows z dokumentu programu Word, gdy dokument zostanie zamknięty.  
  
 [!code-vb[Trin_WordAddInDynamicControls#10](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#10)]
 [!code-csharp[Trin_WordAddInDynamicControls#10](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#10)]  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  