---
title: 'Wskazówki: Zbieranie danych za pomocą formularza systemu Windows'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], Windows Forms
- Windows Forms [Office development in Visual Studio], collecting data
- forms [Office development in Visual Studio], walkthroughs
- worksheets [Office development in Visual Studio], collecting data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ba91d579f8ca9bb4909a601069f74c092b0f456c
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34845564"
---
# <a name="walkthrough-collect-data-by-using-a-windows-form"></a>Wskazówki: Zbieranie danych za pomocą formularza systemu Windows
  W tym przewodniku pokazano, jak otworzyć formularza systemu Windows z dostosowywania poziomie dokumentu dla programu Microsoft Office Excel, zbiera informacje o użytkowniku i zapisać te informacje w komórce arkusza.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Mimo że w tym przewodniku zastosowano specjalnie projekt poziomie dokumentu dla programu Excel, koncepcje dowodzą wskazówki mają zastosowanie do innych projektów pakietu Office.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
> [!NOTE]  
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="create-a-new-project"></a>Tworzenie nowego projektu  
 Pierwszym krokiem jest utworzenie projektu skoroszyt programu Excel.  
  
### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt  
  
1.  Tworzenie projektu skoroszyt programu Excel o nazwie **WinFormInput**i wybierz **Utwórz nowy dokument** w kreatorze. Aby uzyskać więcej informacji, zobacz [porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio zostanie otwarty nowy skoroszyt programu Excel w Projektancie i dodaje **WinFormInput** projektu do **Eksploratora rozwiązań**.  
  
## <a name="add-a-namedrange-control-to-the-worksheet"></a>Dodawanie formantu NamedRange do arkusza  
  
### <a name="to-add-a-named-range-to-sheet1"></a>Aby dodać nazwany zakres na arkuszu 1  
  
1.  Zaznacz komórkę **A1** na `Sheet1`.  
  
2.  W **nazwa** wpisz **formInput**.  
  
     **Nazwa** pole znajduje się na lewym pasku formuły, nad kolumny **A** arkusza.  
  
3.  Naciśnij klawisz **wprowadź**.  
  
     A <xref:Microsoft.Office.Tools.Excel.NamedRange> formant został dodany do komórki **A1**. Nie są widoczne żadne oznaki w arkuszu, ale **formInput** pojawia się w **nazwa** pola (powyżej arkusza z lewej strony) i w **właściwości** okna po komórki **A1** jest zaznaczone.  
  
## <a name="add-a-windows-form-to-the-project"></a>Dodaj do projektu formularza systemu Windows  
 Tworzenie formularza systemu Windows, aby monitować użytkownika o informacje.  
  
### <a name="to-add-a-windows-form"></a>Aby dodać formularza systemu Windows  
  
1.  Wybierz projekt **WinFormInput** w **Eksploratora rozwiązań**.  
  
2.  Na **projektu** menu, kliknij przycisk **dodać formularza systemu Windows**.  
  
3.  Nazwa formularza **GetInputString.vb** lub **GetInputString.cs**, a następnie kliknij przycisk **Dodaj**.  
  
     Nowy formularz zostanie otwarty w projektancie.  
  
4.  Dodaj <xref:System.Windows.Forms.TextBox> i <xref:System.Windows.Forms.Button> do formularza.  
  
5.  Kliknij przycisk, Znajdź właściwość **tekst** w **właściwości** okna i zmień tekst, który **OK**.  
  
 Następnie dodaj kod, aby `ThisWorkbook.vb` lub `ThisWorkbook.cs` do zbierania informacji użytkownika.  
  
## <a name="display-the-windows-form-and-collecting-information"></a>Wyświetlenie formularza systemu Windows i zbieranie informacji  
 Utwórz wystąpienie `GetInputString` formularza systemu Windows i wyświetl ją, a następnie wpisz informacje o użytkowniku w komórce w arkuszu.  
  
#### <a name="to-display-the-form-and-collect-information"></a>Wyświetlenie formularza i zbierać informacje  
  
1.  Kliknij prawym przyciskiem myszy **ThisWorkbook.vb** lub **ThisWorkbook.cs** w **Eksploratora rozwiązań**, a następnie kliknij przycisk **kod widoku**.  
  
2.  W <xref:Microsoft.Office.Tools.Excel.Workbook.Open> obsługi zdarzeń `ThisWorkbook`, Dodaj następujący kod, aby zadeklarować zmienną formularza `GetInputString` , a następnie wyświetlenie formularza.  
  
    > [!NOTE]  
    >  W języku C#, należy dodać program obsługi zdarzeń, jak pokazano w <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> zdarzenia poniżej. Aby uzyskać informacje dotyczące tworzenia procedury obsługi zdarzeń, zobacz [porady: tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingCollectingData#1](../vsto/codesnippet/CSharp/WinFormInputCS/ThisWorkbook.cs#1)]
     [!code-vb[Trin_VstcoreProgrammingCollectingData#1](../vsto/codesnippet/VisualBasic/WinFormInput/ThisWorkbook.vb#1)]  
  
3.  Utwórz metodę o nazwie `WriteStringToCell` który zapisuje tekst do nazwanego zakresu. Ta metoda jest wywoływana z formularza i danych wejściowych użytkownika są przekazywane do <xref:Microsoft.Office.Tools.Excel.NamedRange> kontroli, `formInput`, w komórce **A1**.  
  
     [!code-csharp[Trin_VstcoreProgrammingCollectingData#2](../vsto/codesnippet/CSharp/WinFormInputCS/ThisWorkbook.cs#2)]
     [!code-vb[Trin_VstcoreProgrammingCollectingData#2](../vsto/codesnippet/VisualBasic/WinFormInput/ThisWorkbook.vb#2)]  
  
 Następnie dodaj kod do formularza w celu obsługi kliknięcia przycisku zdarzeń.  
  
## <a name="send-information-to-the-worksheet"></a>Wyślij informacje do arkusza  
  
### <a name="to-send-information-to-the-worksheet"></a>Przesyłanie informacji do arkusza  
  
1.  Kliknij prawym przyciskiem myszy **GetInputString** w **Eksploratora rozwiązań**, a następnie kliknij przycisk **Widok projektanta**.  
  
2.  Kliknij dwukrotnie przycisk, aby otworzyć plik kodu przy użyciu przycisku <xref:System.Windows.Forms.Control.Click> dodać obsługi zdarzeń.  
  
3.  Dodaj kod, aby program obsługi zdarzeń, aby pobrać dane wejściowe z pola tekstowego, wysłać funkcję `WriteStringToCell`, a następnie zamknij formularz.  
  
     [!code-csharp[Trin_VstcoreProgrammingCollectingData#3](../vsto/codesnippet/CSharp/WinFormInputCS/GetInputString.cs#3)]
     [!code-vb[Trin_VstcoreProgrammingCollectingData#3](../vsto/codesnippet/VisualBasic/WinFormInput/GetInputString.vb#3)]  
  
## <a name="test"></a>Test  
 Teraz możesz uruchomić projekt. Pojawi się formularza systemu Windows, a dane wejściowe w arkuszu.  
  
### <a name="to-test-your-workbook"></a>Aby przetestować skoroszytu  
  
1.  Naciśnij klawisz **F5** do uruchomienia projektu.  
  
2.  Upewnij się, że zostanie wyświetlony formularz systemu Windows.  
  
3.  Typ **Hello World** w polu tekstowym, a następnie kliknij przycisk **OK**.  
  
4.  Upewnij się, że **Hello World** pojawia się w komórce **A1** arkusza.  
  
## <a name="next-steps"></a>Następne kroki  
 W tym przewodniku przedstawiono podstawy przedstawiający formularza systemu Windows i przekazywanie danych do arkusza. Inne zadania, które może być konieczne wykonanie obejmują:  
  
-   Formanty formularzy systemu Windows w skoroszycie programu Excel lub dokumentu programu Word. Aby uzyskać więcej informacji, zobacz [formanty formularzy systemu Windows na przegląd dokumentów pakietu Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
-   Zmodyfikuj interfejsu użytkownika aplikacji z dostosowywania poziomie dokumentu lub dodatku VSTO dla pakietu Microsoft Office. Aby uzyskać więcej informacji, zobacz [dostosowywania interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Opracowywania rozwiązań pakietu Office](../vsto/developing-office-solutions.md)   
 [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)   
 [Program dodatków VSTO](../vsto/programming-vsto-add-ins.md)   
 [Dostosowywanie na poziomie dokumentu programu](../vsto/programming-document-level-customizations.md)   
 [Wskazówki dotyczące przy użyciu programu Word](../vsto/walkthroughs-using-word.md)   
 [Wskazówki dotyczące przy użyciu programu Excel](../vsto/walkthroughs-using-excel.md)  
  
  