---
title: Dowiedz się debugować aplikacje wielowątkowe
description: Debugowanie za pomocą stosów równoległych i czujki równoległej systemu windows w programie Visual Studio
ms.custom: H1HackMay2017
ms.date: 06/02/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
ms.assetid: 62df746b-b0f6-4df4-83cf-b1d9d2e72833
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bb178a0a048a3696fc2c1ec642127906c8b83424
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="get-started-debugging-multithreaded-applications-in-visual-studio"></a>Rozpocząć debugowanie wielowątkowe aplikacje w programie Visual Studio
Program Visual Studio udostępnia wiele narzędzi i elementy interfejsu użytkownika, aby pomóc w debugowaniu aplikacji wielowątkowych. Ten samouczek przedstawia sposób użycia znaczników wątku **stosów równoległych** okna, **czujki równoległej** okna, warunkowych punktów przerwania, a punkty przerwania filtru. W tym samouczku zajmuje tylko kilka minut, ale jego wypełnieniu umożliwia zapoznanie się z funkcjami do debugowania aplikacji wielowątkowych.

|         |         |
|---------|---------|
|  ![Ikona aparatu film wideo](../install/media/video-icon.png "obejrzeć film wideo")  |    [Obejrzyj film](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugging-Multi-threaded-Apps-in-Visual-Studio-2017-MoZPKMD6D_111787171) na debugowanie wielowątkowe, który zawiera podobne kroki. |

Inne tematy zawierają dodatkowe informacje o przy użyciu innych narzędzi debugowania wielowątkowe:

- Dla podobnych temat, który przedstawia sposób użycia **debugowania lokalizacji** narzędzi i **wątków** okna, zobacz [wskazówki: debugowanie aplikacji wielowątkowych](../debugger/how-to-use-the-threads-window.md).

- Podobne tematu z przykładu korzystającego z <xref:System.Threading.Tasks.Task> (kod zarządzany) i współbieżność środowiska wykonawczego (C++), zobacz [wskazówki: debugowanie aplikacji równoległych](../debugger/walkthrough-debugging-a-parallel-application.md). Ogólne porady debugowania, które dotyczą najbardziej wielowątkowe typy aplikacji można znaleźć w zarówno w tym temacie oraz temat połączone.
  
Aby rozpocząć tego samouczka, należy projekt aplikacji wielowątkowych. Wykonaj wszystkie czynności opisane tutaj, aby utworzyć tego projektu.  
  
#### <a name="to-create-the-multithreaded-app-project"></a>Aby utworzyć projekt aplikacji wielowątkowych  
  
1.  Na **pliku** menu, wybierz **nowy** , a następnie kliknij przycisk **projektu**.  
  
     **Nowy projekt** zostanie wyświetlone okno dialogowe.  
  
2.  W **typu projektu**s kliknij preferowanego języka: **Visual C#**, **Visual C++**, lub **Visual Basic**.  
  
3.  W **szablony** wybierz **aplikacji konsoli**.  
  
4.  W **nazwa** wpisz nazwę MyThreadWalkthroughApp.  
  
5.  Kliknij przycisk **OK**.  
  
     Zostanie wyświetlony nowy projekt console. Po utworzeniu projektu, zostanie wyświetlony plik źródłowy. W zależności od wybranego języka może można wywołać plik źródłowy, plik Program.cs, MyThreadWalkthroughApp.cpp lub Module1.vb.  
  
