---
title: "Analizowanie danych użycia procesora CPU (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 12/05/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: quickstart
f1_keywords: 
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f2fcd8eee11876853ce51c154e740cdb91015662
ms.sourcegitcommit: 64c7682ec3a2cbea684e716803398d4278b591d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2017
---
# <a name="analyze-cpu-usage-data-in-visual-studio-c"></a>Analizowanie danych użycia procesora CPU w Visual Studio (C++)

Program Visual Studio udostępnia wiele zaawansowanych funkcji, które ułatwiają analizowanie problemy z wydajnością w aplikacji. Ten temat zawiera szybko dowiedzieć się, niektóre podstawowe funkcje. W tym miejscu przyjrzymy się narzędzie w celu zidentyfikowania wąskich gardeł wydajności z powodu wysokiego użycia procesora CPU. Narzędzia diagnostyczne są obsługiwane dla .NET development w Visual Studio, w tym aplikacji ASP.NET i programowania w języku macierzystym/C++.

Centrum diagnostyki oferuje wiele innych opcji do zarządzania sesję diagnostyczną. Jeśli **użycie procesora CPU** narzędzia opisanego w tym miejscu nie zapewnia dane, które chcesz dodać, [innych narzędzi do profilowania](../profiling/profiling-feature-tour.md) zapewniają różne rodzaje informacji, które mogą być przydatne do Ciebie. W wielu przypadkach wąskie gardło aplikacji może być spowodowane przez inną niż Procesora, pamięci, renderowania interfejsu użytkownika lub czas żądania sieciowego. Centrum diagnostyki oferuje wiele innych opcji, aby rejestrować i analizować tego typu danych.

## <a name="create-a-project"></a>Tworzenie projektu

1. W programie Visual Studio, wybierz **Plik > Nowy projekt**.

2. W obszarze **Visual C++**, wybierz **Windows Desktop**, a następnie w środkowym okienku wybierz **aplikacji konsoli systemu Windows**.

3. Wpisz nazwę, takich jak **Diagnostics_Get_Started_Native** i kliknij przycisk **OK**.

    Program Visual Studio tworzy projekt.

4. W MyDbgApp.cpp Zastąp następujący kod

    ```c++
    int main()
    {
        return 0;
    }
    ```

    z tego kodu (nie usuwaj `#include "stdafx.h"`):

    ```c++
    #include <iostream>
    #include <limits>
    #include <mutex>
    #include <random>
    #include <functional>
    
    //.cpp file code:
    
    static constexpr int MIN_ITERATIONS = std::numeric_limits<int>::max() / 1000;
    static constexpr int MAX_ITERATIONS = MIN_ITERATIONS + 10000;
    
    long long m_totalIterations = 0;
    std::mutex m_totalItersLock;
    
    int getNumber()
    {
    
        std::uniform_int_distribution<int> num_distribution(MIN_ITERATIONS, MAX_ITERATIONS);
        std::mt19937 random_number_engine; // pseudorandom number generator
        auto get_num = std::bind(num_distribution, random_number_engine);
        int random_num = get_num();
    
        auto result = 0;
        {
            std::lock_guard<std::mutex> lock(m_totalItersLock);
            m_totalIterations += random_num;
        }
        // we're just spinning here  
        // to increase CPU usage 
        for (int i = 0; i < random_num; i++)
        {
            result = get_num();
        }
        return result;
    }
    
    void doWork()
    {
        std::wcout << L"The doWork function is running on another thread." << std::endl;
    
        auto x = getNumber();    
    }
    
    int main()
    {
        std::vector<std::thread> threads;
    
        for (int i = 0; i < 10; ++i) {
    
            threads.push_back(std::thread(doWork));
            std::cout << "The Main() thread calls this after starting the new thread" << std::endl;
        }
    
        for (auto& thread : threads) {
            thread.join();
        }
    
        return 0;
    }
    ```
  
