---
title: 'Samouczek 1: Tworzenie podglądu obrazów'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 3071d6df-2b2f-4e95-ab68-bef727323136
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5be14bf68f88bc058adf3685cc30e3ab545a6354
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="tutorial-1-create-a-picture-viewer"></a>Samouczek 1: Tworzenie podglądu obrazów
W tym samouczku tworzenia programu, który ładuje obraz z pliku i wyświetla go w oknie. Sposób przeciągnij formanty, takie jak przycisków i pola obrazu na formularzu, ich właściwości i używanie kontenerów aby sprawnie zmienić rozmiar formularza. Można również rozpocząć pisanie kodu. Dowiesz się, jak:  

-   Utwórz nowy projekt.  

-   Test (debugowanie) aplikacji.  

-   Dodawanie podstawowych formantach, takich jak przyciski i pola wyboru do formularza.  

-   Umieść formanty formularza za pomocą układów.  

-   Dodaj **Otwórz plik** i **kolor** okien dialogowych do formularza.  

-   Pisanie kodu za pomocą wstawki kodu programu IntelliSense i kod.  

-   Zapis metody obsługi zdarzeń.  

 Po zakończeniu program będzie wyglądać podobnie jak na poniższej ilustracji.  

 ![Obraz, który można utworzyć w tym samouczku](../ide/media/express_pictureviewerdone.png "Express_PictureViewerDone")  
Obraz, który można utworzyć w tym samouczku  

 Aby pobrać ukończoną wersję przykładu, zobacz [przykładowy samouczek pełny obraz podglądu](http://code.msdn.microsoft.com/Complete-Picture-Viewer-7d91d3a8).  

 ![łącze do wideo](../data-tools/media/playvideo.gif "PlayVideo")wersję wideo tego tematu, zobacz [jak i. Tworzenie podglądu obrazów w języku Visual Basic?](http://go.microsoft.com/fwlink/?LinkId=205207) lub [jak i. Tworzenie podglądu obrazów w języku C#?](http://go.microsoft.com/fwlink/?LinkId=205198).  

> [!NOTE]
>  Tych klipów wideo korzysta z wcześniejszej wersji programu Visual Studio, dlatego są niewielkie różnice w niektórych poleceń menu i inne elementy interfejsu użytkownika. Jednak koncepcje i procedury działają podobnie w bieżącej wersji programu Visual Studio. Visual C# i Visual Basic są przedstawione w tym samouczku, dlatego skupić się na informacje specyficzne dla języka programowania, którego używasz.  
>   
>  Aby wyświetlić kod w języku Visual Basic, wybierz pozycję **VB** w górnej części bloki kodu, a następnie wyświetlić kodu Visual C#, wybierz **C#** kartę. Jeśli interesuje Cię szkoleniowe dotyczące języka Visual C++, zobacz [wprowadzenie](../ide/getting-started-with-cpp-in-visual-studio.md) i [samouczek języka C++](http://www.cplusplus.com/doc/tutorial/).  
>   
>  Jeśli chcesz się dowiedzieć, jak pisać aplikacje Visual C# lub Visual Basic platformy uniwersalnej systemu Windows, zobacz [aplikacji platformy uniwersalnej systemu Windows kompilacji](https://developer.microsoft.com/windows/apps).

## <a name="related-topics"></a>Tematy pokrewne  

|Tytuł|Opis|  
|-----------|-----------------|  
|[Krok 1. Tworzenie projektu aplikacji Windows Forms](../ide/step-1-create-a-windows-forms-application-project.md)|Rozpocznij od utworzenia projektu aplikacji formularzy systemu Windows.|  
|[Krok 2. Uruchamianie programu](../ide/step-2-run-your-program.md)|Uruchom program aplikacji formularzy systemu Windows utworzonego w poprzednim kroku.|  
|[Krok 3. Ustawianie właściwości formularza](../ide/step-3-set-your-form-properties.md)|Zmień wygląd formularza za pomocą **właściwości** okna.|  
|[Krok 4. Określanie układu formularza przy użyciu kontrolki TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)|Dodaj `TableLayoutPanel` sterowania do formularza.|  
|[Krok 5. Dodawanie kontrolek do formularza](../ide/step-5-add-controls-to-your-form.md)|Dodaj formanty, takie jak `PictureBox` kontroli i `CheckBox` sterowania do formularza. Dodawanie przycisków do formularza.|  
|[Krok 6. Nadawanie nazw kontrolkom przycisków](../ide/step-6-name-your-button-controls.md)|Zmień nazwę przyciski komputera na bardziej użyteczny.|  
|[Krok 7. Dodawanie składników okna dialogowego do formularza](../ide/step-7-add-dialog-components-to-your-form.md)|Dodaj **OpenFileDialog** składnika i **ColorDialog** składnika do formularza.|  
|[Krok 8. Tworzenie kodu procedury obsługi zdarzeń dla przycisku Pokaż obraz](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)|Pisanie kodu za pomocą narzędzia IntelliSense.|  
|[Krok 9. Przegląd, komentowanie i testowanie kodu](../ide/step-9-review-comment-and-test-your-code.md)|Przejrzyj i testowanie kodu. W razie potrzeby dodaj komentarze.|  
|[Krok 10. Tworzenie kodu dla dodatkowych przycisków i pola wyboru](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)|Napisz kod umożliwiający innych przycisków i służbowego pola wyboru przy użyciu funkcji IntelliSense.|  
|[Krok 11. Uruchamianie programu i wypróbowanie innych funkcji](../ide/step-11-run-your-program-and-try-other-features.md)|Uruchom program i kolor tła. Spróbuj inne funkcje, takie jak zmiana kolory, czcionki i obramowanie.|
