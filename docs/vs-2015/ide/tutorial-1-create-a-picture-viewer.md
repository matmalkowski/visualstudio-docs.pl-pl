---
title: 'Samouczek 1: Tworzenie przeglądarki obrazów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3071d6df-2b2f-4e95-ab68-bef727323136
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1472d682ea6c00807318873a3f738f792875d1bc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42633297"
---
# <a name="tutorial-1-create-a-picture-viewer"></a>Samouczek 1: Tworzenie podglądu obrazów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [samouczek 1: tworzenie przeglądarki obrazów](https://docs.microsoft.com/visualstudio/ide/tutorial-1-create-a-picture-viewer).  
  
W tym samouczku kompilujesz program, który ładuje obraz z pliku i wyświetla go w oknie. Dowiesz się, jak przeciągać formanty, takie jak przyciski i pola obrazu w formularzu, ustawiać ich właściwości i używać kontenerów, aby sprawnie zmieniać rozmiar formularza. Można również rozpocząć pisanie kodu. Dowiesz się, jak:  
  
-   Utwórz nowy projekt.  
  
-   Testuj (Debuguj) aplikację.  
  
-   Dodaj podstawowe formanty, takie jak pola wyboru i przyciski do formularza.  
  
-   Położenie formantów w formularzu za pomocą układów.  
  
-   Dodaj **Otwórz plik** i **kolor** do formularza przy użyciu okna dialogowego.  
  
-   Pisz kod, używając funkcji IntelliSense i fragmentów kodu.  
  
-   Opisz metody obsługi zdarzeń.  
  
 Po zakończeniu program będzie wyglądać jak na poniższym obrazie.  
  
 ![Obraz, który jest tworzony w tym samouczku](../ide/media/express-pictureviewerdone.png "Express_PictureViewerDone")  
Obraz tworzony w ramach tego samouczka  
  
 Aby pobrać pełną wersję przykładu, zobacz [przykładowy samouczek pełnej przeglądarki obrazów](http://code.msdn.microsoft.com/Complete-Picture-Viewer-7d91d3a8).  
  
 ![Link do wideo](../data-tools/media/playvideo.gif "PlayVideo")wersja wideo tego tematu, zobacz [jak: tworzenie przeglądarki obrazów w języku Visual Basic?](http://go.microsoft.com/fwlink/?LinkId=205207) lub [jak: tworzenie przeglądarki obrazów w języku C#?](http://go.microsoft.com/fwlink/?LinkId=205198).  
  
> [!NOTE]
>  W tych filmach wideo użyj wcześniejszej wersji programu Visual Studio, więc istnieją drobne różnice w niektórych poleceniach menu i innych elementach interfejsu użytkownika. Jednakże pojęcia i procedury działają podobnie w bieżącej wersji programu Visual Studio. Visual C# i Visual Basic zostały omówione w tym samouczku, więc Skoncentruj się na informacjach specyficznych dla języka programowania, którego używasz.  
>   
>  Aby wyświetlić kod w języku Visual Basic, wybierz opcję **VB** u góry bloków kodu, a następnie, aby wyświetlić kod Visual C#, wybierz opcję **C#** kartę. Jeśli interesuje Cię Nauka języka Visual C++, zobacz [wprowadzenie](../misc/getting-started-with-visual-cpp-in-visual-studio-2015.md) i [samouczek języka C++](http://www.cplusplus.com/doc/tutorial/).  
>   
>  Jeśli chcesz się dowiedzieć, jak napisać Visual C# lub Visual Basic aplikacje dla Windows Store, zobacz [tworzenie pierwszej aplikacji Windows Store przy użyciu języka C# lub Visual Basic](http://msdn.microsoft.com/library/windows/apps/hh974581.aspx). Aby uzyskać informacje dotyczące tworzenia aplikacji JavaScript dla Windows Store, zobacz [tworzenie pierwszej aplikacji Windows Store przy użyciu języka JavaScript](http://msdn.microsoft.com/library/windows/apps/br211385.aspx).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Krok 1. Tworzenie projektu aplikacji Windows Forms](../ide/step-1-create-a-windows-forms-application-project.md)|Rozpocznij od utworzenia projektu aplikacji Windows Forms.|  
|[Krok 2. Uruchamianie programu](../ide/step-2-run-your-program.md)|Uruchom program aplikacji Windows Forms, który został utworzony w poprzednim kroku.|  
|[Krok 3. Ustawianie właściwości formularza](../ide/step-3-set-your-form-properties.md)|Zmień wygląd formularz za pomocą **właściwości** okna.|  
|[Krok 4. Określanie układu formularza przy użyciu kontrolki TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)|Dodaj `TableLayoutPanel` formantu do formularza.|  
|[Krok 5. Dodawanie kontrolek do formularza](../ide/step-5-add-controls-to-your-form.md)|Dodaj formanty, takie jak `PictureBox` kontroli i `CheckBox` formantu do formularza. Dodaj do formularza przyciski.|  
|[Krok 6. Nadawanie nazw kontrolkom przycisków](../ide/step-6-name-your-button-controls.md)|Zmień nazwy przycisków na nieco bardziej opisowe.|  
|[Krok 7. Dodawanie składników okna dialogowego do formularza](../ide/step-7-add-dialog-components-to-your-form.md)|Dodaj **OpenFileDialog** składnika i **ColorDialog** składnika do formularza.|  
|[Krok 8. Tworzenie kodu procedury obsługi zdarzeń dla przycisku Pokaż obraz](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)|Pisz kod, używając funkcji IntelliSense.|  
|[Krok 9. Przegląd, komentowanie i testowanie kodu](../ide/step-9-review-comment-and-test-your-code.md)|Przejrzyj i przetestuj swój kod. W razie potrzeby dodaj komentarze.|  
|[Krok 10. Tworzenie kodu dla dodatkowych przycisków i pola wyboru](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)|Napisz kod, aby inne przyciski i pole wyboru będą działać przy użyciu technologii IntelliSense.|  
|[Krok 11. Uruchamianie programu i wypróbowanie innych funkcji](../ide/step-11-run-your-program-and-try-other-features.md)|Uruchom program i ustawić kolor tła. Spróbuj innych funkcji, takich jak zmienianie kolorów, czcionek i obramowania.|