6.  Usuń kod, który pojawia się w pliku źródłowym i zastąp go przykładowy kod pokazano poniżej.

    ```csharp
    using System;
    using System.Threading;

    public class ServerClass
    {

        static int count = 0;
        // The method that will be called when the thread is started.
        public void InstanceMethod()
        {
            Console.WriteLine(
                "ServerClass.InstanceMethod is running on another thread.");

            int data = count++;
            // Pause for a moment to provide a delay to make
            // threads more apparent.
            Thread.Sleep(3000);
            Console.WriteLine(
                "The instance method called by the worker thread has ended.");
        }
    }

    public class Simple
    {
        public static void Main()
        {
            for (int i = 0; i < 10; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.InstanceMethod));
            // Start the thread.
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }
    }
    ```

    ```C++
    #include "stdafx.h"
    #include <thread>
    #include <iostream>
    #include <vector>

    int count = 0;

    void doSomeWork() {

        std::cout << "The doSomeWork function is running on another thread." << std::endl;
        int data = count++;
        // Pause for a moment to provide a delay to make
        // threads more apparent.
        std::this_thread::sleep_for(std::chrono::seconds(3));
        std::cout << "The function called by the worker thread has ended." << std::endl;
    }

    int main() {
        std::vector<std::thread> threads;

        for (int i = 0; i < 10; ++i) {

            threads.push_back(std::thread(doSomeWork));
            std::cout << "The Main() thread calls this after starting the new thread" << std::endl;
        }

        for (auto& thread : threads) {
            thread.join();
        }

        return 0;
    }
    ```

    ```VB
    Imports System.Threading

    Public Class ServerClass
        ' The method that will be called when the thread is started.
        Public count = 0
        Public Sub InstanceMethod()
            Console.WriteLine(
                    "ServerClass.InstanceMethod is running on another thread.")

            Dim data = count + 1
            ' Pause for a moment to provide a delay to make
            ' threads more apparent.
            Thread.Sleep(3000)
            Console.WriteLine(
                    "The instance method called by the worker thread has ended.")
        End Sub

    End Class

    Public Class Simple

        Public Shared Sub Main()

            Dim ts As New ThreadStarter
            For index = 1 To 10
                ts.CreateThreads()
            Next

        End Sub

    End Class
    Public Class ThreadStarter
        Public Sub CreateThreads()
            Dim serverObject As New ServerClass()

            ' Create the thread object, passing in the
            ' serverObject.InstanceMethod method using a
            ' ThreadStart delegate.
            Dim InstanceCaller As New Thread(AddressOf serverObject.InstanceMethod)

            ' Start the thread.
            InstanceCaller.Start()

            Console.WriteLine("The Main() thread calls this after " _
                        + "starting the new InstanceCaller thread.")

        End Sub
    End Class
    ```
  
7.  Na **pliku** menu, kliknij przycisk **Zapisz wszystko**.  
  
#### <a name="to-begin-the-tutorial"></a>Aby rozpocząć samouczka  
  
-   Wyszukaj następujący kod w edytorze kodu źródłowego: 
  
    ```csharp  
    Thread.Sleep(3000);  
    Console.WriteLine();  
    ```  
  
    ```C++  
    Thread::Sleep(3000);  
    Console.WriteLine();  
    ```  
    ```VB
    Thread.Sleep(3000)
    Console.WriteLine()
    ```
  
#### <a name="to-start-debugging"></a>Aby rozpocząć debugowanie  
  
1.  Kliknij w lewym odstępu dla `Thread.Sleep` lub `Thread::Sleep` instrukcji, aby wstawić nowego punktu przerwania.  
  
     W odstępu po lewej stronie Edytor kodu źródłowego pojawi się czerwone kółko. Oznacza to, że punkt przerwania jest teraz ustawić w tej lokalizacji. 
  
