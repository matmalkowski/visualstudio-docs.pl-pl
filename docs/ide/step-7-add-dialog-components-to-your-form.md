---
title: Krok 7. Dodawanie składników okna dialogowego do formularza
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: ea98c55e-6213-4893-ba7b-f19d7f119527
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 73edc0dd97828d6b10d76ecac7367127e8bb725c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="step-7-add-dialog-components-to-your-form"></a>Krok 7. Dodawanie składników okna dialogowego do formularza
Aby włączyć program do otwierania plików obrazu, w którym można wybrać kolor tła, w tym kroku należy dodać **OpenFileDialog** składnika i **ColorDialog** składnika do formularza.  

 Składnik jest formantu w pewnym sensie. Użyj przybornika, aby dodać składnik do formularza i ustawić jej właściwości, za pomocą **właściwości** okna. Ale w przeciwieństwie do formantu, dodanie składnika do formularza nie dodaje widocznego elementu, który użytkownik może zobaczyć na formularzu. Zamiast tego zawiera niektóre zachowania, które mogą być uruchamiane z kodem. Jest to składnik, którego kliknięcie spowoduje otwarcie **Otwórz plik** okno dialogowe.  

 ![łącze do wideo](../data-tools/media/playvideo.gif "PlayVideo")wersję wideo tego tematu, zobacz [samouczek 1: Tworzenie podglądu obrazów w języku Visual Basic - 3 wideo](http://go.microsoft.com/fwlink/?LinkId=205213) lub [samouczek 1: Tworzenie podglądu obrazów w języku C# — Wideo 3](http://go.microsoft.com/fwlink/?LinkId=205202). Tych klipów wideo korzysta z wcześniejszej wersji programu Visual Studio, dlatego są niewielkie różnice w niektórych poleceń menu i inne elementy interfejsu użytkownika. Jednak koncepcje i procedury działają podobnie w bieżącej wersji programu Visual Studio.  

### <a name="to-add-dialog-components-to-your-form"></a>Aby dodać składniki okna dialogowego do formularza  

1.  Wybierz Projektant formularzy systemu Windows (pliku Form1.cs [projekt] lub [projekt] Form1.vb), a następnie otwórz **okna** w przyborniku.  

    > [!NOTE]
    >  **Okna** grupa w przyborniku ma składników, które Otwórz wielu przydatne w oknach dialogowych, które mogą być używane do otwierania i zapisywania plików, przeglądanie katalogów i wybierając pozycję czcionki i kolory. Dwa składniki okna dialogowego są używane w tym projekcie: **OpenFileDialog** i **ColorDialog**.  

2.  Aby dodać składnik o nazwie **openFileDialog1** do formularza, kliknij dwukrotnie **OpenFileDialog**. Aby dodać składnik o nazwie **colorDialog1** do formularza, kliknij dwukrotnie **ColorDialog** w przyborniku. (Należy użyć co w następnym kroku samouczka). Powinien zostać wyświetlony obszar na dole Projektant formularzy systemu Windows (poniżej formularza podglądu obrazów), który zawiera ikonę dla poszczególnych składników dwa okna dialogowego, które zostały dodane, jak pokazano na poniższej ilustracji.  

     ![Składniki okna dialogowego](../ide/media/express_dialogsadded.png "Express_DialogsAdded")  
Składniki okna dialogowego  

3.  Wybierz **openFileDialog1** ikonę w obszarze u dołu Projektant formularzy systemu Windows. Ustaw dwie właściwości:  

    -   Ustaw **filtru** właściwości dla następujących (możesz skopiować i wkleić go):  

        ```  
        JPEG Files (*.jpg)|*.jpg|PNG Files (*.png)|*.png|BMP Files (*.bmp)|*.bmp|All files (*.*)|*.*  
        ```  

    -   Ustaw **tytuł** właściwości do następującego: **wybierz plik obrazu**  

         **Filtru** ustawienia właściwości określa rodzaj typów plików, które będą wyświetlane w **wybierz obraz** plik — okno dialogowe.  

    > [!NOTE]
    >  Aby zobaczyć przykładowy **Otwieranie pliku** okno dialogowe w innej aplikacji, Otwórz w Notatniku lub programie Paint, a na pasku menu wybierz pozycję **pliku**, **Otwórz**. Powiadomienie nie **pliki typu** listy rozwijanej u dołu. Użytkownik używany po prostu **filtru** właściwości w **OpenFileDialog** składnik, aby skonfigurować. Zauważ również, jak **tytuł** i **filtru** właściwości są pogrubione w **właściwości** okna. IDE robi to, aby pokazać wszystkie właściwości, które zostały zmienione z wartościami domyślnymi.  

### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  

-   Aby przejść do następnego kroku samouczka, zobacz [krok 8: wpisywanie kodu dla programu obsługi zdarzeń obrazu przycisku](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md).  

-   Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 6: Nazwa Your kontrolki przycisku](../ide/step-6-name-your-button-controls.md).
