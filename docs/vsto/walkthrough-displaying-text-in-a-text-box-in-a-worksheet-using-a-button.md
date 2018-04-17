---
title: 'Wskazówki: Wyświetlanie tekstu w polu tekstowym w arkuszu za pomocą przycisku | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], displaying worksheets
- worksheets, displaying text
- text boxes, displaying text in worksheets
- text [Office development in Visual Studio], text boxes
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e141618fb5b647f0cdb5341627356588df932fed
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button"></a>Wskazówki: wyświetlanie tekstu w polu tekstowym w arkuszu za pomocą przycisku
  W tym przewodniku przedstawiono podstawy za pomocą przycisków i pola tekstowe w arkuszach programu Microsoft Office Excel i tworzenie projekty programu Excel za pomocą narzędzi programowania pakietu Office w Visual Studio. Aby zobaczyć wynik jako ukończonego próbki, zobacz przykład formanty programu Excel w [Office Development ― przykłady i wskazówki](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 W tym przewodniku przedstawiono sposób:  
  
-   Dodawanie formantów do arkusza.  
  
-   Wypełnij pole tekstowe, po kliknięciu przycisku.  
  
-   Testowanie projektu.  
  
> [!NOTE]  
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 W tym kroku utworzysz projektu skoroszyt programu Excel za pomocą programu Visual Studio.  
  
#### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt  
  
1.  Tworzenie projektu skoroszyt programu Excel o nazwie **Moje przycisk Excel**. Upewnij się, że **Utwórz nowy dokument** jest zaznaczone. Aby uzyskać więcej informacji, zobacz [porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio zostanie otwarty nowy skoroszyt programu Excel w Projektancie i dodaje **Moje przycisk Excel** projektu do **Eksploratora rozwiązań**.  
  
## <a name="adding-controls-to-the-worksheet"></a>Dodawanie formantów do arkusza  
 W ramach tego przewodnika należy przycisk i pole tekstowe z pierwszego arkusza.  
  
#### <a name="to-add-a-button-and-a-text-box"></a>Aby dodać przycisk i pole tekstowe  
  
1.  Sprawdź, czy **Moje Button.xlsx Excel** skoroszyt jest otwarty w projektancie programu Visual Studio z `Sheet1` wyświetlane.  
  
2.  Z **formanty standardowe** karcie przybornika, przeciągnij <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> do `Sheet1`.  
  
3.  Z **widoku** menu, wybierz opcję **okna właściwości**.  
  
4.  Upewnij się, że **Poletekstowe1** jest widoczny w **właściwości** pola rozwijanego okna i zmień **nazwa** właściwości pola tekstowego **Wyświetlany_tekst**.  
  
5.  Przeciągnij **przycisk** kontrolować na `Sheet1` i Zmień następujące właściwości:  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |**Nazwa**|**insertText**|  
    |**Tekst**|**Wstawianie tekstu**|  
  
 Teraz można napisać kod uruchamiany, gdy przycisk zostanie kliknięty.  
  
## <a name="populating-the-text-box-when-the-button-is-clicked"></a>Wypełnianie pola tekstowego, po kliknięciu przycisku  
 Każdym kliknięciu przycisku, **Hello World!** jest dołączany do pola tekstowego.  
  
#### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Można zapisać w polu tekstowym, po kliknięciu przycisku  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Sheet1 —**, a następnie kliknij przycisk **kod widoku** menu skrótów.  
  
2.  Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń przycisku:  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#11)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#11)]  
  
3.  W języku C#, należy dodać program obsługi zdarzeń do <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> zdarzeń, jak pokazano poniżej. Aby uzyskać informacje dotyczące tworzenia procedury obsługi zdarzeń, zobacz [porady: tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#12)]  
  
## <a name="testing-the-application"></a>Testowanie aplikacji  
 Teraz możesz przetestować skoroszyt, aby upewnić się, że komunikat **Hello World!** zostanie wyświetlony w polu tekstowym, po kliknięciu przycisku.  
  
#### <a name="to-test-your-workbook"></a>Aby przetestować skoroszytu  
  
1.  Naciśnij klawisz F5, aby uruchomić projekt.  
  
2.  Kliknij przycisk.  
  
3.  Upewnij się, że **Witaj świecie!** zostanie wyświetlona w polu tekstowym.  
  
## <a name="next-steps"></a>Następne kroki  
 W tym przewodniku przedstawiono podstawy za pomocą przycisków i pola tekstowe w arkuszach programu Excel. Poniżej przedstawiono niektóre zadania, które mogą występować:  
  
-   Wdrażanie projektu. Aby uzyskać więcej informacji, zobacz [wdrażania rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md).  
  
-   Za pomocą pola wyboru, aby zmienić formatowanie. Aby uzyskać więcej informacji, zobacz [wskazówki: zmiana arkusza formatowania za pomocą formantów CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: dodawanie formantów do dokumentów pakietu Office formularzy systemu Windows](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Wskazówki dotyczące korzystania z programu Excel](../vsto/walkthroughs-using-excel.md)   
 [Ograniczenia kontrolek Windows Forms w dokumentach pakietu Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  