##  <a name="BKMK_Quick_start__Collect_diagnostic_data"></a>Krok 1: Zbieranie danych profilowania 
  
1.  Najpierw należy ustawić punkt przerwania w aplikacji w tym wierszu kodu w `main` funkcji:

    `for (int i = 0; i < 10; ++i) {`

    Ustaw punkt przerwania, klikając w odstępu w lewo wiersz kodu.

2.  Następnie ustaw drugiego punktu przerwania na zamykający nawias klamrowy na końcu `main` funkcji:

     ![Ustaw punkty przerwania dla profilowania](../profiling/media/quickstart-cpu-usage-breakpoints-cplusplus.png "Ustaw punkty przerwania do profilowania")

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

## <a name="Step2"></a>Krok 2: Analizowanie danych użycia procesora CPU

Zalecamy rozpocząć analizowanie danych, sprawdzając listę funkcji zgodnie z użycia procesora CPU, identyfikowanie funkcji, które robią najbardziej pracy i następnie biorąc bliższe spojrzenie na każdym z nich.

1. Na liście funkcji badania funkcji, które robią większość pracy.

     ![Diagnostyka narzędzia użycie procesora CPU kartę](../profiling/media/quickstart-cpu-usage-cpu-cplusplus.png "DiagToolsCPUUsageTab")

    > [!TIP]
    > Funkcje są wymienione w kolejności, począwszy od tych czynności najbardziej pracy (nie są one w kolejności wywołania). Dzięki temu można szybko zidentyfikować najdłuższym funkcje uruchomione.

2. Na liście funkcji kliknij dwukrotnie `getNumber` funkcji.

    Po dwukrotnym kliknięciu funkcji **wywołujący/wywoływany** widok zostanie otwarty w okienku po lewej stronie. 

    ![Widok wywoływany obiekt wywołujący narzędzi diagnostycznych](../profiling/media/quickstart-cpu-usage-caller-callee-cplusplus.png "DiagToolsCallerCallee")

    W tym widoku wybranej funkcji zostaną wyświetlone w nagłówku, a w **bieżącej funkcji** pola (`getNumber`, w tym przykładzie). Funkcji, które wywołały bieżącą funkcję jest wyświetlany po lewej stronie w obszarze **podczas wywoływania funkcji**, a wszystkie funkcje wywoływane przez bieżącą funkcję są wyświetlane w **funkcji o nazwie** pole po prawej stronie. (Wybierz albo pola, aby zmienić bieżącą funkcję).

    Ten widok przedstawia łączny czas (ms) i odsetek ogólną aplikacji czasu podejmujący funkcja do wykonania działania.

    **Treść funkcji** również przedstawia łączną ilość czasu (i wartość procentowa czasu) w treści funkcji bez czasu poświęcony na wywołanie i wywołać funkcji. (Na tej ilustracji ms 119 z 43602 zostały spędzony w treści funkcji, a pozostałe czasu w innym kodzie wywoływanych przez tę funkcję). Bardzo różnią się w zależności od środowiska spowoduje rzeczywiste wartości.

    > [!TIP]
    > Wysokiej wartości w **treści funkcji** może wskazywać wąskie gardło w samej funkcji.

## <a name="next-steps"></a>Następne kroki

- [Analizowanie użycia pamięci](../profiling/memory-usage.md)do zidentyfikowania wąskich gardeł wydajności.
- [Analiza użycia procesora CPU](../profiling/cpu-usage.md) uzyskać więcej szczegółowych informacji na temat narzędzia użycie procesora CPU.
- Analiza użycia Procesora bez istnieje debuger dołączony lub wybierając uruchomionej aplikacji — Aby uzyskać więcej informacji, zobacz [zbierania danych profilowania bez debugowania](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) w [uruchomienie narzędzia z lub bez debuger profilowania](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="see-also"></a>Zobacz też  

 [Profilowanie w programie Visual Studio](../profiling/index.md)  
 [Przewodnik po funkcjach profilowania](../profiling/profiling-feature-tour.md)
