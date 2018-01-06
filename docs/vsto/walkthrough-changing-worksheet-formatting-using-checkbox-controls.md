---
title: "Wskazówki: Zmiana formatowania arkusza za pomocą formantów CheckBox | Dokumentacja firmy Microsoft"
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
- worksheets, changing formatting using managed controls
- worksheets, check box controls
- controls [Office development in Visual Studio], adding to worksheets
ms.assetid: 4be79613-50a0-428e-9816-aadbc098272a
caps.latest.revision: "70"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: e1729a7921f72df07439261cb054fe30770b24d9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-changing-worksheet-formatting-using-checkbox-controls"></a>Wskazówki: zmiana formatowania arkusza za pomocą formantów CheckBox
  W tym przewodniku przedstawiono podstawowe do Zmienianie formatowania za pomocą pola wyboru w arkuszu programu Microsoft Office Excel. Użyjesz narzędzi programowania pakietu Office w Visual Studio do tworzenia i Dodaj kod do projektu. Aby zobaczyć wynik jako ukończonego próbki, zobacz przykład formanty programu Excel w [Office Development ― przykłady i wskazówki](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 W tym przewodniku przedstawiono sposób:  
  
-   Dodawanie tekstu i formantów do arkusza.  
  
-   Wybrano opcję formatowania tekstu.  
  
-   Testowanie projektu.  
  
> [!NOTE]  
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)]lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 W tym kroku utworzysz projektu skoroszyt programu Excel za pomocą programu Visual Studio.  
  
#### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt  
  
