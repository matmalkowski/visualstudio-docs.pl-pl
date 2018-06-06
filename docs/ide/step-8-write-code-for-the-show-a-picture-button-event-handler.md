---
title: 'Krok 8: Wpisywanie kodu dla programu obsługi zdarzeń przycisk obrazu'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 07f4ec00-cda4-42f4-98bb-37edc7167de7
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dc9bc3e5b0c3a61e911f7e49395f940ac07e2548
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34748607"
---
# <a name="step-8-write-code-for-the-show-a-picture-button-event-handler"></a>Krok 8: Wpisywanie kodu dla programu obsługi zdarzeń przycisk obrazu
W tym kroku należy **Pokaż obraz** przycisk pracy w następujący sposób:

-   Po wybraniu tego przycisku zostanie otwarty program <xref:System.Windows.Forms.OpenFileDialog> pole.

-   Jeśli użytkownik otwiera plik obrazu, powoduje wyświetlenie tego obrazu w <xref:System.Windows.Forms.PictureBox>.

 IDE ma zaawansowane narzędzie IntelliSense, która ułatwia pisanie kodu. Po wprowadzeniu kodu IDE otwiera okno z sugerowanych zakończeń częściowe wyrazy, które należy wprowadzić. Próbuje określić, co chcesz zrobić dalej i automatycznie przejdzie do ostatniego elementu, który możesz wybrać z listy. Można użyć w górę lub strzałkę w dół, aby przenieść na liście, lub można zachować wpisywanie listy, aby ograniczyć zakres pozycji. Po wyświetleniu wybór należy wybrać **kartę** klucz, aby go wybrać. Alternatywnie możesz zignorować sugestii, jeśli nie są wymagane.

 ![łącze do wideo](../data-tools/media/playvideo.gif)wersję wideo tego tematu, zobacz [samouczek 1: Tworzenie podglądu obrazów w języku Visual Basic - 4 wideo](http://go.microsoft.com/fwlink/?LinkId=205215) lub [samouczek 1: Tworzenie podglądu obrazów w języku C# — 4 wideo](http://go.microsoft.com/fwlink/?LinkId=205203). Tych klipów wideo korzysta z wcześniejszej wersji programu Visual Studio, dlatego są niewielkie różnice w niektórych poleceń menu i inne elementy interfejsu użytkownika. Jednak koncepcje i procedury działają podobnie w bieżącej wersji programu Visual Studio.

## <a name="to-write-code-for-the-show-a-picture-button-event-handler"></a>Pisanie kodu dla programu obsługi zdarzenia obrazu przycisku

1.  Przejdź do **Projektant formularzy systemu Windows** i kliknij dwukrotnie **Pokaż obraz** przycisku. IDE natychmiast przechodzi do projektanta kodu i przesuwa kursor, znajduje się wewnątrz `showButton_Click()` metody dodanego wcześniej.

2.  Typ `i` w pustym wierszu w nawiasach klamrowych dwóch `{ }`. (W języku Visual Basic, wpisz w pustym wierszu między `Private Sub...` i `End Sub`.) **IntelliSense** zostanie otwarte okno, jak pokazano na poniższej ilustracji.

     ![IntelliSense z Visual C&#35; kod](../ide/media/express_ifintellisense.png)
**IntelliSense** z kodu Visual C#

3.  **IntelliSense** okna powinna wyróżnianie słowo `if`. (Jeśli nie, wprowadź jedną małą literę `f`, i będzie ono.) Zwróć uwagę, jak trochę *tooltip* obok pola **IntelliSense** z opisu, zostanie wyświetlone okno **fragment kodu dotyczący if — instrukcja**. (W języku Visual Basic, etykietkę narzędzia również stwierdza, że jest fragment, ale treść nieco inne.) Aby używać tego fragment, więc należy wybrać **kartę** klawisz, aby wstawić `if` w kodzie. Następnie wybierz pozycję **kartę** klucz ponownie `if` fragment kodu. (W przypadku wybrania w innym miejscu i **IntelliSense** okna zniknął, backspace za pośrednictwem `i` i ponownie, wpisz i **IntelliSense** ponownie zostanie otwarte okno.)

     ![Visual C&#35; kod](../ide/media/express_highlighttrue.png) kodu Visual C#

4.  Następnie użyj IntelliSense, aby wprowadzić więcej kod, aby otworzyć **Otwieranie pliku** okno dialogowe. Jeśli użytkownik wybrał **OK** przycisku, element PictureBox ładuje plik wybranego użytkownika. Poniższe kroki pokazują, jak wprowadzić kod i wiele kroków, ale jest kilka naciśnięcia klawiszy:

    1.  Rozpoczynać się od tekstu zaznaczonego **true** we fragmencie. Typ `op` go zastąpić. (W języku Visual Basic rozpoczynać się od zakończenia początkowej, dlatego należy wpisać `Op`.)

    2.  **IntelliSense** otwiera się okno i wyświetla **openFileDialog1**. Wybierz **kartę** klucz, aby go wybrać. (W języku Visual Basic, rozpoczyna się od zakończenia początkowej, tak aby widoczne **OpenFileDialog1**. Upewnij się, że **OpenFileDialog1** wybrano.)

         Aby dowiedzieć się więcej o `OpenFileDialog`, zobacz [OpenFileDialog](http://msdn.microsoft.com/library/system.windows.forms.openfiledialog.aspx).

    3.  Wpisz kropkę (`.`) (wielu programistów wywołać to kropkę.) Ponieważ wpisany prawo kropkę po **openFileDialog1**, **IntelliSense** okno wypełnione wszystkie **OpenFileDialog** składnika właściwości i metody. Są to te same właściwości, które są widoczne w **właściwości** okna, jeśli został wybrany **Projektant formularzy systemu Windows**. Możesz również metody określające składnik do wykonywania czynności (np. Czy otworzyć okno dialogowe).

        > [!NOTE]
        >  **IntelliSense** okna można wyświetlić zarówno właściwości i metody. Aby ustalić, co jest wyświetlane, przyjrzeć się ikony po lewej stronie każdego elementu w **IntelliSense** okna. Zostanie wyświetlony obraz bloku obok każdej metody i obraz klucza (lub klucza) obok każdej właściwości. Istnieje również ikonę błyskawicy obok każdego zdarzenia. Te obrazy są wyświetlane w następujący sposób.

         ![Ikona metody](../ide/media/express_iconmethod.png)
**metody** ikony

         ![Ikona właściwości](../ide/media/express_iconproperty.png)
**właściwości** ikony

         ![Ikona zdarzenie](../ide/media/express_iconevent.png)
**zdarzeń** ikony

    4.  Wpisywania `ShowDialog` (wielkość liter jest bez znaczenia funkcji IntelliSense). `ShowDialog()` Opisano metody **Otwórz plik** okno dialogowe. Po oknie ujawniło **ShowDialog**, wybierz **kartę** klucza. Można wyróżnić "ShowDialog" i wybierz **F1** klawisz, aby uzyskać pomoc dotyczącą go.

         Aby dowiedzieć się więcej o `ShowDialog()` metody, zobacz [metody ShowDialog](http://msdn.microsoft.com/library/c7ykbedk.aspx).

    5.  Jeśli używasz metody w formancie lub składnikiem (nazywane *podczas wywoływania metody*), należy dodać nawiasów. Dlatego należy wprowadzić nawiasy otwierające i zamykające natychmiast po "g" w `ShowDialog`: `()` powinna wyglądać tak jak "openFileDialog1.ShowDialog()".

        > [!NOTE]
        >  Metody są ważną częścią programu, a ten samouczek pokazuje, kilka sposobów użycia metod. Można wywołać metody składnika stwierdzić, aby zrobić coś, jak wywołać **OpenFileDialog** składnika `ShowDialog()` metody. Możesz utworzyć własne metody, aby program wykonywanie czynności, jak teraz tworzysz o nazwie `showButton_Click()` metodę, która otwiera okno dialogowe i obrazu, gdy użytkownik wybierze przycisk.

    6.  Visual C#, Dodaj miejsce, a następnie dodaj dwie znaku równości (`==`). W języku Visual Basic, Dodaj miejsce, a następnie użyj pojedynczego znaku równości (`=`). (Visual C# i Visual Basic Operatory równości różnych.)

    7.  Dodaj miejsce do innego. Natychmiast po wykonaniu czynności innego **IntelliSense** zostanie otwarte okno. Wpisywania `DialogResult` i wybierz polecenie **kartę** klawisz, aby ją dodać.

        > [!NOTE]
        >  Podczas pisania kodu, aby wywołać metodę czasami zwraca wartość. W takim przypadku **OpenFileDialog** składnika <xref:System.Windows.Forms.CommonDialog.ShowDialog> metoda zwraca <xref:System.Windows.Forms.DialogResult> wartość. DialogResult jest specjalna wartość, która informuje, co się stało w oknie dialogowym. **OpenFileDialog** składnika może spowodować, wybierania użytkownika **OK** lub **anulować**, więc jego `ShowDialog()` metoda zwraca albo `DialogResult.OK` lub `DialogResult.Cancel`.

    8.  Wpisz kropką, aby otworzyć wartość DialogResult **IntelliSense** okna. Wprowadź literę `O` i wybierz polecenie **kartę** klawisz, aby wstawić **OK**.

         Aby dowiedzieć się więcej na temat DialogResult, zobacz [DialogResult](http://msdn.microsoft.com/library/system.windows.forms.dialogresult.aspx).

        > [!NOTE]
        >  Powinna zakończyć się pierwszy wiersz kodu. Visual C#, należy go poniżej.
        >
        >  `if (openFileDialog1.ShowDialog() == DialogResult.OK)`
        >
        >  W języku Visual Basic należy go poniżej.
        >
        >  `If OpenFileDialog1.ShowDialog() = DialogResult.OK Then`

    9. Teraz Dodaj kolejny wiersz kodu. Należy ją wpisać (lub skopiuj i wklej go), ale należy wziąć pod uwagę, aby dodać go za pomocą funkcji IntelliSense. Im bardziej znanych jesteś z funkcji IntelliSense, tym szybciej można napisać własny kod. Twoje final `showButton_Click()` metody wygląda podobnie do następującej. (Wybierz **VB** kartę, aby wyświetlić wersję kodu języka Visual Basic.)

         [!code-csharp[VbExpressTutorial1Step8#1](../ide/codesnippet/CSharp/step-8-write-code-for-the-show-a-picture-button-event-handler_1.cs)]
         [!code-vb[VbExpressTutorial1Step8#1](../ide/codesnippet/VisualBasic/step-8-write-code-for-the-show-a-picture-button-event-handler_1.vb)]

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

-   Aby przejść do następnego kroku samouczka, zobacz [krok 9: Przejrzyj, komentowanie i testowanie kodu](../ide/step-9-review-comment-and-test-your-code.md).

-   Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 7: Dodawanie składników okna dialogowego do formularza](../ide/step-7-add-dialog-components-to-your-form.md).
