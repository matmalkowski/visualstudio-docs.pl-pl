---
title: "Szybki Start: Tworzenie Windows aplikacji formularzy w programie Visual Studio za pomocą Visual Basic | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 12/04/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: quickstart
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: ghogen
dev_langs: vb
ms.openlocfilehash: cf7ba7882d9e95cac013e257a73bd536f36b97cf
ms.sourcegitcommit: 64c7682ec3a2cbea684e716803398d4278b591d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2017
---
# <a name="quickstart-create-a-windows-forms-app-in-visual-studio-with-visual-basic"></a>Szybki Start: Tworzenie Windows aplikacji formularzy w programie Visual Studio za pomocą Visual Basic
W tej 5 – 10 min wprowadzenie do programu Visual Studio zintegrowane środowisko programistyczne (IDE) utworzysz prostą aplikację języka Visual Basic, która ma interfejs użytkownika systemu Windows (UI).

Jeśli nie został już zainstalowany program Visual Studio, przejdź do [programu Visual Studio pobiera](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) stronę, aby zainstalować ją bezpłatnie.

## <a name="create-a-project"></a>Tworzenie projektu
Najpierw utworzysz projekt aplikacji Visual Basic. Typ projektu zawiera wszystkie pliki szablonu, które będą potrzebne, zanim nawet dodano niczego.  

1. Otwórz program Visual Studio 2017 r.  

2. Na pasku menu u góry wybierz **pliku** > **nowy** > **projektu...** .  

3. W **nowy projekt** okno dialogowe w okienku po lewej stronie rozwiń węzeł **Visual Basic**, a następnie wybierz pozycję **klasycznego pulpitu systemu Windows**. W środkowym okienku wybierz **aplikacji formularzy systemu Windows (.NET Framework)**. Nadaj nazwę plikowi `HelloWorld`.  

     Jeśli nie widzisz **aplikacji formularzy systemu Windows (.NET Framework)** projektu szablonu, Anuluj poza **nowy projekt** okna dialogowego polu, a następnie na pasku menu u góry wybierz **narzędzia**  >  **Pobierz narzędzia i funkcje...** . Uruchamia Instalator programu Visual Studio. Wybierz **tworzenia klasycznych aplikacji .NET** obciążenia, a następnie wybierz **Modyfikuj**.  

     ![Obciążenie .NET core w Instalatorze programu Visual Studio](../ide/media/install-dot-net-desktop-env.png)  

## <a name="create-the-application"></a>Tworzenie aplikacji
Po wybraniu szablonu projektu języka Visual Basic oraz nazwę pliku, Visual Studio otwiera formularza. Formularz jest interfejs użytkownika systemu Windows. Utworzymy aplikację "Hello World" przez dodawanie formantów do formularza, a następnie będzie uruchomić aplikację.   

### <a name="add-a-button-to-the-form"></a>Dodawanie przycisku do formularza  

1. Kliknij przycisk **przybornika** można otworzyć okna wysuwanego przybornika.

     ![Kliknij przycisk przybornika, aby otworzyć okno przybornika](../ide/media/vb-toolbox-toolwindow.png)  

     (Jeśli nie widzisz opcji wysuwanego przybornika, można otworzyć go na pasku menu. Aby to zrobić, kliknij przycisk **widoku** > **przybornika**. Możesz również nacisnąć klawisz **Ctrl**+**Alt**+**X**.)

2. Kliknij przycisk **numeru Pin** ikonę, aby dock okno przybornika.

     ![Kliknij ikonę numeru Pin, aby przypiąć okno przybornika do środowiska IDE](../ide/media/vb-pin-the-toolbox-window.png)  
3. Kliknij przycisk **przycisk** kontroli, a następnie przeciągnij ją na formularzu.

     ![Dodawanie przycisku do formularza](../ide/media/vb-add-a-button-to-form1.png)

4. W **wygląd** sekcji **właściwości** , wpisz "Kliknij tutaj", a następnie naciśnij klawisz **Enter**.

     ![Dodawanie tekstu na przycisk w formularzu](../ide/media/vb-button-control-text.png)  

     (Jeśli nie widzisz okna właściwości, można otworzyć go na pasku menu. Aby to zrobić, kliknij przycisk **widoku** > **okna właściwości**. Możesz również nacisnąć klawisz **F4**.)

5. W **projekt** sekcji **właściwości** , zmienić nazwę z "Button1" na "btnClickThis", a następnie naciśnij klawisz **Enter**.

     ![Dodawanie funkcji do przycisk w formularzu](../ide/media/vb-button-control-function.png)

### <a name="add-a-label-to-the-form"></a>Dodawanie etykiet do formularza
Teraz, gdy dodaliśmy kontrolkę przycisku, aby utworzyć akcję Dodajmy formantu etykiety do wysyłania tekst.

1. Wybierz **etykiety** kontrolować z okno przybornika, a następnie przeciągnij go do formularza i upuść je pod **kliknij** przycisku.

2. W **projekt** sekcji **właściwości** , zmienić nazwę z "Label1" na "lblHelloWorld", a następnie naciśnij klawisz **Enter**.

### <a name="add-code-to-the-form"></a>Dodawanie kodu do formularza

1. W **Form1.vb &#91; projektowania &#93;** okna, kliknij dwukrotnie **kliknij** przycisk, aby otworzyć **Form1.vb** okna.

      (Można również rozwinąć **Form1.vb** w **Eksploratora rozwiązań** okna, a następnie kliknij przycisk **Form1**.)

2. W **Form1.vb** okna, między **Private Sub** wiersza i **End Sub** wiersz, wpisz lub Wklej `lblHelloWorld.Text = "Hello World!"`.

     ![Dodaj kod, aby formularz formularza](../ide/media/vb-add-code-to-the-form.png)

## <a name="run-the-application"></a>Uruchamianie aplikacji
1. Kliknij przycisk **Start** przycisk, aby uruchomić aplikację.

     ![Kliknij przycisk Start do debugowania i uruchamiania aplikacji](../ide/media/vb-click-start-hello-world.png)

   Nastąpi kilka rzeczy. W programie Visual Studio IDE zostanie otwarte okno narzędzia diagnostyczne i dane wyjściowe zostanie otwarte okno zbyt. Ale poza IDE, zostanie wyświetlone okno dialogowe Form1. Będzie ona zawierać Twojego **kliknij** przycisk i tekście "Label1".

2. Kliknij przycisk **kliknij** przycisk **Form1** okno dialogowe. Należy zauważyć, że tekst "Label1" zostanie zmieniony na "Hello World!".

    ![Okno dialogowe Form1 zawierającego Label1 tekst ](../ide/media/vb-form1-dialog-hello-world.png)

Gratulujemy Kończenie pracy tego przewodnika Szybki Start! Mamy nadzieję, że znasz nieco dotyczące języka Visual Basic i Visual Studio IDE. Jeśli chcesz delve głębiej, kontynuuj samouczek w **samouczki** sekcji spisu treści.  

## <a name="see-also"></a>Zobacz także   
* [Szybki Start: Tworzenie aplikacji konsoli w programie Visual Studio za pomocą Visual Basic](quickstart-visual-basic-console.md)
* [Dowiedz się więcej na temat języka Visual Basic IntelliSense](visual-basic-specific-intellisense.md)  
