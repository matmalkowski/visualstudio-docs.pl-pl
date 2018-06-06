---
title: Analizowanie danych użycia procesora CPU (ASP.NET)
description: Mierzyć wydajność aplikacji w aplikacji ASP.NET przy użyciu narzędzia diagnostycznego użycie procesora CPU
ms.custom: mvc
ms.date: 12/05/2017
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 00704c236e8e0c0453a36add4cb4603b76c31bd9
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34477291"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-aspnet"></a>Szybki Start: Analizowanie danych użycia procesora CPU w Visual Studio (ASP.NET)

Program Visual Studio udostępnia wiele zaawansowanych funkcji, które ułatwiają analizowanie problemy z wydajnością w aplikacji. Ten temat zawiera szybko dowiedzieć się, niektóre podstawowe funkcje. W tym miejscu przyjrzymy się narzędziem do zidentyfikowania wąskich gardeł wydajności z powodu wysokiego użycia procesora CPU. Narzędzia diagnostyczne są obsługiwane dla .NET development w Visual Studio, w tym aplikacji ASP.NET i programowania w języku macierzystym/C++.

Centrum diagnostyki oferuje wiele innych opcji do zarządzania sesję diagnostyczną. Jeśli **użycie procesora CPU** narzędzia opisanego w tym miejscu nie zapewnia dane, które chcesz dodać, [innych narzędzi do profilowania](../profiling/Profiling-Tools.md) zapewniają różne rodzaje informacji, które mogą być przydatne do Ciebie. W wielu przypadkach wąskie gardło aplikacji może być spowodowane przez inną niż Procesora, pamięci, renderowania interfejsu użytkownika lub czas żądania sieciowego.

> [!NOTE]
> Dla platformy .NET Core i ASP.NET Core narzędzia użycie procesora CPU aktualnie nie zawiera prawidłowych wyników z PBDs przenośnej. Zamiast tego użyj pełne pliki PDB.

## <a name="create-a-project"></a>Tworzenie projektu

1. W programie Visual Studio, wybierz **Plik > Nowy projekt**.

1. W obszarze **Visual C#**, wybierz **Web**, a następnie w środkowym okienku wybierz **aplikacji sieci Web platformy ASP.NET (.NET Framework)**.

    > [!NOTE]
    > Narzędzia użycie procesora CPU nie jest obecnie obsługiwane w ASP.NET Core.

1. Wpisz nazwę, takich jak **MyProfilingApp_MVC** i kliknij przycisk **OK**.

1. W oknie dialogowym wybierz **MVC** w środkowym okienku, a następnie kliknij przycisk **OK**.

    Program Visual Studio tworzy projekt. Eksplorator rozwiązań (po prawej) zawiera pliki projektu.

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy folder modeli, a następnie wybierz pozycję **Dodaj** > **klasy**.

1. Nazwa nowej klasy `Data.cs` i wybierz polecenie **Dodaj**.

1. W Eksploratorze rozwiązań Otwórz `Models/Data.cs` i dodaj następującą `using` instrukcji na początku pliku:

    ```csharp
    using System.Threading;
    ```

1. W Data.cs Zastąp następujący kod:

    ```csharp
    public class Data
    {
    }
    ```

    o tym kodzie:

    ```csharp
    public class ServerClass
    {
        const int MIN_ITERATIONS = int.MaxValue / 1000;
        const int MAX_ITERATIONS = MIN_ITERATIONS + 10000;

        long m_totalIterations = 0;
        readonly object m_totalItersLock = new object();
        // The method that will be called when the thread is started.
        public void GenerateData()
        {
            Console.WriteLine(
                "ServerClass.InstanceMethod is running on another thread.");

            var x = GetNumber();
        }

        private int GetNumber()
        {
            var rand = new Random();
            var iters = rand.Next(MIN_ITERATIONS, MAX_ITERATIONS);
            var result = 0;
            lock (m_totalItersLock)
            {
                m_totalIterations += iters;
            }
            // we're just spinning here  
            // and using Random to frustrate compiler optimizations  
            for (var i = 0; i < iters; i++)
            {
                result = rand.Next();
            }
            return result;
        }
    }

    public class Simple
    {
        int numberOfThreads = 200;

        public Simple()
        {
            for (int i = 0; i < numberOfThreads; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.GenerateData));
            // Start the thread.
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }

        public int GetData()
        {
            // Not returning any meaningful data.
            return numberOfThreads;
        }
    }
    ```

1. W Eksploratorze rozwiązań Otwórz Controller/HomeControllers.cs i Zastąp następujący kod:

    ```csharp
    public ActionResult About()
    {
        ViewBag.Message = "Your application description page.";

        return View();
    }
    ```

    o tym kodzie:

    ```csharp
    public ActionResult About()
    {
        Models.Simple s = new Models.Simple();

        ViewBag.Message = "Your application description page.";

        return View(s.GetData());
    }
    ```

##  <a name="BKMK_Quick_start__Collect_diagnostic_data"></a> Krok 1: Zbieranie danych profilowania 
  
1.  Najpierw należy ustawić punkt przerwania w aplikacji w tym wierszu kodu w `Simple` konstruktora:

    `for (int i = 0; i < 200; i++)`

    Ustaw punkt przerwania, klikając w odstępu w lewo wiersz kodu.

1.  Następnie ustaw drugiego punktu przerwania na zamykający nawias klamrowy na końcu `Simple` konstruktora:

     ![Ustaw punkty przerwania do profilowania](../profiling/media/quickstart-cpu-usage-breakpoints-aspnet.png)

    > [!TIP]
    > Ustawiając dwa punkty przerwania, można ograniczyć zbieranie danych do części kodu, który chcesz przeanalizować.
  
