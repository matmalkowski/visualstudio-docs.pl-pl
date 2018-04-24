---
title: Analizowanie danych użycia procesora CPU (zarządzany kod) | Dokumentacja firmy Microsoft
ms.custom: ''
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
- dotnet
ms.openlocfilehash: cac26376df6a5e7dc26b55e07fbebe240b1511de
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="analyze-cpu-usage-data-in-visual-studio-managed-code"></a>Analizowanie danych użycia procesora CPU w programie Visual Studio (zarządzany kod)

Program Visual Studio udostępnia wiele zaawansowanych funkcji, które ułatwiają analizowanie problemy z wydajnością w aplikacji. Ten temat zawiera szybko dowiedzieć się, niektóre podstawowe funkcje. W tym miejscu przyjrzymy się narzędzie w celu zidentyfikowania wąskich gardeł wydajności z powodu wysokiego użycia procesora CPU. Narzędzia diagnostyczne są obsługiwane dla .NET development w Visual Studio, w tym aplikacji ASP.NET i programowania w języku macierzystym/C++.

Centrum diagnostyki oferuje wiele innych opcji do zarządzania sesję diagnostyczną. Jeśli **użycie procesora CPU** narzędzia opisanego w tym miejscu nie zapewnia dane, które chcesz dodać, [innych narzędzi do profilowania](../profiling/profiling-feature-tour.md) zapewniają różne rodzaje informacji, które mogą być przydatne do Ciebie. W wielu przypadkach wąskie gardło aplikacji może być spowodowane przez inną niż Procesora, pamięci, renderowania interfejsu użytkownika lub czas żądania sieciowego. Centrum diagnostyki oferuje wiele innych opcji, aby rejestrować i analizować tego typu danych.

> [!NOTE]
> Dla platformy .NET Core i ASP.NET Core narzędzia użycie procesora CPU aktualnie nie zawiera prawidłowych wyników z PBDs przenośnej. Zamiast tego użyj pełne pliki PDB.

## <a name="create-a-project"></a>Tworzenie projektu

1. W programie Visual Studio, wybierz **Plik > Nowy projekt**.

2. W obszarze **Visual C#** lub **Visual Basic**, wybierz **klasycznego pulpitu systemu Windows**, a następnie w środkowym okienku wybierz **aplikacji konsoli (.NET Framework)**.

3. Wpisz nazwę, takich jak **MyProfilerApp** i kliknij przycisk **OK**.

    Program Visual Studio tworzy projekt.

2. Otwórz plik Program.cs i Zastąp cały kod z następującym kodem:

    ```cs
    using System;
    using System.Threading;
    public class ServerClass
    {
        const int MIN_ITERATIONS = int.MaxValue / 1000;
        const int MAX_ITERATIONS = MIN_ITERATIONS + 10000;
    
        long m_totalIterations = 0;
        readonly object m_totalItersLock = new object();
        // The method that will be called when the thread is started.
        public void DoWork()
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
        public static void Main()
        {
            for (int i = 0; i < 200; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();
    
            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.DoWork));
            // Start the thread.
            InstanceCaller.Start();
    
            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");
    
        }
    }
    ```

    ```vb
    Imports System
    Imports System.Threading
    
    Namespace MyProfilerApp
        Public Class ServerClass
            Const MIN_ITERATIONS As Integer = Integer.MaxValue / 1000
            Const MAX_ITERATIONS As Integer = MIN_ITERATIONS + 10000
    
            Private m_totalIterations As Long = 0
            ReadOnly m_totalItersLock As New Object()
            ' The method that will be called when the thread is started.
            Public Sub DoWork()
                Console.WriteLine("ServerClass.InstanceMethod is running on another thread.")
    
                Dim x = GetNumber()
            End Sub
    
            Private Function GetNumber() As Integer
                Dim rand = New Random()
                Dim iters = rand.[Next](MIN_ITERATIONS, MAX_ITERATIONS)
                Dim result = 0
                SyncLock m_totalItersLock
                    m_totalIterations += iters
                End SyncLock
                ' we're just spinning here  
                ' and using Random to frustrate compiler optimizations  
                For i As Integer = 0 To iters - 1
                    result = rand.[Next]()
                Next
                Return result
            End Function
        End Class
    
        Public Class Simple
            Public Shared Sub Main()
                For i As Integer = 0 To 199
                    CreateThreads()
                Next
            End Sub
            Public Shared Sub CreateThreads()
                Dim serverObject As New ServerClass()
    
                Dim InstanceCaller As New Thread(New ThreadStart(AddressOf serverObject.DoWork))
                ' Start the thread.
                InstanceCaller.Start()
    
                Console.WriteLine("The Main() thread calls this after " + "starting the new InstanceCaller thread.")
    
            End Sub
        End Class
    End Namespace
    ```

    > [!NOTE]
    > W języku Visual Basic, upewnij się, ma ustawioną wartość obiektu uruchamiania `Sub Main` (**właściwości > aplikacji > obiekt uruchomieniowy**).

