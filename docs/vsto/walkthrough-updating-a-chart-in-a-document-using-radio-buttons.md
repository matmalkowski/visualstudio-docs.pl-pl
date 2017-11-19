---
title: "Wskazówki: Aktualizacja wykresu w dokumencie za pomocą przycisków radiowych | Dokumentacja firmy Microsoft"
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
- documents [Office development in Visual Studio], updating using controls
- controls [Office development in Visual Studio], updating documents
ms.assetid: 56e6d1f2-65a4-41f0-aff5-f0cfd96d7185
caps.latest.revision: "60"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2d6fa02174a8b334b404a0a4ea84ee0e8089c584
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-updating-a-chart-in-a-document-using-radio-buttons"></a>Wskazówki: aktualizacja wykresu w dokumencie za pomocą przycisków radiowych
  W tym przewodniku przedstawiono sposób użycia przycisków radiowych w dostosowaniu poziomie dokumentu dla programu Microsoft Office Word umożliwić użytkownikom możliwość wybrania style wykresu w dokumencie.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Dodawanie wykresu do dokumentu w projektach na poziomie dokumentu w czasie projektowania.  
  
-   Grupowanie przycisków radiowych przez dodanie ich do kontrolki użytkownika.  
  
-   Zmienianie stylu wykresu, po wybraniu opcji.  
  
 Aby zobaczyć wynik jako ukończonego próbka, zobacz przykład formanty programu Word w [Office Development ― przykłady i wskazówki](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]lub [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Pierwszym krokiem jest utworzenie projektu dokument programu Word.  
  
#### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt  
  
1.  Tworzenie projektu dokument programu Word o nazwie **Moje opcje wykresu**. W kreatorze Wybierz **Utwórz nowy dokument**. Aby uzyskać więcej informacji, zobacz [porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio zostanie otwarty nowy dokument programu Word w Projektancie i dodaje **Moje opcje wykresu** projektu do **Eksploratora rozwiązań**.  
  
## <a name="adding-a-chart-to-the-document"></a>Dodawanie wykresu do dokumentu  
  
#### <a name="to-add-a-chart"></a>Aby dodać wykresu  
  
1.  W dokumencie programu Word, który znajduje się w projektancie programu Visual Studio na Wstążce, kliknij przycisk **Wstaw** kartę.  
  
2.  W **tekst** kliknij przycisk **Wstaw obiekt** przycisku rozwijanego, a następnie kliknij przycisk **obiektu**.  
  
     **Obiektu** zostanie otwarte okno dialogowe.  
  
3.  W **typu obiektu** listy na **Utwórz nowy** wybierz opcję **wykres programu Microsoft Graph** , a następnie kliknij przycisk **OK**.  
  
     Wykres zostanie dodany do dokumentu punkt wstawiania i **arkusz danych** zostanie wyświetlone okno z niektórych domyślnych danych.  
  
4.  Zamknij **arkusz danych** okno, aby zaakceptować wartości domyślne na wykresie, a następnie kliknij wewnątrz dokument na przeniesienie fokusu poza wykresem.  
  
5.  Kliknij prawym przyciskiem myszy wykres, a następnie kliknij przycisk **Format obiektu**.  
  
6.  Na **układu** karcie **Format obiektu** okno dialogowe, wybierz opcję **kwadratowe** i kliknij przycisk **OK**.  
  
## <a name="adding-a-user-control-to-the-project"></a>Dodawanie formantu użytkownika do projektu  
 Przyciski radiowe w dokumencie nie wykluczają domyślnie. Możesz wprowadzić je działać poprawnie przez dodanie ich do kontrolki użytkownika, a następnie pisania kodu, aby kontrolować zaznaczenia.  
  
#### <a name="to-add-a-user-control"></a>Aby dodać kontrolkę użytkownika  
  
1.  Wybierz **Moje opcje wykresu** projektu w **Eksploratora rozwiązań**.  
  
2.  Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.  
  
3.  W **Dodaj nowy element** okno dialogowe, kliknij przycisk **kontrolki użytkownika**, nazwa formantu **ChartOptions,** i kliknij przycisk **Dodaj**.  
  
#### <a name="to-add-windows-form-controls-to-the-user-control"></a>Aby dodać kontrolki formularza systemu Windows do kontrolki użytkownika  
  
1.  Kontrola użytkownika nie jest widoczne w projektancie, kliknij dwukrotnie **ChartOptions** w **Eksploratora rozwiązań**.  
  
2.  Z **formanty standardowe** karcie **przybornika**, przeciągnij pierwszy **przycisk radiowy** kontroli do kontrolki użytkownika i Zmień następujące właściwości.  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |**Nazwa**|**columnChart**|  
    |**Tekst**|**Wykres kolumnowy**|  
  
3.  Dodaj drugi **przycisk radiowy** użytkownikowi kontrolowanie i Zmień następujące właściwości.  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |**Nazwa**|**barChart**|  
    |**Tekst**|**Wykres słupkowy**|  
  
4.  Dodaj innej **przycisk radiowy** użytkownikowi kontrolowanie i Zmień następujące właściwości.  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |**Nazwa**|**lineChart**|  
    |**Tekst**|**Wykres liniowy**|  
  
5.  Dodaj czwarty **przycisk radiowy** użytkownikowi kontrolowanie i Zmień następujące właściwości.  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |**Nazwa**|**areaBlockChart**|  
    |**Tekst**|**Wykres warstwowy bloku**|  
  
## <a name="adding-references"></a>Dodawanie odwołań  
 Dostęp do wykres z kontrolki użytkownika w dokumencie, musi mieć odwołanie do zestawu Microsoft.Office.Interop.Graph w projekcie.  
  
#### <a name="to-add-a-reference-to-the-microsoftofficeinteropgraph-assembly"></a>Aby dodać odwołanie do zestawu Microsoft.Office.Interop.Graph  
  
1.  Na **projektu** menu, kliknij przycisk **Dodaj odwołanie**.  
  
     **Dodaj odwołanie** zostanie wyświetlone okno dialogowe.  
  
2.  Na **.NET** wybierz opcję **Microsoft.Office.Interop.Graph** i kliknij przycisk **OK**. Wybierz 14.0.0.0 wersji zestawu.  
  
## <a name="changing-the-chart-style-when-a-radio-button-is-selected"></a>Zmienianie stylu wykresu, po wybraniu przycisku radiowego  
 Aby przyciski działał prawidłowo, Utwórz zdarzenie publiczne na kontrolki użytkownika, Dodaj właściwość można ustawić typ zaznaczenia, a następnie utwórz procedurę `CheckedChanged` zdarzenia każdego z przycisków radiowych.  
  
#### <a name="to-create-an-event-and-property-on-a-user-control"></a>Aby utworzyć zdarzenie i właściwości na kontrolkę użytkownika  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy kontrolki użytkownika, a następnie kliknij przycisk **kod widoku**.  
  
2.  Dodaj kod, aby utworzyć `SelectionChanged` zdarzeń i `Selection` właściwości `ChartOptions` klasy.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#9)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#9](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#9)]  
  
#### <a name="to-handle-the-checkedchange-event-of-the-radio-buttons"></a>Obsługa zdarzenia CheckedChange przycisków radiowych  
  
1.  Ustaw typ wykresu w `CheckedChanged` obsługi zdarzeń `areaBlockChart` przycisk radiowy, a następnie wywołaj zdarzenie.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#10)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#10](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#10)]  
  
2.  Ustaw typ wykresu w `CheckedChanged` obsługi zdarzeń `barChart` przycisk radiowy.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#11](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#11)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#11](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#11)]  
  
3.  Ustaw typ wykresu w `CheckedChanged` obsługi zdarzeń `columnChart` przycisk radiowy.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#12](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#12)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#12](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#12)]  
  
4.  Ustaw typ wykresu w `CheckedChanged` obsługi zdarzeń `lineChart` przycisk radiowy.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#13](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#13)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#13](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#13)]  
  
5.  W języku C# należy dodać obsługę zdarzeń dla przycisków radiowych. Można dodać kod do `ChartOptions` Konstruktor poniżej wywołanie `InitializeComponent`. Aby uzyskać informacje dotyczące tworzenia procedury obsługi zdarzeń, zobacz [porady: tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#14](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#14)]  
  
## <a name="adding-the-user-control-to-the-document"></a>Dodawanie formantu użytkownika do dokumentu  
 Podczas kompilowania rozwiązania nowy formant użytkownika jest automatycznie dodawany do **przybornika**. Można następnie przeciągnij formant z **przybornika** do dokumentu.  
  
#### <a name="to-add-the-user-control-your-document"></a>Aby dodać kontrolkę użytkownika dokumentu  
  
1.  Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
     **ChartOptions** użytkownika formant został dodany do **przybornika**.  
  
2.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ThisDocument.vb** lub **ThisDocument.cs**, a następnie kliknij przycisk **Widok projektanta**.  
  
3.  Przeciągnij `ChartOptions` kontrolować z **przybornika** do dokumentu.  
  
     W **właściwości** okna, nazwa formantu, który został właśnie dodany do dokumentu `ChartOptions1`.  
  
## <a name="changing-the-chart-type"></a>Zmiana typu wykresu  
 Tworzenie procedury obsługi zdarzeń, aby zmienić typ wykresu, w zależności od opcji wybranej w formancie użytkownika.  
  
#### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-document"></a>Aby zmienić typ wykresu, który jest wyświetlany w dokumencie  
  
1.  Dodaj następujące obsługi zdarzeń do `ThisDocument` klasy.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#15](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#15)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#15](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#15)]  
  
2.  W języku C#, należy dodać program obsługi zdarzeń dla formantu użytkownika do <xref:Microsoft.Office.Tools.Word.Document.Startup> zdarzeń.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#16](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#16)]  
  
## <a name="testing-the-application"></a>Testowanie aplikacji  
 Teraz możesz przetestować dokumencie, aby upewnić się, że styl wykresu jest poprawnie aktualizowany po wybraniu przycisku radiowego.  
  
#### <a name="to-test-your-document"></a>Aby przetestować dokumentu  
  
1.  Naciśnij klawisz F5, aby uruchomić projekt.  
  
2.  Wybierz różne przycisków radiowych.  
  
3.  Upewnij się, że styl wykresu zmienia się zgodnie z wyborem.  
  
## <a name="next-steps"></a>Następne kroki  
 Poniżej przedstawiono niektóre zadania, które mogą występować:  
  
-   Za pomocą przycisku, aby wypełnić pole tekstowe. Aby uzyskać więcej informacji, zobacz [wskazówki: wyświetlanie tekstu w polu tekstowym w dokumencie za pomocą przycisku](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).  
  
-   Zmienianie formatowania, wybierając stylu z pola kombi. Aby uzyskać więcej informacji, zobacz [wskazówki: zmiana dokumentu formatowania za pomocą formantów CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki dotyczące korzystania z programu Word](../vsto/walkthroughs-using-word.md)   
 [Office Development ― przykłady i wskazówki](../vsto/office-development-samples-and-walkthroughs.md)   
 [Ograniczenia formantów formularzy systemu Windows w dokumentach pakietu Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  