1.  **Narzędzia diagnostyczne** okno jest już widoczny, jeśli wyłączono go. Aby wyświetlić okno ponownie, kliknij przycisk **Debug / Windows / Pokaż narzędzia diagnostyczne**.

1.  Kliknij przycisk **Debug / Rozpocznij debugowanie** (lub **Start** na pasku narzędzi lub **F5**).

1.  Po zakończeniu ładowania aplikacji kliknij przycisk **o** łącze u góry strony sieci web, aby rozpocząć Uruchamianie nowego kodu.

1.  Przyjrzyj się **Podsumowanie** zostanie wyświetlony widok narzędzi diagnostycznych.

1.  Gdy debuger jest wstrzymana, Włącz zbierania danych użycia procesora CPU, wybierając **rekord Procesora profilu**, a następnie otwórz **użycie procesora CPU** kartę.

     ![Narzędzia diagnostyki Włącz profilowanie procesora CPU](../profiling/media/quickstart-cpu-usage-summary.png)

     Po włączeniu funkcji zbierania danych, przycisk rekordu wyświetla czerwonym kółku.

     Po wybraniu **rekord Procesora profilu**, Visual Studio rozpocznie się rejestrowanie funkcji i jak długo podjęte w celu wykonania i udostępnia również wykres osi czasu, można skupić się na poszczególnych segmentów sesji próbkowania. Zebrane dane można przeglądać tylko wtedy, gdy aplikacja jest zatrzymywane w punkcie przerwania.

6.  Naciśnij klawisz F5, aby uruchomić aplikację na drugi punkt przerwania.

     Teraz masz teraz dane dotyczące wydajności aplikacji specjalnie dla regionu kodu, który uruchamia między dwoma punktami przerwań.

     Profiler rozpoczyna przygotowywania danych wątku. Poczekaj na jego zakończenie.
  
     Użycie procesora CPU narzędzie wyświetla raport w **użycie procesora CPU** kartę.

     W tym momencie można rozpocząć do analizowania danych.

## <a name="Step2"></a> Krok 2: Analizowanie danych użycia procesora CPU

Zalecamy rozpocząć analizowanie danych, sprawdzając listę funkcji zgodnie z użycia procesora CPU, identyfikowanie funkcji, które robią najbardziej pracy i następnie biorąc bliższe spojrzenie na każdym z nich.

1. Na liście funkcji badania funkcji, które robią większość pracy.

     ![Diagnostyka narzędzi kartę użycie procesora CPU](../profiling/media/quickstart-cpu-usage-cpu-aspnet.png)

    > [!TIP]
    > Funkcje są wymienione w kolejności, począwszy od tych czynności najbardziej pracy (nie są one w kolejności wywołania). Dzięki temu można szybko zidentyfikować najdłuższym funkcje uruchomione.

2. Na liście funkcji kliknij dwukrotnie `MyProfilingApp_MVC.Models.ServerClass::GetNumber` funkcji.

    Po dwukrotnym kliknięciu funkcji **wywołujący/wywoływany** widok zostanie otwarty w okienku po lewej stronie. 

    ![Widok wywoływany obiekt wywołujący narzędzia diagnostyczne](../profiling/media/quickstart-cpu-usage-caller-callee-aspnet.png)

    W tym widoku wybranej funkcji zostaną wyświetlone w nagłówku, a w **bieżącej funkcji** pola (`ServerClass::GetNumber`, w tym przykładzie). Funkcji, które wywołały bieżącą funkcję jest wyświetlany po lewej stronie w obszarze **podczas wywoływania funkcji**, a wszystkie funkcje wywoływane przez bieżącą funkcję są wyświetlane w **funkcji o nazwie** pole po prawej stronie. (Wybierz albo pola, aby zmienić bieżącą funkcję).

    Ten widok przedstawia łączny czas (ms) i odsetek ogólną aplikacji czasu podejmujący funkcja do wykonania działania.

    **Treść funkcji** również przedstawia łączną ilość czasu (i wartość procentowa czasu) w treści funkcji bez czasu poświęcony na wywołanie i wywołać funkcji. (Na tej ilustracji 2220 poza 2235 ms zostały spędzony w treści funkcji i pozostały czas (< 20 ms) był poświęcony w kodzie zewnętrznych wywoływanych przez tę funkcję). Rzeczywiste wartości może się różnić w zależności od środowiska.

    > [!TIP]
    > Wysokiej wartości w **treści funkcji** może wskazywać wąskie gardło w samej funkcji.

## <a name="next-steps"></a>Następne kroki

- [Analizowanie użycia pamięci](../profiling/memory-usage.md)do zidentyfikowania wąskich gardeł wydajności.
- [Analiza użycia procesora CPU](../profiling/cpu-usage.md) uzyskać więcej szczegółowych informacji na temat narzędzia użycie procesora CPU.
- Analiza użycia Procesora bez istnieje debuger dołączony lub wybierając uruchomionej aplikacji — Aby uzyskać więcej informacji, zobacz [zbierania danych profilowania bez debugowania](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) w [uruchomienie narzędzia z lub bez debuger profilowania](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="see-also"></a>Zobacz też  

 [Profilowanie w programie Visual Studio](../profiling/index.md)  
 [Przewodnik po funkcjach profilowania](../profiling/profiling-feature-tour.md)
