---
title: 'Krok 11: Uruchom program i próbowanie innych funkcji'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: feee6c95852e90fef5f3fcacf47dfb67d48255b7
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34747645"
---
# <a name="step-11-run-your-program-and-try-other-features"></a>Krok 11: Uruchom program i próbowanie innych funkcji
Program jest gotowy i gotowa do uruchomienia. Możesz uruchomić program i ustawić kolor tła <xref:System.Windows.Forms.PictureBox>. Aby dowiedzieć się więcej, spróbuj zwiększyć program zmiana koloru formularza, dostosowywanie przycisków i pola wyboru i zmiana właściwości formularza.

 Aby pobrać ukończoną wersję przykładu, zobacz [pełnego obrazu podglądu samouczek próbki](http://code.msdn.microsoft.com/Complete-Picture-Viewer-7d91d3a8).

 ![łącze do wideo](../data-tools/media/playvideo.gif)wersję wideo tego tematu, zobacz [samouczek 1: Tworzenie podglądu obrazów w języku Visual Basic - 5 wideo](http://go.microsoft.com/fwlink/?LinkId=205216) lub [samouczek 1: Tworzenie podglądu obrazów w języku C# - 5 wideo](http://go.microsoft.com/fwlink/?LinkId=205206). Tych klipów wideo korzysta z wcześniejszej wersji programu Visual Studio, dlatego są niewielkie różnice w niektórych poleceń menu i inne elementy interfejsu użytkownika. Jednak koncepcje i procedury działają podobnie w bieżącej wersji programu Visual Studio.

## <a name="to-run-your-program-and-set-the-background-color"></a>Aby uruchomić program i kolor tła

1.  Wybierz **F5**, lub na pasku menu wybierz **debugowania** > **Rozpocznij debugowanie**.

2.  Przed otwarciem obrazu wybierz **kolor tła** przycisku. **Kolor** zostanie otwarte okno dialogowe.

     ![Okno dialogowe kolorów](../ide/media/express_colordialog.png)
**kolor** — okno dialogowe

3.  Wybierz kolor, aby ustawić kolor tła PictureBox. Należy dokładnie przejrzeć `backgroundButton_Click()` metodę, aby zrozumieć, jak to działa.

    > [!NOTE]
    >  Można załadować obrazu z Internetu przez wklejenie jej adres URL do **Otwórz plik** okno dialogowe. Spróbuj odnaleźć obrazu z przeźroczystym tłem, dlatego przedstawia kolor tła.

4.  Wybierz **Wyczyść obraz** przycisk, aby upewnić się, usuwa ją. Następnie, zamknij program, wybierając **Zamknij** przycisku.

## <a name="to-try-other-features"></a>Aby wypróbować inne funkcje

-   Zmiana koloru formularz i przyciski, za pomocą **BackColor** właściwości.

-   Dostosowywanie przycisków i pola wyboru przy użyciu **czcionki** i **ForeColor** właściwości.

-   Zmień formularza **FormBorderStyle** i **ControlBox** właściwości.

-   Użyj formularza **AcceptButton** i **CancelButton** właściwości dzięki tym przyciski są automatycznie wybranego gdy użytkownik wybierze **Enter** lub **Esc** klucza. Ten program był otwarty **Otwieranie pliku** okno dialogowe, gdy użytkownik wybierze **Enter** i zamknąć okno, gdy użytkownik wybierze **Esc**.

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

-   Aby dowiedzieć się więcej na temat programowania w programie Visual Studio, zobacz [koncepcje programowania](http://msdn.microsoft.com/Library/65c12cca-af4f-4017-886e-2dbc00a189d6).

-   Aby dowiedzieć się więcej na temat języka Visual Basic, zobacz [opracowywania aplikacji za pomocą Visual Basic](/dotnet/visual-basic/developing-apps/index).

-   Aby dowiedzieć się więcej na temat języka Visual C#, zobacz [wprowadzenie do języka C# i .NET Framework](/dotnet/csharp/getting-started/introduction-to-the-csharp-language-and-the-net-framework).

-   Aby przejść do następnego samouczek, zobacz [samouczek 2: tworzenie kwizu matematycznego](../ide/tutorial-2-create-a-timed-math-quiz.md).

-   Aby powrócić do poprzedniego kroku samouczka, zobacz [kroku 10: pisanie kodu dla dodatkowych przycisków i pola wyboru](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).
