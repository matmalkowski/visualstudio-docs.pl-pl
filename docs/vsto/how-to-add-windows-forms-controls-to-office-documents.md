---
title: 'Porady: dodawanie formantów formularzy systemu Windows do dokumentów pakietu Office'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], adding
- controls [Office development in Visual Studio], Windows Forms controls
- documents [Office development in Visual Studio], Windows Forms controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6fcff642f75da15f649cc7e3ab525b4db0ac1c83
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34264550"
---
# <a name="how-to-add-windows-forms-controls-to-office-documents"></a>Porady: dodawanie formantów formularzy systemu Windows do dokumentów pakietu Office
  Formanty formularzy systemu Windows można dodać do programu Microsoft Office Excel i Microsoft Office Word dokumentów w czasie projektowania w projektach na poziomie dokumentu. W czasie wykonywania można dodawać formanty w dostosowaniach na poziomie dokumentu i w dodatkach VSTO. Na przykład można dodać <xref:Microsoft.Office.Tools.Excel.Controls.ComboBox> sterowania do arkusza, dzięki czemu użytkownicy mogą wybrać z listy opcji.  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
 W tym temacie opisano następujące zadania:  
  
-   [Dodawanie formantów w czasie projektowania](#designtime)  
  
-   [Dodawanie formantów w czasie wykonywania w projektach na poziomie dokumentu](#runtimedoclevel)  
  
-   [Dodawanie formantów w czasie wykonywania w dodatkach VSTO](#runtimeaddin)  
  
 ![łącze do wideo](../vsto/media/playvideo.gif "łącze do wideo") dla powiązanych pokaz wideo, zobacz [jak I: Dodaj formanty do dokumentu powierzchni w czasie wykonywania?](http://go.microsoft.com/fwlink/?LinkId=132782).  
  
##  <a name="designtime"></a> Dodawanie formantów w czasie projektowania  
 Istnieje kilka sposobów Dodaj formanty formularzy systemu Windows do dokumentów w projektach na poziomie dokumentu w czasie projektowania.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-drag-a-windows-forms-control-to-the-document"></a>Przeciągnij kontrolki formularza systemu Windows do dokumentu  
  
1.  Utwórz lub Otwórz project skoroszytu programu Excel lub dokumentu programu Word w Visual Studio, dzięki czemu dokumentu jest widoczny w projektancie. Aby uzyskać informacje dotyczące tworzenia projektów, zobacz [porady: tworzenie projektach pakietu Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  W **formanty standardowe** karcie **przybornika**, kontroli, które chcesz dodać kliknij i przeciągnij go do dokumentu.  
  
    > [!NOTE]  
    >  Po wybraniu formantu w programie Excel, zobaczysz **=EMBED("WinForms.Control.Host","")** w **pasek formuły**. Ten tekst jest i nie należy go usunąć.  
  
### <a name="to-draw-a-windows-forms-control-on-the-document"></a>Rysowanie formantu formularzy systemu Windows w dokumencie  
  
1.  Utwórz lub Otwórz project skoroszytu programu Excel lub dokumentu programu Word w Visual Studio, dzięki czemu dokumentu jest widoczny w projektancie. Aby uzyskać informacje dotyczące tworzenia projektów, zobacz [porady: tworzenie projektach pakietu Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  W **formanty standardowe** karcie **przybornika**, kliknij przycisk kontroli, które chcesz dodać.  
  
3.  Dokumentu kliknij w miejscu górnego lewego rogu formantu znajdował się i przeciągnij, aby miejsce prawym dolnym rogu formantu można znaleźć.  
  
     Formant został dodany do dokumentu z określonej lokalizacji i rozmiaru.  
  
    > [!NOTE]  
    >  Po wybraniu formantu w programie Excel, zobaczysz **=EMBED("WinForms.Control.Host","")** w **pasek formuły**. Ten tekst jest i nie należy go usunąć.  
  
### <a name="to-add-a-windows-forms-control-to-the-document-by-single-clicking-the-control"></a>Aby dodać kontrolkę formularzy systemu Windows do dokumentu przez pojedyncze kliknięcie formantu  
  
1.  Utwórz lub Otwórz project skoroszytu programu Excel lub dokumentu programu Word w Visual Studio, dzięki czemu dokumentu jest widoczny w projektancie. Aby uzyskać informacje dotyczące tworzenia projektów, zobacz [porady: tworzenie projektach pakietu Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  W **formanty standardowe** karcie **przybornika**, kliknij przycisk kontroli, które chcesz dodać  
  
3.  Jeden dokument, należy formantu ma zostać dodana.  
  
     Formant został dodany do dokumentu zawierającego domyślny rozmiar.  
  
    > [!NOTE]  
    >  Po wybraniu formantu w programie Excel, zobaczysz **=EMBED("WinForms.Control.Host","")** w **pasek formuły**. Ten tekst jest i nie należy go usunąć.  
  
### <a name="to-add-a-windows-forms-control-to-the-document-by-double-clicking-the-control"></a>Aby dodać kontrolkę formularzy systemu Windows do dokumentu przez dwukrotne kliknięcie formantu  
  
1.  Utwórz lub Otwórz project skoroszytu programu Excel lub dokumentu programu Word w Visual Studio, dzięki czemu dokumentu jest widoczny w projektancie. Aby uzyskać informacje dotyczące tworzenia projektów, zobacz [porady: tworzenie projektach pakietu Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  W **formanty standardowe** karcie **przybornika**, kliknij dwukrotnie formant, które chcesz dodać.  
  
     Formant został dodany do dokumentu w środkowej części dokumentu lub aktywne okienko.  
  
    > [!NOTE]  
    >  Po wybraniu formantu w programie Excel, zobaczysz **=EMBED("WinForms.Control.Host","")** w **pasek formuły**. Ten tekst jest i nie należy go usunąć.  
  
### <a name="to-add-a-windows-forms-control-to-the-document-by-pressing-the-enter-key"></a>Aby dodać kontrolkę formularzy systemu Windows do dokumentu, naciskając klawisz Enter  
  
1.  Utwórz lub Otwórz project skoroszytu programu Excel lub dokumentu programu Word w Visual Studio, dzięki czemu dokumentu jest widoczny w projektancie. Aby uzyskać informacje dotyczące tworzenia projektów, zobacz [porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  W **formanty standardowe** karcie **przybornika**, kliknij kontrolkę chcesz dodać, a następnie naciśnij klawisz **Enter** klucza.  
  
     Formant został dodany do dokumentu w środkowej części dokumentu lub aktywne okienko.  
  
    > [!NOTE]  
    >  Po wybraniu formantu w programie Excel, zobaczysz **=EMBED("WinForms.Control.Host","")** w **pasek formuły**. Ten tekst jest i nie należy go usunąć.  
  
##  <a name="runtimedoclevel"></a> Dodawanie formantów w czasie wykonywania w projektach na poziomie dokumentu  
 Formanty formularzy systemu Windows można dodać programistycznie do dokumentu w czasie wykonywania. W programie Word, należy użyć metod <xref:Microsoft.Office.Tools.Word.DocumentBase.Controls%2A> właściwość `ThisDocument` klasy. W programie Excel, użyj metody <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Controls%2A> właściwość `Sheet` *n* klasy. Każda metoda ma kilka przeciążeń, które można określić lokalizacji formantu na różne sposoby.  
  
 Po dodaniu formantu formularzy systemu Windows do dokumentów w czasie wykonywania formantu nie jest trwały dokumentu, gdy dokument zostanie zamknięty. Kontrolki można odtworzyć przy następnym otwarciu dokumentu. Aby uzyskać więcej informacji, zobacz [dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
### <a name="to-add-a-windows-forms-control-at-runtime"></a>Aby dodać kontrolkę formularzy systemu Windows w czasie wykonywania  
  
1.  Metoda ma nazwę Dodaj\<*kontrolować klasy*> (gdzie *kontrolować klasy* jest nazwą klasy formantu formularzy systemu Windows, który chcesz dodać, takich jak <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>).  
  
     Poniższy przykładowy kod przedstawia sposób dodawania <xref:Microsoft.Office.Tools.Excel.Controls.Button> do komórki **C5** z `Sheet1` w projektach na poziomie dokumentu dla programu Excel.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#4)]  
  
##  <a name="runtimeaddin"></a> Dodawanie formantów w czasie wykonywania w dodatkach VSTO  
 Formanty formularzy systemu Windows można dodać programistycznie do otwartego dokumentu w czasie wykonywania. Po pierwsze Generowanie elementu hosta, który jest oparty na otwartego dokumentu lub arkusza. Następnie w programie Word, należy użyć metody <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> właściwość nowego elementu host. W programie Excel, użyj metody <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> właściwość nowego elementu host. Każda metoda ma kilka przeciążeń, które można określić lokalizacji formantu na różne sposoby.  
  
 Po dodaniu formantu formularzy systemu Windows do dokumentów w czasie wykonywania formantu nie jest trwały dokumentu, gdy dokument zostanie zamknięty. Kontrolki można odtworzyć przy następnym otwarciu dokumentu. Aby uzyskać więcej informacji, zobacz [dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Aby uzyskać więcej informacji na temat generowania elementów hosta w projektów dodatku VSTO zobacz [dokumentów rozszerzania programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
### <a name="to-add-a-windows-forms-control-at-runtime"></a>Aby dodać kontrolkę formularzy systemu Windows w czasie wykonywania  
  
1.  Metoda ma nazwę Dodaj\<*kontrolować klasy*> (gdzie *kontrolować klasy* jest nazwą klasy formantu formularzy systemu Windows, który chcesz dodać, takich jak <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>).  
  
    > [!NOTE]  
    >  W dodatku VSTO projektów przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później, należy dodać odwołanie do *Microsoft.Office.Tools.Excel.v4.0.Utilities.dll* lub *Microsoft.Office.Tools.Word.v4.0.Utilities.dll* zestawu w celu uzyskania dostępu do dodawania\<*kontrolować klasy*> metody.  
  
     Poniższy przykładowy kod przedstawia sposób dodawania <xref:Microsoft.Office.Tools.Word.Controls.Button> na pierwszym akapicie aktywnego dokumentu przy użyciu dodatku VSTO programu Word.  
  
     [!code-vb[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#7)]
     [!code-csharp[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#7)]  
  
## <a name="see-also"></a>Zobacz także  
 [Formanty formularzy systemu Windows na przegląd dokumentów pakietu Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Porady: zmiana rozmiaru formantów w komórkach arkusza](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [Obiekty hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md)   
 [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)  
  