1.  Tworzenie projektu skoroszyt programu Excel o nazwie **Moje formatowania programu Excel**. Upewnij się, że **Utwórz nowy dokument** jest zaznaczone. Aby uzyskać więcej informacji, zobacz [porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio zostanie otwarty nowy skoroszyt programu Excel w Projektancie i dodaje **Moje formatowania programu Excel** projektu do **Eksploratora rozwiązań**.  
  
## <a name="adding-text-and-controls-to-the-worksheet"></a>Dodawanie tekstu i formantów do arkusza  
 W ramach tego przewodnika należy trzy <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> kontrolek i tekst w <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu.  
  
#### <a name="to-add-three-check-boxes"></a>Aby dodać trzy pola wyboru  
  
1.  Sprawdź, czy skoroszyt jest otwarty w projektancie programu Visual Studio i że `Sheet1` jest otwarty.  
  
2.  Z **formanty standardowe** karcie **przybornika**, przeciągnij <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> formantu do lub w jego pobliżu komórki **B2** w **Sheet1 —**.  
  
3.  Z **widoku** menu, wybierz opcję **właściwości** okna.  
  
4.  Upewnij się, że **pole wyboru 1** jest widoczny w polu listy Nazwa obiektu z **właściwości** okna i Zmień następujące właściwości:  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |**Nazwa**|**applyBoldFont**|  
    |**Tekst**|**Bold**|  
  
5.  Przeciągnij drugiego pola wyboru lub w jego pobliżu komórki **B4** i Zmień następujące właściwości:  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |**Nazwa**|**applyItalicFont**|  
    |**Tekst**|**Kursywa**|  
  
6.  Przeciągnij trzecie pole wyboru lub w jego pobliżu komórki **B6** i Zmień następujące właściwości:  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |**Nazwa**|**applyUnderlineFont**|  
    |**Tekst**|**Podkreślenie**|  
  
7.  Zaznacz wszystkie trzy pola wyboru kontrolki, przytrzymując klawisz CTRL.  
  
8.  W grupie rozmieszczanie kartę Format w programie Excel kliknij **Wyrównaj**, a następnie kliknij przycisk **Wyrównaj do lewej**.  
  
     Po lewej stronie w miejscu pierwszego formantu wybranego wyrównania formanty trzy pola wyboru.  
  
     Następnie możesz przeciągnąć <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu w arkuszu.  
  
    > [!NOTE]  
    >  Można również dodać <xref:Microsoft.Office.Tools.Excel.NamedRange> sterowania, wpisując **textFont** do **nazwa** pole.  
  
#### <a name="to-add-text-to-a-namedrange-control"></a>Aby dodać tekst formantu NamedRange  
  
1.  Z **formanty Excel** karcie przybornika, przeciągnij <xref:Microsoft.Office.Tools.Excel.NamedRange> formant w komórce **B9**.  
  
2.  Sprawdź, czy **$B$ 9** pojawia się w polu tekstowym można edytować, a ta komórka **B9** jest zaznaczone. Jeśli nie, kliknij komórkę **B9** aby go wybrać.  
  
3.  Kliknij przycisk **OK**.  
  
4.  Komórki **B9** staje się zakres o nazwie `NamedRange1`.  
  
     Nie są widoczne żadne oznaki w arkuszu, ale `NamedRange1` pojawia się w **nazwa** (powyżej arkusza po lewej stronie) gdy komórka **B9** jest zaznaczone.  
  
5.  Upewnij się, że **NamedRange1** jest widoczny w polu listy Nazwa obiektu z **właściwości** okna i Zmień następujące właściwości:  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |**Nazwa**|**textFont**|  
    |**Wartość2**|**Kliknij pole wyboru, aby zmienić formatowanie ten tekst.**|  
  
 Następnie należy napisać kod do formatowania tekstu, gdy opcja jest zaznaczona.  
  
## <a name="formatting-the-text-when-an-option-is-selected"></a>Formatowanie tekstu gdy opcja jest zaznaczona.  
 W tej sekcji zostanie napisać kod, aby, gdy użytkownik wybierze opcję formatowania, format tekstu w arkuszu zostanie zmieniona.  
  
#### <a name="to-change-formatting-when-a-check-box-is-selected"></a>Aby zmienić formatowanie, gdy pole wyboru jest zaznaczone  
  
1.  Kliknij prawym przyciskiem myszy **Sheet1 —**, a następnie kliknij przycisk **kod widoku** menu skrótów.  
  
2.  Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń `applyBoldFont` pola wyboru:  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#7)]  
  
3.  Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń `applyItalicFont` pola wyboru:  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#8)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#8)]  
  
4.  Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń `applyUnderlineFont` pola wyboru:  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#9)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#9)]  
  
5.  W języku C#, należy dodać obsługę zdarzeń dla pola wyboru, aby <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> zdarzeń, jak pokazano poniżej. Aby uzyskać informacje dotyczące tworzenia procedury obsługi zdarzeń, zobacz [porady: tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#10)]  
  
## <a name="testing-the-application"></a>Testowanie aplikacji  
 Teraz możesz przetestować skoroszytu, aby upewnić się, że tekst jest prawidłowo sformatowana, zaznacz lub usuń zaznaczenie pola wyboru.  
  
#### <a name="to-test-your-workbook"></a>Aby przetestować skoroszytu  
  
1.  Naciśnij klawisz F5, aby uruchomić projekt.  
  
2.  Wybierz lub wyczyść pole wyboru.  
  
3.  Upewnij się, że tekst jest prawidłowo sformatowany.  
  
## <a name="next-steps"></a>Następne kroki  
 W tym przewodniku przedstawiono podstawowe informacje o użyciu pola wyboru i formatowanie tekstu w arkuszach programu Excel. Poniżej przedstawiono niektóre zadania, które mogą występować:  
  
-   Wdrażanie projektu. Aby uzyskać więcej informacji, zobacz [wdrażania rozwiązania do pakietu Office za pomocą technologii ClickOnce za pomocą](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
-   Za pomocą przycisku, aby wypełnić pole tekstowe. Aby uzyskać więcej informacji, zobacz [wskazówki: wyświetlanie tekstu w polu tekstowym w arkuszu za pomocą przycisku](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki dotyczące korzystania z programu Excel](../vsto/walkthroughs-using-excel.md)   
 [Namedrange — formant](../vsto/namedrange-control.md)   
 [Ograniczenia kontrolek Windows Forms w dokumentach pakietu Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  