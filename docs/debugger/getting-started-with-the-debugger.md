---
title: Wprowadzenie do debugera
ms.description: Learn how to start the Visual Studio debugger, step through code, and inspect data.
ms.custom: mvc
ms.date: 03/16/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0f3d4c27f0aedf879137b3ef7a154fb7dd6f9164
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766262"
---
# <a name="tutorial-learn-to-debug-using-visual-studio"></a>Samouczek: Dowiedz się, jak debugować przy użyciu programu Visual Studio

W tym temacie przedstawiono funkcje debugera programu Visual Studio w przewodniku krok po kroku. Widok wyższego poziomu funkcje debugera, zobacz [samouczek funkcji debugera](../debugger/debugger-feature-tour.md).

Albo odczytanie wzdłuż, zobacz Funkcje debugera, lub można pobrać kompletne przykładowe używany w funkcji samouczka i postępuj zgodnie z instrukcjami samodzielnie. Aby pobrać przykład i z niego skorzystać, przejdź do [pokaz podglądu zdjęć](https://code.msdn.microsoft.com/windowsdesktop/WPF-Photo-Viewer-Demo-be75662a).

|         |         |
|---------|---------|
|  ![Ikona aparatu film wideo](../install/media/video-icon.png "obejrzeć film wideo")  |    [Obejrzyj film](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugger-Feature-tour-of-Visual-studio-2017-sqwiwLD6D_1111787171) debugowania, który zawiera podobne kroki. |

Mimo że aplikacja demonstracyjna C#, funkcje mają zastosowanie do języka C++, Visual Basic, JavaScript i innych języków obsługiwanych przez program Visual Studio (inaczej w przypadku gdy).

W tym samouczku obejmują:

> [!div class="checklist"]
> * Uruchom debuger i trafień punktów przerwania.
> * Dowiedz się więcej poleceń do wykonania kroków opisanych kodu w debugerze
> * Sprawdź zmienne w etykietki danych i debugera systemu windows
> * Sprawdź stosu wywołań
> * Przy użyciu Pomocnika wyjątków

## <a name="prerequisites"></a>Wymagania wstępne

* Musi mieć Visual Studio 2017 r zainstalowany i. **NET development pulpitu** obciążenia.

    Jeśli nie został już zainstalowany program Visual Studio, przejdź do [program Visual Studio pobiera](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) stronę, aby zainstalować ją bezpłatnie.

    Jeśli musisz zainstalować obciążenie, ale jeszcze programu Visual Studio, kliknij przycisk **Otwórz Instalator programu Visual Studio** łącze w lewym okienku **nowy projekt** okno dialogowe (wybierz **pliku**  >  **Nowe** > **projektu**). Uruchamia Instalator programu Visual Studio. Wybierz. **NET development pulpitu** obciążenia, a następnie wybierz **Modyfikuj**.

## <a name="start-the-debugger"></a>Uruchom debuger!

1. W odbiorze te czynności w programie Visual Studio, Pobierz przykład [na tej stronie](https://code.msdn.microsoft.com/windowsdesktop/WPF-Photo-Viewer-Demo-be75662a).

    > [!IMPORTANT]
    > Musisz zainstalować program Visual Studio z obciążeniem projektowania aplikacji .NET, aby uruchomić aplikację, której używamy w pokaz.

2. Rozpakuj projektu.

3. Otwórz program Visual Studio i wybierz **pliku > Otwórz** menu polecenie, a następnie wybierz pozycję **projektu/rozwiązania**, a następnie otwórz folder, gdzie został pobrany projekt.

     ![Otwórz przykładowy projekt](../debugger/media/dbg-tour-open-project.png "Otwórz projekt")

3. Otwórz pokaz podgląd fotografii WPF > C#, wybierz plik photoapp.sln i wybierz opcję **Otwórz**.

     Projekt zostanie otwarty w programie Visual Studio. Eksplorator rozwiązań w okienku po prawej stronie zawiera wszystkie pliki projektu.

    ![Pliki w Eksploratorze rozwiązania](../debugger/media/dbg-tour-solution-explorer.png "Eksploratora rozwiązań")

4. Naciśnij klawisz F5 (**Debuguj > Rozpocznij debugowanie** lub **Rozpocznij debugowanie** przycisk ![Rozpocznij debugowanie](../debugger/media/dbg-tour-start-debugging.png "Rozpocznij debugowanie") na pasku narzędzi debugowania).

     ![Zdjęcie podglądu aplikacji](../debugger/media/dbg-tour-wpf-app.png "Photo aplikacji Viewer")

     F5 uruchomienia aplikacji w debugerze procesu aplikacji, ale prawo obecnie nie możemy dodać wszystkie punkty przerwania lub wykonywane jakieś szczególne zbadanie kodu. Tak właśnie ładuje aplikację i Zobacz obrazy zdjęcie.

     W tym samouczku możemy zająć bliższe spojrzenie na tej aplikacji za pomocą debugera i pobrać przyjrzeć się debuger funkcji.

5. Zatrzymywanie działania debugera przez naciśnięcie przycisku Zatrzymaj red ![Zatrzymaj debugowanie](../debugger/media/dbg-tour-stop-debugging.png "Zatrzymaj debugowanie") przycisku.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Ustaw punkt przerwania i uruchomienia debugera

Aby debugować, należy uruchomić aplikację w debugerze procesu aplikacji.

1. W `MainWindow` Konstruktor MainWindow.xaml.cs, ustaw punkt przerwania, klikając na lewym marginesie pierwszy wiersz kodu.

     ![Ustaw punkt przerwania](../debugger/media/dbg-tour-set-a-breakpoint.gif "SetABreakPoint")

6. Naciśnij klawisz F5 lub **Rozpocznij debugowanie** przycisk uruchamiania aplikacji i debuger uruchamia do wiersza kodu, którym można ustawić punktu przerwania.

    Żółta strzałka reprezentuje instrukcję, w której debuger wstrzymana, również wstrzymuje wykonywanie aplikacji w tym samym punkcie (Ta instrukcja nie wykonane).

    F5 jest nadal uruchomiona aplikacja do następnego punktu przerwania. (Jeśli aplikacja nie jest jeszcze uruchomiona, F5 uruchomienie debugera i zatrzymuje się na pierwszym punktu przerwania.)

    Punkty przerwania są to przydatne, gdy wiesz, wiersz kodu lub części kodu, który ma zostać zbadany szczegółowo.

## <a name="restart-your-app-quickly"></a>Szybkie ponowne uruchomienie aplikacji

Kliknij przycisk **Uruchom ponownie** ![ponowne uruchomienie aplikacji](../debugger/media/dbg-tour-restart.png "RestartApp") przycisku w pasku narzędzi debugowania (Ctrl + Shift + F5).

Po naciśnięciu **ponowne uruchomienie**, można zaoszczędzić czas i zatrzymywanie aplikacji i ponowne uruchamianie debugera. Debuger wstrzymuje na pierwszy punkt przerwania, który zostaje trafiony za wykonywanie kodu.

Debuger ponownie zatrzymuje się na punkt przerwania, należy ustawić w `MainWindow` konstruktora.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Przejdź do kodu w debugerze przy użyciu poleceń krokowych

Przede wszystkim, używamy skróty klawiaturowe w tym miejscu, ponieważ jest on sposobem uzyskania przy wykonywania aplikacji w debugerze (odpowiednik polecenia takie jak menu poleceń są wyświetlane w nawiasach).

1. Naciśnij klawisz F11 (**debugowania > Wkrocz**) dwa razy, aby poprawić wykonywania aplikacji `InitializeComponent()` funkcji.

     ![Umożliwia F11 kod Step Into](../debugger/media/dbg-tour-f11.png "F11 Step Into")

     Jest F11 **Step Into** poleceń i zmienia aplikacji wykonanie jednej instrukcji w czasie. F11 jest dobrym sposobem Sprawdź przepływ wykonania w najbardziej szczegółowy. (Aby szybciej niż przy użyciu kodu, możemy opisano niektóre inne opcje również.) Domyślnie debuger nakłada się na kodu innych użytkowników (Aby uzyskać więcej szczegółów, zobacz [tylko mój kod](../debugger/just-my-code.md)).

     >[!NOTE]
     > W kodzie zarządzanym zobaczysz okno dialogowe z pytaniem, jeśli chcesz otrzymać powiadomienie, gdy automatycznie wkroczyć nad właściwościami i operatorami (domyślnie). Jeśli chcesz zmienić ustawienie później, wyłącz **Przekrocz nad właściwościami i operatorami** w **Narzędzia > Opcje** menu w obszarze **debugowanie**.

2. Naciśnij klawisz F10 (**Debuguj > Step Over**) kilka razy, aż debuger zatrzymuje się w pierwszym wierszu kodu w `OnApplicationStartup` obsługi zdarzeń.

     ![Użyj F10, aby kod Step Over](../debugger/media/dbg-tour-f10-step-over.png "F10 Step Over")

     F10 wyjście z kodu bez Wkraczanie do funkcji lub metody w kodzie aplikacji (kod nadal wykonuje). Naciskając F10 `InitializeComponent` wywołanie metody (zamiast F11), możemy pominięte przez kod implementacji `InitializeComponent` (które może być firma Microsoft nie interesuje w tej chwili).

## <a name="step-into-a-property"></a>Wkraczać do właściwości

1. Z debugera wstrzymana na ten wiersz kodu:

    ````
    mainWindow.Photos.Path = Environment.CurrentDirectory + "\\images";
    ````

    Kliknij prawym przyciskiem myszy na linii kodu i wybierz polecenie **Wkrocz do określonego**, następnie **SDKSamples.ImageSample.PhotoCollection.Path.set**

     ![Krok do określonych funkcji](../debugger/media/dbg-tour-step-into-specific.png "Wkrocz do określonego")

    Jak wspomniano wcześniej, domyślnie debuger nakłada się na zarządzaną i pól, ale **Wkrocz do określonego** polecenie pozwala zmienić to zachowanie. Teraz chcemy Szukaj, co się stanie, gdy `Path.set` uruchamia metody ustawiającej właściwość. **Wkrocz do określonego** pobiera nam `Path.set` kodu w tym miejscu.

     ![wynik Wkrocz do określonego](../debugger/media/dbg-tour-step-into-specific-2.png "Wkrocz do określonego")

     `Update` w tym kodzie wygląda tak, może to być przydatne, tak pozwala użyć debugera do sprawdzenia kodu bliskiej.

5. Umieść kursor nad `Update` metody do momentu zielonego **Uruchom kliknięcie** przycisk ![Uruchom kliknięcie](../debugger/media/dbg-tour-run-to-click.png "RunToClick") pojawia się po lewej stronie.

     ![Za pomocą polecenia Uruchom kliknięcie funkcji](../debugger/media/dbg-tour-run-to-click-2.png "Uruchom kliknięcie")

    >  [!NOTE] 
    > **Uruchom kliknięcie** przycisku jest nowa w programie [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]. Jeśli nie widzisz przycisku zieloną strzałkę, użyj F11 w tym przykładzie można poprawić debugera.

6. Kliknij przycisk **Uruchom kliknięcie** przycisk ![Uruchom kliknięcie](../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    Za pomocą tego przycisku jest podobne do tymczasowego punktu przerwania. **Uruchom kliknięcie** jest przydatna do poruszania się szybko w obrębie regionu widoczne kodu aplikacji (kliknięcie w dowolnym Otwieranie pliku).

    Przejście do debugera `Update` implementacji metody.

7. Naciśnij klawisz F11, aby wkraczać do `Update` metody.

     ![Wynik Wkraczanie do metody aktualizacji](../debugger/media/dbg-tour-update-method.png "krok do aktualizacji — metoda")

    W tym miejscu znaleźliśmy więcej kodu wyglądająca interesujące; aplikacja otrzymuje wszystkie pliki *.jpg znajdującej się w określonym katalogu, a następnie utworzenie obiektu fotografii dla każdego pliku. Ten kod daje możliwość uruchomienia sprawdzania stanu Twojej aplikacji (zmienne) z debugera. Firma Microsoft będzie zrobić w kolejnych sekcjach tego samouczka.

    Funkcje, które pozwalają sprawdzić zmienne są jednym z najbardziej przydatnych funkcji debugera i są to robić na różne sposoby. Często podczas debugowania problemu, próbujesz sprawdzić, czy zmienne są przechowywane wartości, które powinni mieć w określonym czasie.

## <a name="examine-the-call-stack"></a>Sprawdź stosu wywołań

Podczas wstrzymania w `Update` metody, kliknij przycisk **stos wywołań** okna, które jest domyślnie otwarty w dolnym okienku po prawej stronie.

![Sprawdź stos wywołań](../debugger/media/dbg-tour-call-stack.png "ExamineCallStack")

**Stos wywołań** okno zawiera kolejność, w którym są pobierania wywoływane metody i funkcje. Górny wiersz zawiera bieżącą funkcję ( `Update` metody w aplikacji samouczka). Drugi wiersz wskazuje, że `Update` została wywołana z `Path.set` właściwości i tak dalej.

>  [!NOTE]
> **Stos wywołań** jest podobne do perspektywy debugowania w niektórych IDEs, takich jak Eclipse.

Stos wywołań jest dobrze do badania i zrozumienie przepływu wykonywania aplikacji.

Możesz kliknąć dwukrotnie linię kod Przyjrzyj się tej kodu źródłowego i zmienia także bieżącego zakresu kontrolowanym przez debuger. Ta akcja nie poprawić debugera.

Można również użyć menu kliknij prawym przyciskiem myszy **stos wywołań** okno, aby wykonać inne czynności. Na przykład można wstawić punktów przerwania do określonych funkcji, wcześniejsze debuger przy użyciu **Uruchom do kursora**i przejdź zbadanie kodu źródłowego. Aby uzyskać więcej informacji, zobacz [porady: Sprawdź stos wywołań](../debugger/how-to-use-the-call-stack-window.md).

## <a name="step-out"></a>Wyjdź

Załóżmy, że wszystko będzie gotowe badanie `Update` metody Data.cs, i chcesz uzyskać z funkcji, ale pozostają w debugerze. Można to zrobić za pomocą **Wyjdź** polecenia.

1. Naciśnij klawisze Shift + F11 (lub **Debuguj > Wyjdź**).

     To polecenie wznawia wykonywanie aplikacji (i wyjście z kodu) do momentu zwraca bieżącej funkcji.

     Należy ponownie `Update` wywołania metody w Data.cs.

2. Naciśnij klawisze Shift + F11 ponownie i debuger umieszczane w górę stosu wywołań z powrotem do `OnApplicationStartup` obsługi zdarzeń.

## <a name="run-to-cursor"></a>Uruchom do kursora

1. Wybierz **Zatrzymaj debugowanie** czerwony przycisk ![Zatrzymaj debugowanie](../debugger/media/dbg-tour-stop-debugging.png "Zatrzymaj debugowanie") lub Shift + F5.

2. W `Update` metody w Data.cs, kliknij prawym przyciskiem myszy `Add` metody wywołań i wybierz polecenie **Uruchom do kursora**. To polecenie uruchamia profilowanie i ustawia w bieżącym wierszu kodu tymczasowej punktu przerwania.

     ![Użyj Uruchom, aby funkcja kursora](../debugger/media/dbg-tour-run-to-cursor.png "Uruchom do kursora")

    Powinien być wstrzymane na punkt przerwania w `MainWindow` (ponieważ jest pierwszy punkt przerwania został skonfigurowany).

3. Naciśnij klawisz F5, aby przejść do `Add` po wybraniu metody **Uruchom do kursora**.

    To polecenie jest przydatne podczas edytowania kodu i chcesz szybko ustawić punkt przerwania tymczasowego i uruchomienia debugera.

## <a name="change-the-execution-flow"></a>Przepływ wykonania zmian

1. Z debugera wstrzymana na `Add` wywołania metody, za pomocą myszy do pobrania żółta strzałka (wskaźnik wykonywania) po lewej stronie i Przenieś żółta strzałka w górę o jeden wiersz do `foreach` pętli.

     ![Przesuń wskaźnik wykonywania](../debugger/media/dbg-tour-move-the-execution-pointer.gif "wskaźnika wykonywania")

    Zmieniając przepływu wykonywania, możesz to zrobić rzeczy, takich jak przetestować różne ścieżki wykonywania lub uruchom ponownie kodu bez ponownego uruchamiania debugera.

2. Teraz naciśnij klawisz F5.

    Widać obrazy dodane do okna aplikacji. Ponieważ są ponowne uruchamianie kodu w `foreach` pętli, niektóre obrazy zostały dodane dwa razy!
    
    > [!WARNING]
    > Często należy zachować ostrożność przy użyciu tej funkcji i zostanie wyświetlone ostrzeżenie w etykietce narzędzia. Zbyt mogą pojawić się inne ostrzeżenia. Przesuń wskaźnik nie można przywrócić aplikację do wcześniejszego stanu aplikacji.

## <a name="inspect-variables-with-data-tips"></a>Sprawdź zmienne etykietki danych

1. Otwórz Data.cs w aplikacji demonstracyjnej podgląd fotografii, kliknij prawym przyciskiem myszy `private void Update` deklaracji funkcji i wybierz polecenie **Uruchom do kursora** (Zatrzymaj aplikację najpierw Jeśli jest już uruchomiona).

    Wstrzyma aplikacji w debugerze. Umożliwia firmie Microsoft w celu zbadania stanu.

2. Umieść kursor nad `Add` metodę wywołania i kliknij przycisk **Uruchom kliknięcie** przycisk ![Uruchom kliknięcie](../debugger/media/dbg-tour-run-to-click.png "RunToClick").

3. Teraz, umieść kursor nad obiektu pliku (`f`) i sprawdź wartość właściwości domyślną nazwę pliku `market 031.jpg`.

     ![Wyświetl etykietki danych](../debugger/media/dbg-tour-data-tips.gif "wyświetlenia etykietki danych")

4. Rozwiń obiekt, aby wyświetlić wszystkie właściwości, takie jak `FullPath` właściwości.

    Często podczas debugowania, chcesz szybko sprawdzić wartości właściwości obiektów i etykietki danych to dobry sposób, aby wykonać to zadanie.

    > [!TIP]
    > W najbardziej obsługiwanych języków można edytować kodu w trakcie wykonywania sesji debugera, jeśli okaże się coś, co chcesz zmienić. Aby uzyskać więcej informacji, zobacz [Edytuj i Kontynuuj](../debugger/edit-and-continue.md). Aby użyć tej funkcji w tej aplikacji, jednak będą najpierw musimy zaktualizować wersję aplikacji programu .NET Framework.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Sprawdź zmienne z automatycznych i ustawień regionalnych systemu windows

1. Przyjrzyj się **automatycznych** okna w dolnej części edytora kodu.

     ![Sprawdź zmienne w okno zmiennych automatycznych](../debugger/media/dbg-tour-autos-window.png "okno zmiennych automatycznych")

    W **automatycznych** okna, zobacz zmienne i ich bieżącą wartość. **Automatycznych** wszystkie zmienne używane w poprzednim wierszu lub bieżący wiersz zawiera okna (w języku C++ okna zawiera zmienne w poprzednim trzy wiersze kodu. Dokumentacji zachowanie specyficzne dla języka).

    > [!NOTE]
    > W języku JavaScript **zmiennych lokalnych** okna jest nie obsługiwane **automatycznych** okna.

2. Następnie przyjrzeć się **zmiennych lokalnych** okna.

    **Zmiennych lokalnych** okno zawiera zmienne, które znajdują się w bieżącym zakresie.

    ![Sprawdź zmienne w oknie zmienne lokalne](../debugger/media/dbg-tour-locals-window.png "okno zmiennych lokalnych")

    Obecnie `this` obiektu i obiekt pliku (`f`) znajdują się w bieżącym zakresie. Aby uzyskać więcej informacji, zobacz [sprawdzić zmiennych w automatycznych i zmiennych lokalnych Windows](../debugger/autos-and-locals-windows.md).

## <a name="set-a-watch"></a>Ustaw czujki

1. W oknie edytora kodu głównym kliknij prawym przyciskiem myszy obiekt pliku (`f`) i wybierz polecenie **Dodaj wyrażenie kontrolne**.

    Można użyć **czujki** okna, aby określić zmienną (lub wyrażenie), który chcesz śledzić na.

    Teraz masz czujki, ustawiać `File` obiekt, aby sprawdzić jego wartość zmienić podczas przeglądania przez debuger. W przeciwieństwie do innych zmiennych systemu windows **czujki** okno zawsze zawiera zmienne możesz obserwowanie (one jest wyszarzona kiedy poza zakresem).

2. Na `Add` metody, kliknij zielony ![Uruchom kliknięcie](../debugger/media/dbg-tour-run-to-click.png "RunToClick") przycisk ponownie (lub naciśnij klawisz F11 kilka razy) odszukaj `foreach` pętli.

    ![Ustaw czujki w zmiennej](../debugger/media/dbg-tour-watch-window.png "okno czujki")

    Może być również wyświetlany obraz pierwszego zostaną dodane do głównego okna działanie przykładowej aplikacji, ale działa w wątku innej aplikacji, obrazy mogą nie być widoczne jeszcze.

    Aby uzyskać więcej informacji, zobacz [ustawić czujki, przy użyciu czujki i QuickWatch systemu Windows](../debugger/watch-and-quickwatch-windows.md)

## <a name="examine-an-exception"></a>Sprawdź Wystąpił wyjątek

1. W oknie aplikacji uruchomionej Usuń tekst **ścieżki** pole wejściowe, a następnie wybierz **zmiany** przycisku.

     ![Wyjątek był zgłaszany](../debugger/media/dbg-tour-cause-an-exception.png "spowodowało wyjątku")

     Aplikacja zgłasza wyjątek i debuger przejście do wiersza kodu, która zgłosiła wyjątek.
     
     ![Pomocnik wyjątków](../debugger/media/dbg-tour-exception-helper.png "pomocnika wyjątków")

     W tym miejscu **pomocnika wyjątków** pokazuje `System.ArgumentException` i komunikat o błędzie z informacją, że ścieżka nie jest niedozwolony format. Tak wiemy, że wystąpił błąd na argumentu metody lub funkcji.

     W tym przykładzie `DirectoryInfo` wywołania nadać błąd na pusty ciąg, przechowywane w `value` zmiennej. (Umieść kursor nad `value` wyświetlić pusty ciąg.)

     Pomocnik wyjątków jest doskonałym funkcja, która może pomóc w debugowaniu błędy. Można również wykonywać następujące czynności widoku Szczegóły błędu i Dodaj wyrażenie kontrolne pomocnika wyjątków. Lub, w razie potrzeby można zmienić warunki zgłaszanie określonego wyjątku.

    >  [!NOTE] 
    > Pomocnik wyjątków zastępuje Asystenta wyjątków w [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

2. Rozwiń węzeł **ustawienia wyjątków** węzeł, aby wyświetlić więcej opcji, w jaki sposób obsługiwać ten typ wyjątku, ale nie ma potrzeby zmian w tym samouczku!

3. Naciśnij klawisz F5, aby kontynuować aplikacji.

Aby dowiedzieć się więcej na temat funkcji debugera, zobacz [debugera porady i wskazówki](../debugger/debugger-tips-and-tricks.md).

## <a name="next-steps"></a>Następne kroki

W tym samouczku kiedy znasz już sposobu uruchamiania debugera, kroki do kodu i sprawdzić zmiennych. Możesz pobrać wysokiego poziomu przyjrzeć się debuger funkcji oraz łącza do dodatkowych informacji.

> [!div class="nextstepaction"]
> [Przewodnik po funkcjach debugera](../debugger/debugger-feature-tour.md)