##  <a name="BKMK_Quick_start__Collect_diagnostic_data"></a> Krok 1: Zbieranie danych profilowania 
  
1.  Najpierw należy ustawić punkt przerwania w aplikacji w tym wierszu kodu w `Main` funkcji:

    `for (int i = 0; i < 200; i++)`

    lub, w języku Visual Basic:

    `For i As Integer = 0 To 199`

    Ustaw punkt przerwania, klikając w odstępu w lewo wiersz kodu.

2.  Następnie ustaw drugiego punktu przerwania na zamykający nawias klamrowy na końcu `Main` funkcji:

     ![Ustaw punkty przerwania dla profilowania](../profiling/media/quickstart-cpu-usage-breakpoints.png "Ustaw punkty przerwania do profilowania")

    > [!TIP]
    > Ustawiając dwa punkty przerwania, można ograniczyć zbieranie danych do części kodu, który chcesz przeanalizować.
  
3.  **Narzędzia diagnostyczne** okno jest już widoczny, jeśli wyłączono go. Aby wyświetlić okno ponownie, kliknij przycisk **Debug / Windows / Pokaż narzędzia diagnostyczne**.

4.  Kliknij przycisk **Debug / Rozpocznij debugowanie** (lub **Start** na pasku narzędzi lub **F5**).

     Gdy aplikacja zakończy ładowania, **Podsumowanie** zostanie wyświetlony widok narzędzi diagnostycznych.

5.  Gdy debuger jest wstrzymana, Włącz zbierania danych użycia procesora CPU, wybierając **rekord Procesora profilu**, a następnie otwórz **użycie procesora CPU** kartę.

     ![Narzędzia diagnostyki Włącz profilowanie procesora CPU](../profiling/media/quickstart-cpu-usage-summary.png "narzędzi diagnostycznych Włącz profilowanie procesora CPU")

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

     ![Diagnostyka narzędzia użycie procesora CPU kartę](../profiling/media/quickstart-cpu-usage-cpu.png "DiagToolsCPUUsageTab")

    > [!TIP]
    > Funkcje są wymienione w kolejności, począwszy od tych czynności najbardziej pracy (nie są one w kolejności wywołania). Dzięki temu można szybko zidentyfikować najdłuższym funkcje uruchomione.

2. Na liście funkcji kliknij dwukrotnie `ServerClass::GetNumber` funkcji.

    Po dwukrotnym kliknięciu funkcji **wywołujący/wywoływany** widok zostanie otwarty w okienku po lewej stronie. 

    ![Widok wywoływany obiekt wywołujący narzędzi diagnostycznych](../profiling/media/quickstart-cpu-usage-caller-callee.png "DiagToolsCallerCallee")

    W tym widoku wybranej funkcji zostaną wyświetlone w nagłówku, a w **bieżącej funkcji** pola (`GetNumber`, w tym przykładzie). Funkcji, które wywołały bieżącą funkcję jest wyświetlany po lewej stronie w obszarze **podczas wywoływania funkcji**, a wszystkie funkcje wywoływane przez bieżącą funkcję są wyświetlane w **funkcji o nazwie** pole po prawej stronie. (Wybierz albo pola, aby zmienić bieżącą funkcję).

    Ten widok przedstawia łączny czas (ms) i odsetek ogólną aplikacji czasu podejmujący funkcja do wykonania działania.

    **Treść funkcji** również przedstawia łączną ilość czasu (i wartość procentowa czasu) w treści funkcji bez czasu poświęcony na wywołanie i wywołać funkcji. (Na tej ilustracji 2856 poza 2863 ms zostały spędzony w treści funkcji i pozostały czas (< 20 ms) był poświęcony w kodzie zewnętrznych wywoływanych przez tę funkcję). Rzeczywiste wartości może się różnić w zależności od środowiska.

    > [!TIP]
    > Wysokiej wartości w **treści funkcji** może wskazywać wąskie gardło w samej funkcji.

## <a name="next-steps"></a>Następne kroki

- [Analizowanie użycia pamięci](../profiling/memory-usage.md)do zidentyfikowania wąskich gardeł wydajności.
- [Analiza użycia procesora CPU](../profiling/cpu-usage.md) uzyskać więcej szczegółowych informacji na temat narzędzia użycie procesora CPU.
- Analiza użycia Procesora bez istnieje debuger dołączony lub wybierając uruchomionej aplikacji — Aby uzyskać więcej informacji, zobacz [zbierania danych profilowania bez debugowania](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) w [uruchomienie narzędzia z lub bez debuger profilowania](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="see-also"></a>Zobacz też  

 [Profilowanie w programie Visual Studio](../profiling/index.md)  
 [Przewodnik po funkcjach profilowania](../profiling/profiling-feature-tour.md)
