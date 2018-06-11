---
title: 'Wskazówki: aktualizacja wykresu w arkuszu za pomocą przycisków radiowych'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, updating using managed controls
- controls [Office development in Visual Studio], updating worksheets
- worksheets, using radio buttons
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 574c43778d5adc31afdf2e2fed02a51f9469a24f
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35258622"
---
# <a name="walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons"></a>Wskazówki: aktualizacja wykresu w arkuszu za pomocą przycisków radiowych
  W tym przewodniku przedstawiono podstawy zapewniają sposób szybkie przełączanie opcji użytkownika, za pomocą przycisków radiowych w arkuszu programu Microsoft Office Excel. W takim przypadku opcji Zmień styl wykresu.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Aby zobaczyć wynik jako ukończonego próbki, zobacz przykład formanty programu Excel w [Office development ― przykłady i wskazówki](../vsto/office-development-samples-and-walkthroughs.md).  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Dodawanie grupy przycisków radiowych do arkusza.  
  
-   Zmienianie stylu wykresu, po wybraniu opcji.  
  
> [!NOTE]  
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="add-a-chart-to-a-worksheet"></a>Dodaj wykres do arkusza  
 Można utworzyć projektu skoroszyt programu Excel, który dostosowuje istniejącego skoroszytu. W tym przewodniku będzie Dodawanie wykresu do skoroszytu, a następnie użycie tego skoroszytu w nowego rozwiązania programu Excel. Źródło danych w ramach tego przewodnika ma postać arkusza o nazwie **danych wykresu**.  
  
### <a name="to-add-the-data"></a>Aby dodać dane  
  
1.  Otwórz program Microsoft Excel.  
  
2.  Kliknij prawym przyciskiem myszy **sheet3 —** , a następnie kliknij pozycję **zmienić** menu skrótów.  
  
3.  Zmień nazwę arkusza do **danych wykresu**.  
  
4.  Dodaj następujące dane **danych wykresu** z komórki A4 jest lewy górny narożnik i E8 prawym dolnym rogu.  
  
    ||1.|K2|K3|KWARTAŁ 4|  
    |-|--------|--------|--------|--------|  
    |Zachodnie|500|550|550|600|  
    |Region Azji i Pacyfiku|600|625|675|700|  
    |Północna|450|470|490|510|  
    |Południowa|800|750|775|790|  
  
 Następnie dodaj wykres do pierwszego arkusza, aby wyświetlić dane.  
  
### <a name="to-add-a-chart-in-excel"></a>Aby dodać wykres w programie Excel  
  
1.  Na **Wstaw** karcie **wykresów** kliknij przycisk **kolumny**, a następnie kliknij przycisk **wszystkie typy wykresów**.  
  
2.  W **Wstaw wykres** okno dialogowe, kliknij przycisk **OK**.  
  
3.  Na **projekt** karcie **danych** kliknij przycisk **danych wybierz**.  
  
4.  W **wybierz źródło danych** okno dialogowe, kliknij w **zakres Chartdata** i wyczyść wszystkie wybór domyślny.  
  
5.  W **danych wykresu** arkusza, wybierz bloku komórek, który zawiera numery, które zawiera A4 w lewym górnym rogu do E8 w prawym dolnym rogu.  
  
6.  W **wybierz źródło danych** okno dialogowe, kliknij przycisk **OK**.  
  
7.  Zmienia położenie wykresu, dzięki czemu prawym górnym rogu wyrównana z komórki **E2**.  
  
8.  Zapisz plik na dysku C i nadaj jej nazwę **ExcelChart.xlsx**.  
  
9. Zakończ działanie programu Excel.  
  
## <a name="create-a-new-project"></a>Tworzenie nowego projektu  
 W tym kroku utworzysz projektu skoroszyt programu Excel na podstawie **ExcelChart** skoroszytu.  
  
### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt  
  