2.  Na **debugowania** menu, kliknij przycisk **Rozpocznij debugowanie** (**F5**).  
  
     Visual Studio kompiluje rozwiązanie, uruchomieniu aplikacji do uruchamiania w debugerze, a następnie aplikacja zatrzymuje się na punkt przerwania.  
  
    > [!NOTE]
    > Po przełączeniu fokus w oknie konsoli kliknij [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] okno, aby wrócić fokus [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
4.  W edytorze kodu źródłowego odszukaj wiersz zawierający punkt przerwania:  
  
    ```csharp  
    Thread.Sleep(3000);  
    ```  
  
    ```C++  
    Thread::Sleep(3000);  
    ```

    ```VB
    Thread.Sleep(3000)
    ```    
  
#### <a name="ShowThreadsInSource"></a>Aby odnaleźć znacznika wątku  

1.  Na pasku narzędzi debugowania, kliknij przycisk **Pokaż wątki w źródle** przycisk ![Pokaż wątki w źródle](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker").

2. Naciśnij klawisz **F11** raz, aby poprawić debugera jeden wiersz kodu.
  
3.  Spójrz na odstępu w lewej części okna. W tym wierszu, zostanie wyświetlony *znacznika wątku* ikona ![znacznika wątku](../debugger/media/dbg-thread-marker.png "ThreadMarker") o podobny dwoma wątkami materiału. Znacznika wątku wskazuje, że wątek został zatrzymany w tej lokalizacji.

    Zwróć uwagę, że znacznika wątku może być częściowo ukrywane przez punkt przerwania. 
  
4.  Umieść kursor nad znacznika wątku. Zostanie wyświetlone etykietek danych. Etykietek danych zawiera numer identyfikacyjny nazwy i wątków dla każdego zatrzymanego wątku. W takim przypadku nazwa jest prawdopodobnie `<noname>`. 
  
5.  Kliknij prawym przyciskiem myszy znacznika wątku, aby wyświetlić opcje dostępne w menu skrótów.
    
## <a name="ParallelStacks"></a>Sprawdź lokalizację wątków

W **stosów równoległych** okna, można przełączać się między widokiem wątków i (na potrzeby programowania opartego na zadaniach) widoku zadania, a można przeglądać informacje stosu wywołań dla każdego wątku. W tej aplikacji możemy użyć widoku wątków.

1. Otwórz **stosów równoległych** okna, wybierając **Debuguj > Windows > stosów równoległych**. Powinny pojawić się podobny do poniższego (dokładne informacje będą różne w zależności od bieżącej lokalizacji każdy wątek, sprzętu i języka programowania).

    ![Równoległych stosów okna](../debugger/media/dbg-multithreaded-parallel-stacks.png "ParallelStacksWindow")

    W tym przykładzie od lewej do prawej uzyskujemy te informacje:
    
    - Wątek Main (po lewej stronie) została zatrzymana na `Thread.Start` (punkt zatrzymania jest oznaczony ikoną znacznika wątku ![znacznika wątku](../debugger/media/dbg-thread-marker.png "ThreadMarker")).
    - Dwa wątki zostały wprowadzone `ServerClass.InstanceMethod`, z których jeden jest bieżący wątek (żółta strzałka), podczas gdy inne wątku zostało zatrzymane w `Thread.Sleep`.
    - Nowego wątku (po prawej) jest również uruchamiana (zatrzymana na `ThreadHelper.ThreadStart`).

2.  Kliknij prawym przyciskiem myszy wpisy w **stosów równoległych** okno, aby wyświetlić dostępne opcje menu skrótów.

    Wykonaj różne akcje z tych menu kliknij prawym przyciskiem myszy, ale w tym samouczku pokazano, jeden z tych szczegółów w **czujki równoległej** okna (w następnej sekcji).

    > [!NOTE]
    > Jeśli interesuje Cię więcej wyświetlenie listy, wyświetlania informacji dotyczących każdego wątku, użyj **wątków** okna zamiast tego. Zobacz [wskazówki: debugowanie aplikacji wielowątkowych](../debugger/how-to-use-the-threads-window.md).

## <a name="set-a-watch-on-a-variable"></a>Ustaw czujki w zmiennej

1. Otwórz **czujki równoległej** okna, wybierając **Debuguj > Windows > czujki równoległej > 1 czujki równoległej**.

2. Kliknij komórkę, w której występuje `<Add Watch>` tekst (lub komórki pusty nagłówek kolumny 4), typ `data`, i naciśnij klawisz Enter.

    Wartości dla zmiennej danych dla każdego wątku są wyświetlane w oknie.

3. Kliknij ponownie przycisk w komórce, w której występuje `<Add Watch>` tekst (lub komórki pusty nagłówek kolumny 5.), typ `count`, i naciśnij klawisz Enter.

    Wartości dla zmiennej licznika dla każdego wątku są wyświetlane w oknie. (Jeśli nie widzisz jeszcze tyle informacji, spróbuj nacisnąć klawisz F11 kilka razy więcej można poprawić wykonywanie wątków w debugerze.)

    ![Okno czujki równoległych](../debugger/media/dbg-multithreaded-parallel-watch.png "ParallelWatchWindow")

4. Kliknij prawym przyciskiem myszy jednego z wierszy w oknie, aby wyświetlić dostępne opcje.

## <a name="flagging-and-unflagging-threads"></a>Flagami i Unflagging wątków  
Można Flaga wątków, które chcesz nadać szczególną uwagę. Flagowanie wątków jest dobrym sposobem do śledzenia ważnych wątków i Ignoruj wątków, które nie zależy Ci.  
  
#### <a name="to-flag-threads"></a>Aby oflagowania wątków  

1. W **czujki równoległej** okna, naciśnij i przytrzymaj klawisz SHIFT i zaznaczyć wiele wierszy.

2. Kliknij prawym przyciskiem myszy i wybierz polecenie **flagi**.

    Teraz są oznaczane wybrane wątki. Teraz możesz filtrować Pokaż tylko oflagowane wątki.
  
3.  W **czujki równoległej** oknie Znajdź **Pokaż tylko oflagowane wątki** przycisk ![Pokaż oflagowane wątki](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker").  
  
4.  Kliknij przycisk **Pokaż tylko oflagowane wątki** przycisku.  
  
    Na liście pojawi się teraz tylko oflagowane wątku.

    > [!TIP]
    > Gdy flagą niektórych wątków, musisz kliknij prawym przyciskiem myszy linię kodu w edytorze kodu i wybrać **Uruchom oflagowane wątki do kursora** (Upewnij się, wybierz kod, że wszystkie oflagowane wątki osiągną). Spowoduje to wstrzymać wątków w wybranym wierszu kodu, co ułatwia kontrolowanie kolejność wykonywania przez [zamrażanie i odblokowania wątków](#bkmk_freeze).

5.  Kliknij przycisk **Pokaż tylko oflagowane wątki** przycisk, aby powrócić do **Pokaż wszystkie wątki** tryb.
    
#### <a name="to-unflag-threads"></a>Aby usuwanie oflagowania wątków

Aby usuwanie oflagowania wątków, kliknąć prawym przyciskiem myszy jeden lub więcej wątków oflagowanych w **czujki równoległej** okna i wybierz polecenie **Unflag**.

## <a name="bkmk_freeze"></a> Zamrażanie i odblokowania wykonywanie wątków 

> [!TIP]
> Możesz zablokować i odblokować (wstrzymywania i wznawiania) wątków, aby określić kolejność, w którym wątków wykonywania pracy. To może pomóc rozwiązać problemy ze współbieżnością, takich jak zakleszczenie i zastępować warunków.
  
#### <a name="to-freeze-and-unfreeze-threads"></a>Aby blokowanie i odblokowywanie wątków  
  
1.  W **czujki równoległej** okno z wszystkich wybranych wierszy, kliknij prawym przyciskiem myszy i wybierz **Zablokuj**.

    W drugiej kolumnie ikoną wstrzymania jest teraz wyświetlany dla każdego wiersza. Ikona Wstrzymaj wskazuje, że wątek jest zablokowana.

2.  Anuluj wybór wiersze, klikając tylko jeden wiersz.

3.  Kliknij prawym przyciskiem myszy wiersza i wybierz **odblokowania**.

    Wstrzymaj ikona zniknie na ten wiersz i wskazujący, że wątek jest już zablokowana.

4.  Przełącz się do edytora kodu i kliknij przycisk **F11**. Uruchamia odblokowanej wątku.

    Aplikacja może także utworzyć wystąpienia niektóre nowe wątki. Zwróć uwagę, że wszystkie nowe wątki są bez flagi i nie są zablokowane.

## <a name="bkmk_follow_a_thread"></a> Wykonaj jeden wątek za pomocą warunkowe punkty przerwania

Czasami może być przydatne do wykonania wykonywania jest jeden wątek w debugerze. Jedną z metod można to zrobić zamrażanie wątków, które nie są zainteresowane, ale w niektórych przypadkach warto wykonaj pojedynczego wątku bez zamrażanie innych wątków (do określonego usterek, na przykład reprodukcja). Do wykonania wątku bez zamrażanie inne wątki, można uniknąć dzielenia na kod z wyjątkiem w wątku, który chcesz. Można to zrobić przez ustawienie [warunkowych punktów przerwania](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).

Można ustawić punktów przerwania w różnych warunkach, takie jak nazwa wątku lub identyfikator wątku. Innej metody, które mogą być pomocne jest warunek danych, który będzie unikatowy dla każdego wątku. To jest typowym scenariuszem debugowania, w którym myślisz więcej niż w jednym z wątków niektóre wartości danych.

#### <a name="to-follow-a-single-thread"></a>Do wykonania wątku pojedynczego

1. Kliknij prawym przyciskiem myszy punkt przerwania została wcześniej utworzona, a następnie wybierz pozycję **warunki**.

2. W **ustawienia punktów przerwania** wpisz `data == 5` dla wyrażenia warunkowego.

    ![Punkt przerwania warunkowego](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

    > [!TIP]
    > Jeśli interesuje Cię więcej w konkretnym wątkiem, użyj Nazwa wątku lub identyfikator wątku dla warunku. Aby to zrobić w **ustawienia punktów przerwania** wybierz **filtru** zamiast **wyrażenia warunkowego**i postępuj zgodnie z poradami filtru. Warto nazwa Twojej wątków w kodzie aplikacji (ponieważ wątków identyfikatorów zmiany po ponownym uruchomieniu debugera).

3. Zamknij **ustawienia punktów przerwania** okna.

4. Kliknij przycisk Uruchom ponownie ![ponowne uruchomienie aplikacji](../debugger/media/dbg-tour-restart.png "RestartApp") przycisk, aby ponownie uruchomić sesję debugowania.

    Spowoduje przerwanie do kodu w wątku, dla której zmienna danych wynosi 5. Wyszukaj żółta strzałka (bieżącego kontekstu debugera) **czujki równoległej** okno, aby sprawdzić, czy.

5. Można teraz, Przekrocz nad kodu (F10) i wykonywanie kodu (F11) i wykonaj wykonywanie jednego wątku.

    Tak długo, jak warunku punktu przerwania jest unikatowy dla wątku i debuger nie osiągnęła innych punktów przerwania w innych wątków (może być konieczne je wyłączyć), możesz Przekrocz nad kodu i wykonywanie kodu bez przełączania do innych wątków.

    > [!NOTE]
    > Po przejściu debuger będzie uruchamiane są wszystkie wątki. Jednak debuger nie Dziel na kod na inne wątki, chyba, że jeden z innych wątków trafienia punktu przerwania. 
  
## <a name="more-about-the-multithreaded-debugging-windows"></a>Więcej informacji na temat wielowątkowe debugowania systemu windows 

#### <a name="to-switch-to-another-thread"></a>Aby przełączyć się do innego wątku 

- Aby przełączyć się do innego wątku, zobacz [porady: przełączanie do innego wątku podczas debugowania](../debugger/how-to-switch-to-another-thread-while-debugging.md) 

#### <a name="to-learn-more-about-the-parallel-stack-and-parallel-watch-windows"></a>Aby dowiedzieć się więcej na temat okna stosów równoległych i czujki równoległej  
  
- Zobacz [porady: Korzystanie z okna stosu równoległych](../debugger/using-the-parallel-stacks-window.md) 

- Zobacz [porady: Korzystanie z okna czujki równoległej](../debugger/how-to-use-the-parallel-watch-window.md) 
  
## <a name="see-also"></a>Zobacz też  
 [Debuguj aplikacje wielowątkowe](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Porady: przełączanie na inny wątek podczas debugowania](../debugger/how-to-switch-to-another-thread-while-debugging.md)
