---
title: 'Krok 11: Uruchamianie programu i próbowanie innych funkcji | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 38d83c46ecf910a4df5050c6e73de58a1a0963b1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42676624"
---
# <a name="step-11-run-your-program-and-try-other-features"></a>Krok 11. Uruchamianie programu i wypróbowanie innych funkcji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [krok 11: Uruchom swój Program i spróbuj innych funkcji](https://docs.microsoft.com/visualstudio/ide/step-11-run-your-program-and-try-other-features).  
  
Program jest gotowy i gotowa do uruchomienia. Możesz uruchomić program i ustawić kolor tła PictureBox. Aby dowiedzieć się więcej, spróbuj poprawić program zmieniając kolor formularza, dostosowując przyciski i pole wyboru i zmieniając właściwości formularza.  
  
 Aby pobrać pełną wersję przykładu, zobacz [przykładowy samouczek pełnej przeglądarki obrazów](http://code.msdn.microsoft.com/Complete-Picture-Viewer-7d91d3a8).  
  
 ![Link do wideo](../data-tools/media/playvideo.gif "PlayVideo")wersja wideo tego tematu, zobacz [samouczek 1: tworzenie przeglądarki obrazów w Visual Basic – wideo 5](http://go.microsoft.com/fwlink/?LinkId=205216) lub [samouczek 1: tworzenie przeglądarki obrazów w języku C# - Film wideo 5](http://go.microsoft.com/fwlink/?LinkId=205206). W tych filmach wideo użyj wcześniejszej wersji programu Visual Studio, więc istnieją drobne różnice w niektórych poleceniach menu i innych elementach interfejsu użytkownika. Jednakże pojęcia i procedury działają podobnie w bieżącej wersji programu Visual Studio.  
  
### <a name="to-run-your-program-and-set-the-background-color"></a>Aby uruchomić program i ustawić kolor tła  
  
1.  Wybierz F5 lub na pasku menu wybierz **debugowania**, **Rozpocznij debugowanie**.  
  
2.  Przed otwarciem obrazu wybierz **Ustaw kolor tła** przycisku. **Kolor** zostanie otwarte okno dialogowe.  
  
     ![Okno dialogowe kolorów](../ide/media/express-colordialog.png "Express_ColorDialog")  
Okno dialogowe kolorów  
  
3.  Wybierz kolor, aby ustawić kolor tła PictureBox. Przyjrzyj się bliżej `backgroundButton_Click()` metodę, aby zrozumieć, jak to działa.  
  
    > [!NOTE]
    >  Możesz załadować obraz z Internetu wklejając jego adres URL do **Otwórz plik** okno dialogowe. Spróbuj odnaleźć obraz z przezroczystym tłem, więc pojawia się kolor tła.  
  
4.  Wybierz **Wyczyść obraz** przycisk, aby upewnić się, czy to powoduje wyczyszczenie. Następnie zamknij program, wybierając **Zamknij** przycisku.  
  
### <a name="to-try-other-features"></a>Aby wypróbować inne funkcje  
  
-   Zmień kolor formularza i przyciski za pomocą **BackColor** właściwości.  
  
-   Dostosuj przyciski i pola wyboru za pomocą **czcionki** i **ForeColor** właściwości.  
  
-   Zmień formularza **FormBorderStyle** i **ControlBox** właściwości.  
  
-   Użyj formularza **AcceptButton** i **CancelButton** właściwości, tak aby przyciski są wybierane automatycznie kiedy użytkownik naciśnie klawisz ENTER lub ESC. Ten program był otwarty **Otwórz plik** okno dialogowe, gdy użytkownik zdecyduje się WPROWADZIĆ, a następnie zamknij okno, gdy użytkownik wybierze klawisz ESC.  
  
### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
-   Aby dowiedzieć się więcej na temat programowania w programie Visual Studio, zobacz [pojęcia programowania](http://msdn.microsoft.com/library/65c12cca-af4f-4017-886e-2dbc00a189d6).  
  
-   Aby dowiedzieć się więcej na temat języka Visual Basic, zobacz [tworzenie aplikacji za pomocą Visual Basic](http://msdn.microsoft.com/library/1e1c0c81-6d95-4167-a98b-44b1efb6d25f).  
  
-   Aby dowiedzieć się więcej na temat Visual C#, zobacz [wprowadzenie do języka C# i .NET Framework](http://msdn.microsoft.com/library/0a2dff4e-cd84-42ff-8141-e89889b24081).  
  
-   Aby przejść do następnego samouczka, zobacz [samouczek 2: Utwórz, Timed Math Quiz](../ide/tutorial-2-create-a-timed-math-quiz.md).  
  
-   Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 10: pisanie kodu dla dodatkowych przycisków i pola wyboru](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).



