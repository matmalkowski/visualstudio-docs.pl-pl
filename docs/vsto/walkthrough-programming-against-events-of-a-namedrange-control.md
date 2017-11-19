---
title: "Wskazówki: Programowanie w odniesieniu do zdarzeń formantu NamedRange | Dokumentacja firmy Microsoft"
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
- ranges, programming against events
- worksheets, changing cell values
- NamedRange control, events
- worksheets, events
- worksheets, automating
ms.assetid: b69676f9-23b2-4ed6-83ab-8868c3f10948
caps.latest.revision: "57"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 40076f607e66ec76aaa42ae297d22b38a6234ab0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-programming-against-events-of-a-namedrange-control"></a>Wskazówki: programowanie w odniesieniu do zdarzeń formantu NamedRange
  W tym przewodniku przedstawiono sposób dodawania <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu arkusza programu Microsoft Excel pakietu Office i programu w odniesieniu do jego zdarzeń przy użyciu narzędzi programowania pakietu Office w Visual Studio.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 W tym przewodniku przedstawiono sposób:  
  
-   Dodaj <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu do arkusza.  
  
-   Program przed <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolowanie zdarzeń.  
  
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
  
1.  Tworzenie projektu skoroszyt programu Excel o nazwie **Moje zdarzenia zakresu o nazwie**. Upewnij się, że **Utwórz nowy dokument** jest zaznaczone. Aby uzyskać więcej informacji, zobacz [porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio zostanie otwarty nowy skoroszyt programu Excel w Projektancie i dodaje **Moje zdarzenia o nazwie zakresu** projektu do **Eksploratora rozwiązań**.  
  
## <a name="adding-text-and-named-ranges-to-the-worksheet"></a>Dodawanie tekstu i nazwanych zakresów arkusza  
 Formanty hosta są rozszerzonych obiektów pakietu Office, dlatego można dodać je do dokumentu w taki sam sposób należy dodać obiekt natywny. Na przykład można dodać Excel <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu do arkusza, otwierając **Wstaw** menu i wskazujący **nazwa**i wybierając polecenie **Definiuj**. Można również dodać <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu, przeciągając je z **przybornika** do arkusza.  
  
 W tym kroku zostaną dodane dwa formanty nazwany zakres na arkuszu za pomocą **przybornika**, a następnie dodaj tekst w arkuszu.  
  
#### <a name="to-add-a-range-to-your-worksheet"></a>Aby dodać zakres do arkusza  
  
1.  Sprawdź, czy **Events.xlsx zakresu o nazwie My** skoroszyt jest otwarty w projektancie programu Visual Studio z `Sheet1` wyświetlane.  
  
2.  Z **formanty Excel** karcie przybornika, przeciągnij <xref:Microsoft.Office.Tools.Excel.NamedRange> formant w komórce **A1** w `Sheet1`.  
  
     **Dodać namedrange — formant** zostanie wyświetlone okno dialogowe.  
  
3.  Sprawdź, czy **$A$ 1** pojawia się w polu tekstowym można edytować, a ta komórka **A1** jest zaznaczone. Jeśli nie, kliknij komórkę **A1** aby go wybrać.  
  
4.  Kliknij przycisk **OK**.  
  
     Komórki **A1** staje się zakres o nazwie `namedRange1`. Nie są widoczne żadne oznaki w arkuszu, ale `namedRange1` pojawia się w **nazwa** pola (znajdujące się powyżej w arkuszu po lewej stronie) gdy komórka **A1** jest zaznaczone.  
  
5.  Dodaj inny <xref:Microsoft.Office.Tools.Excel.NamedRange> formant w komórce **B3**.  
  
6.  Sprawdź, czy **$B$ 3** pojawia się w polu tekstowym można edytować, a ta komórka **B3** jest zaznaczone. Jeśli nie, kliknij komórkę **B3** aby go wybrać.  
  
7.  Kliknij przycisk **OK**.  
  
     Komórki **B3** staje się zakres o nazwie `namedRange2`.  
  
#### <a name="to-add-text-to-your-worksheet"></a>Aby dodać tekst do arkusza  
  
1.  W komórce **A1**, wpisz następujący tekst:  
  
     **To jest przykład formantu NamedRange.**  
  
2.  W komórce **A3** (z lewej strony `namedRange2`), wpisz następujący tekst:  
  
     **Zdarzenia:**  
  
 W poniższych sekcjach zostaną pisania kodu, który wstawia tekst do `namedRange2` i modyfikuje właściwości `namedRange2` formant w odpowiedzi na <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>, <xref:Microsoft.Office.Tools.Excel.NamedRange.Change>, i <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> zdarzenia `namedRange1`.  
  
## <a name="adding-code-to-respond-to-the-beforedoubleclick-event"></a>Dodawanie kodu do odpowiadanie na zdarzenia BeforeDoubleClick  
  
#### <a name="to-insert-text-into-namedrange2-based-on-the-beforedoubleclick-event"></a>Aby wstawić tekst na na podstawie zdarzenia BeforeDoubleClick NamedRange2  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Sheet1.vb** lub **Sheet1.cs** i wybierz **kod widoku**.  
  
2.  Dodaj kod, więc `namedRange1_BeforeDoubleClick` obsługi zdarzeń wygląda podobnie do następującej:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#24)]  
  
3.  W języku C#, należy dodać obsługi zdarzeń dla nazwanego zakresu, jak pokazano w <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> zdarzenia poniżej. Aby uzyskać informacje dotyczące tworzenia procedury obsługi zdarzeń, zobacz [porady: tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#25](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#25)]  
  
## <a name="adding-code-to-respond-to-the-change-event"></a>Dodawanie kodu do odpowiadanie na zdarzenia zmiany  
  
#### <a name="to-insert-text-into-namedrange2-based-on-the-change-event"></a>Aby wstawić tekst na namedRange2 na podstawie zdarzenia zmiany  
  
1.  Dodaj kod, więc `NamedRange1_Change` obsługi zdarzeń wygląda podobnie do następującej:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#26)]  
  
    > [!NOTE]  
    >  Ponieważ dwukrotnie komórki w zakresie programu Excel przechodzi do trybu edycji, <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> zdarzenie występuje, gdy zaznaczenie zostanie przeniesiona poza zakresem, nawet jeśli wystąpił brak zmian do tekstu.  
  
## <a name="adding-code-to-respond-to-the-selectionchange-event"></a>Dodawanie kodu do odpowiadanie na zdarzenia SelectionChange  
  
#### <a name="to-insert-text-into-namedrange2-based-on-the-selectionchange-event"></a>Aby wstawić tekst na namedRange2 oparte na SelectionChange, zdarzenie  
  
1.  Dodaj kod, więc **NamedRange1_SelectionChange** obsługi zdarzeń wygląda podobnie do następującej:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#27)]  
  
    > [!NOTE]  
    >  Dwukrotnie komórki w zakresie programu Excel powoduje, że zaznaczenie, aby przenieść do zakresu, <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> zdarzenie występuje przed <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> zdarzenie.  
  
## <a name="testing-the-application"></a>Testowanie aplikacji  
 Teraz możesz przetestować skoroszyt, aby sprawdzić, że tekst opisu zdarzenia <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu są wstawiane do innego nazwany zakres momencie pojawienia się zdarzenia.  
  
#### <a name="to-test-your-document"></a>Aby przetestować dokumentu  
  
1.  Naciśnij klawisz F5, aby uruchomić projekt.  
  
2.  Umieść kursor w `namedRange1`i sprawdź, czy tekst dotyczące <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> wstawić zdarzenia i komentarze są wstawiane do arkusza.  
  
3.  Kliknij dwukrotnie wewnątrz `namedRange1`i sprawdź, czy tekst dotyczące <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> zdarzeń zostaną wstawione na czerwono kursywy w `namedRange2`.  
  
4.  Kliknij przycisk poza `namedRange1` i zanotuj, czy wystąpi zdarzenie zmiany podczas zamykania trybu edycji, nawet jeśli nie zmiany w tekście.  
  
5.  Zmień tekst wewnątrz `namedRange1`.  
  
6.  Kliknij przycisk poza `namedRange1`i sprawdź, czy tekst dotyczące <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> zdarzenie dodaje się z niebieski tekst pod `namedRange2`.  
  
## <a name="next-steps"></a>Następne kroki  
 W tym przewodniku przedstawiono podstawowe informacje o programowanie w odniesieniu do zdarzeń <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu. Poniżej przedstawiono zadania, które mogą występować:  
  
-   Wdrażanie projektu. Aby uzyskać więcej informacji, zobacz [wdrażania rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekty hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md)   
 [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)   
 [Namedrange — formant](../vsto/namedrange-control.md)   
 [Porady: zmiana rozmiaru formantów NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Porady: dodawanie formantów NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Ograniczenia programowe elementów hosta i formantów hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Porady: tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md)  
  
  