1.  Tworzenie projektu skoroszyt programu Excel o nazwie **Moje wykres**. W kreatorze Wybierz **Skopiuj istniejący dokument**.  
  
     Aby uzyskać więcej informacji, zobacz [porady: tworzenie projektach pakietu Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Kliknij przycisk **Przeglądaj** buttonand Przeglądaj, aby skoroszyt został utworzony we wcześniejszej części tego przewodnika.  
  
3.  Kliknij przycisk **OK**.  
  
     Visual Studio zostanie otwarty nowy skoroszyt programu Excel w Projektancie i dodaje **Moje wykres** projektu do **Eksploratora rozwiązań**.  
  
## <a name="set-properties-of-the-chart"></a>Ustawianie właściwości wykresu  
 Podczas tworzenia nowego projektu skoroszyt programu Excel, która korzysta z istniejącego skoroszytu kontrolki hosta są tworzone automatycznie dla wszystkich nazwane zakresy, listę obiektów i wykresy w skoroszycie. Można zmienić nazwę <xref:Microsoft.Office.Tools.Excel.Chart> formantu przy użyciu **właściwości** okna.  
  
### <a name="to-change-the-name-of-the-chart-control"></a>Aby zmienić nazwę formantu wykresu  
  
1.  Wybierz <xref:Microsoft.Office.Tools.Excel.Chart> kontroli w Projektancie i zmienić następujących właściwości w **właściwości** okna.  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |**Nazwa**|**dataChart**|  
    |**HasLegend**|**false**|  
  
## <a name="add-controls"></a>Dodawanie formantów  
 Tego arkusza używa przycisków radiowych umożliwić użytkownikom można szybko zmienić styl wykresu. Jednak przycisków radiowych muszą być wyłącznego — po wybraniu jednego przycisku żaden inny przycisk w grupie można wybrać w tym samym czasie. To zachowanie nie odbywa się domyślnie, po dodaniu kilka przycisków radiowych do arkusza.  
  
 Jednym ze sposobów dodać to zachowanie jest grupa przycisków radiowych w formancie użytkownika wpisz swój kod za kontrolki użytkownika, a następnie dodaj kontrolkę użytkownika w arkuszu.  
  
### <a name="to-add-a-user-control"></a>Aby dodać kontrolkę użytkownika  
  
1.  Wybierz **Moje wykres** projektu w **Eksploratora rozwiązań**.  
  
2.  Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.  
  
3.  W **Dodaj nowy element** okno dialogowe, kliknij przycisk **kontrolki użytkownika**, nazwa formantu **ChartOptions,** i kliknij przycisk **Dodaj**.  
  
### <a name="to-add-radio-buttons-to-the-user-control"></a>Aby dodać przycisków radiowych do kontrolki użytkownika  
  
1.  Kontrola użytkownika nie jest widoczne w projektancie, kliknij dwukrotnie **ChartOptions** w **Eksploratora rozwiązań**.  
  
2.  Z **formanty standardowe** karcie **przybornika**, przeciągnij **przycisk radiowy** kontroli do kontrolki użytkownika i Zmień następujące właściwości.  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |**Nazwa**|**columnChart**|  
    |**Tekst**|**Wykres kolumnowy**|  
  
3.  Dodawanie drugiego przycisku radiowego do kontrolki użytkownika i zmienić następujących właściwości.  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |**Nazwa**|**barChart**|  
    |**Tekst**|**Wykres słupkowy**|  
  
4.  Dodaj trzeci przycisku radiowego do kontrolki użytkownika i Zmień następujące właściwości.  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |**Nazwa**|**lineChart**|  
    |**Tekst**|**Wykres liniowy**|  
  
5.  Dodaj czwarty przycisku radiowego do kontrolki użytkownika i Zmień następujące właściwości.  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |**Nazwa**|**areaBlockChart**|  
    |**Tekst**|**Wykres warstwowy bloku**|  
  
 Następnie należy napisać kod, aby zaktualizować wykresu, gdy zostanie kliknięty przycisk radiowy.  
  
## <a name="change-the-chart-style-when-a-radio-button-is-selected"></a>Zmień styl wykresu, gdy przycisk radiowy zostanie wybrany  
 Teraz można dodać kod, aby zmienić styl wykresu. W tym celu Utwórz zdarzenie publiczne na kontrolki użytkownika, Dodaj właściwość można ustawić typ zaznaczenia i Utwórz program obsługi zdarzeń dla `CheckedChanged` zdarzenia każdego z przycisków radiowych.  
  
### <a name="to-create-an-event-and-property-on-a-user-control"></a>Aby utworzyć zdarzenie i właściwości na kontrolkę użytkownika  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy kontrolki użytkownika, a następnie kliknij przycisk **kod widoku**.  
  
2.  Dodaj kod, aby `ChartOptions` klasy w celu utworzenia `SelectionChanged` zdarzeń i `Selection` właściwości.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#13](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#13)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#13)]  
  
### <a name="to-handle-the-checkedchanged-event-of-the-radio-buttons"></a>Obsługa zdarzenia CheckedChanged przycisków radiowych  
  
1.  Ustaw typ wykresu w `CheckedChanged` obsługi zdarzeń `areaBlockChart` przycisk radiowy, a następnie wywołaj zdarzenie.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#14](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#14)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#14)]  
  
2.  Ustaw typ wykresu w `CheckedChanged` obsługi zdarzeń `barChart` przycisk radiowy.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#15](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#15)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#15)]  
  
3.  Ustaw typ wykresu w `CheckedChanged` obsługi zdarzeń `columnChart` przycisk radiowy.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#16](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#16)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#16)]  
  
4.  Ustaw typ wykresu w `CheckedChanged` obsługi zdarzeń `lineChart` przycisk radiowy.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#17](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#17)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#17)]  
  
5.  W języku C# należy dodać obsługę zdarzeń dla przycisków radiowych. Można dodać kod do `ChartOptions` Konstruktor poniżej wywołanie `InitializeComponent`. Aby uzyskać informacje o sposobie tworzenia procedury obsługi zdarzeń, zobacz [porady: tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#18)]  
  
## <a name="add-the-user-control-to-the-worksheet"></a>Dodaj kontrolkę użytkownika do arkusza  
 Podczas kompilowania rozwiązania nowy formant użytkownika jest automatycznie dodawany do **przybornika**. Można następnie przeciągnij formant z **przybornika** do arkusza.  
  
### <a name="to-add-the-user-control-your-worksheet"></a>Aby dodać kontrolkę użytkownika arkusza  
  
1.  Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
     **ChartOptions** użytkownika formant został dodany do **przybornika**.  
  
2.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Sheet1.vb** lub **Sheet1.cs**, a następnie kliknij przycisk **Widok projektanta**.  
  
3.  Przeciągnij **ChartOptions** kontrolować z **przybornika** w arkuszu.  
  
     Nowy formant o nazwie `my_Excel_Chart_ChartOptions1` zostanie dodany do projektu.  
  
4.  Zmień nazwę formantu **ChartOptions1**.  
  
## <a name="change-the-chart-type"></a>Zmień typ wykresu  
 Aby zmienić typ wykresu, należy utworzyć program obsługi zdarzeń, który ustawia styl w zależności od opcji wybranej w formancie użytkownika.  
  
### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-worksheet"></a>Aby zmienić typ wykresu, który jest wyświetlany w arkuszu  
  
1.  Dodaj następujące obsługi zdarzeń do `Sheet1` klasy.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#19](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#19)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#19)]  
  
2.  W języku C#, należy dodać program obsługi zdarzeń dla formantu użytkownika do <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> zdarzeń, jak pokazano poniżej. Aby uzyskać informacje o sposobie tworzenia procedury obsługi zdarzeń, zobacz [porady: tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#20)]  
  
## <a name="test-the-application"></a>Testowanie aplikacji  
 Teraz możesz przetestować Twojego skoroszytu, aby upewnić się, że wykres jest poprawnie wstawiony po wybraniu przycisku radiowego.  
  
### <a name="to-test-your-workbook"></a>Aby przetestować skoroszytu  
  
1.  Naciśnij klawisz **F5** do uruchomienia projektu.  
  
2.  Wybierz różne przycisków radiowych.  
  
3.  Upewnij się, że styl wykresu zmienia się zgodnie z wyborem.  
  
## <a name="next-steps"></a>Następne kroki  
 W tym przewodniku przedstawiono podstawy za pomocą przycisków radiowych i style wykresu w arkuszu. Poniżej przedstawiono niektóre zadania, które mogą występować:  
  
-   Wdrażanie projektu. Aby uzyskać więcej informacji, zobacz [wdrażania rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md).  
  
-   Za pomocą przycisku, aby wypełnić pole tekstowe. Aby uzyskać więcej informacji, zobacz [wskazówki: wyświetlanie tekstu w polu tekstowym w arkuszu za pomocą przycisku](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).  
  
-   Zmiana formatowania arkusza za pomocą pola wyboru. Aby uzyskać więcej informacji, zobacz [wskazówki: arkusz Zmienianie formatowania za pomocą formantów CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Wskazówki dotyczące przy użyciu programu Excel](../vsto/walkthroughs-using-excel.md)  
  
  