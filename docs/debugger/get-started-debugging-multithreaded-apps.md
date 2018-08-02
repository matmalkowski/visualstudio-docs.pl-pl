---
title: Dowiedz się, jak debugowanie aplikacji wielowątkowych
description: Debugowanie za pomocą okna stosów równoległych i równoległego wyrażenia kontrolnego w programie Visual Studio
ms.custom: H1HackMay2017
ms.date: 08/01/2018
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
ms.openlocfilehash: 11cb05ea81f086cf8c26e3058850968a909b84e3
ms.sourcegitcommit: 0cf1e63b6e0e6a0130668278489b21a6e5038084
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39468686"
---
# <a name="get-started-debugging-multithreaded-applications-in-visual-studio"></a>Rozpoczynanie debugowania aplikacji wielowątkowych w programie Visual Studio
Program Visual Studio udostępnia wiele narzędzi i elementów interfejsu użytkownika w celu ułatwienia debugowania aplikacji wielowątkowych. W tym samouczku pokazano, jak i używaj znaczników wątków **stosów równoległych** oknie **równoległego wyrażenia kontrolnego** okien, warunkowe punkty przerwania i filtr punktów przerwania. Ten samouczek zawiera tylko kilka minut, ale jego ukończenia umożliwia zapoznanie się z funkcjami debugowania aplikacji wielowątkowych.

|         |         |
|---------|---------|
|  ![Ikona aparatu film wideo](../install/media/video-icon.png "Obejrzyj klip wideo")  |    [Obejrzyj film wideo](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugging-Multi-threaded-Apps-in-Visual-Studio-2017-MoZPKMD6D_111787171) na debugowanie wielowątkowe, który zawiera podobne kroki. |

Inne tematy zawierają dodatkowe informacje na temat korzystania z innymi narzędziami debugowania wielowątkowe:

- Podobne tematu, który pokazuje, jak używać **Lokalizacja debugowania** narzędzi i **wątków** okna, zobacz [wskazówki: debugowanie aplikacji wielowątkowych](../debugger/how-to-use-the-threads-window.md).

- Podobne tematu przy użyciu przykładu, który używa <xref:System.Threading.Tasks.Task> (kodu zarządzanego) i środowisko uruchomieniowe współbieżności (C++), zobacz [wskazówki: debugowanie aplikacji równoległych](../debugger/walkthrough-debugging-a-parallel-application.md). Ogólne debugowania porady, które mają zastosowanie do najbardziej wielowątkowe typów aplikacji można znaleźć w tym temacie i połączone tematu.
  
Do wykonywania kroków opisanych w tym samouczku, potrzebny jest projektu aplikacji wielowątkowych. Wykonaj kroki wymienione w tym miejscu do utworzenia tego projektu.  
  
#### <a name="to-create-the-multithreaded-app-project"></a>Aby utworzyć projekt aplikacji wielowątkowych  
  
1.  Na **pliku** menu, wybierz **New** a następnie kliknij przycisk **projektu**.  
  
     **Nowy projekt** pojawi się okno dialogowe.  
  
2.  Kliknij wybranego przez siebie języka: **Visual C#**, **Visual C++**, lub **języka Visual Basic**.  
  
3.  W obszarze **pulpitu Windows**, wybierz **aplikacja Konsolowa**.  
  
4.  W **nazwa** wpisz nazwę MyThreadWalkthroughApp.  
  
5.  Kliknij przycisk **OK**.  
  
     Pojawi się nowy projekt konsoli. Po utworzeniu projektu, zostanie wyświetlony plik źródłowy. W zależności od języka wybranego pliku źródłowego może można wywołać plik Program.cs, MyThreadWalkthroughApp.cpp lub Module1.vb.  
  
6.  Usuń kod, który pojawia się w pliku źródłowym i Zastąp kod przykładu przedstawiony w tym miejscu.

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

    using namespace;

    int count = 0;

    void doSomeWork() {

        cout << "The doSomeWork function is running on another thread." << endl;
        int data = count++;
        // Pause for a moment to provide a delay to make
        // threads more apparent.
        this_thread::sleep_for(chrono::seconds(3));
        cout << "The function called by the worker thread has ended." << endl;
    }

    int main() {
        vector<thread> threads;

        for (int i = 0; i < 10; ++i) {

            threads.push_back(thread(doSomeWork));
            cout << "The Main() thread calls this after starting the new thread" << endl;
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
  
-   W edytorze kodu źródłowego Wyszukaj następujący kod: 
  
    ```csharp  
    Thread.Sleep(3000);  
    Console.WriteLine();  
    ```  
  
    ```C++  
    this_thread::sleep_for(chrono::seconds(3));
    cout << "The function called by the worker thread has ended." << endl; 
    ```  

    ```VB
    Thread.Sleep(3000)
    Console.WriteLine()
    ```
  
#### <a name="to-start-debugging"></a>Aby rozpocząć debugowanie  
  
1.  Kliknij na lewym marginesie z `Thread.Sleep` lub `this_thread::sleep_for` instrukcję, aby wstawić nowy punkt przerwania.  
  
     Na marginesie po lewej stronie Edytor kodu źródłowego pojawi się czerwone kółko. Oznacza to, że punkt przerwania są teraz ustawione w tej lokalizacji. 
  
2.  Na **debugowania** menu, kliknij przycisk **Rozpocznij debugowanie** (**F5**).  
  
     Program Visual Studio tworzy rozwiązanie, aplikacja zaczyna być uruchamiana w debugerze i zatrzymywany aplikacji w punkcie przerwania.  
  
    > [!NOTE]
    > Jeśli możesz przełączać fokus w oknie konsoli, kliknij w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] okna powrót do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
4.  W Edytor kodu źródłowego zlokalizuj wiersz zawierający punkt przerwania:  
  
    ```csharp  
    Thread.Sleep(3000);  
    ```  
  
    ```C++  
    this_thread::sleep_for(chrono::seconds(3)); 
    ```

    ```VB
    Thread.Sleep(3000)
    ```    
  
#### <a name="ShowThreadsInSource"></a>Aby odnaleźć znacznika wątku  

1.  Na pasku narzędzi debugowania kliknij **Pokaż wątki w źródle** przycisk ![Pokaż wątki w źródle](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker").

2. Naciśnij klawisz **F11** raz, aby awansować debugera jednego wiersza kodu.
  
3.  Spójrz na oprawę w lewej części okna. W tym wierszu, zostanie wyświetlony *znacznika wątku* ikonę ![znacznika wątku](../debugger/media/dbg-thread-marker.png "ThreadMarker") o podobny dwoma wątkami ręczników. Znacznika wątku wskazuje, że wątek został zatrzymany w tej lokalizacji.

    Należy zauważyć, że znacznika wątku może częściowo zasłonięte przez punkt przerwania. 
  
4.  Umieść wskaźnik myszy nad znacznika wątku. Pojawi się DataTip. DataTip informuje numer identyfikacyjny nazwy i wątku dla każdego wątku zatrzymania. W takim przypadku nazwa jest prawdopodobnie `<noname>`. 
  
5.  Kliknij prawym przyciskiem myszy znacznika wątku, aby wyświetlić dostępne opcje w menu skrótów.
    
## <a name="ParallelStacks"></a>Sprawdź lokalizację wątków

W **stosów równoległych** okna, można przełączać się między widokiem wątków i (w przypadku programowania opartego na zadaniach) widoku zadania, na które mogą wyświetlać informacje stosu wywołań dla każdego wątku. W tej aplikacji możemy użyć widoku wątków.

1. Otwórz **stosów równoległych** okna, wybierając **Debuguj > Windows > stosów równoległych**. Powinien zostać wyświetlony, podobne do poniższego kodu (konkretne informacje będą różne w zależności od aktualnej lokalizacji każdego wątku, sprzętu i języka programowania).

    ![Okno stosów równoległych](../debugger/media/dbg-multithreaded-parallel-stacks.png "ParallelStacksWindow")

    W tym przykładzie od lewej do prawej uzyskujemy te informacje dla kodu zarządzanego:
    
    - Główny wątek (lewa strona) została zatrzymana na `Thread.Start` (punkt zatrzymania jest wskazywany przez ikonę znacznika wątku ![znacznika wątku](../debugger/media/dbg-thread-marker.png "ThreadMarker")).
    - Wprowadzono dwa wątki `ServerClass.InstanceMethod`, z których jedna jest bieżący wątek (żółta strzałka), podczas gdy inne wątku została zatrzymana w `Thread.Sleep`.
    - Nowy wątek (po prawej stronie) jest również uruchamiana (zatrzymana na `ThreadHelper.ThreadStart`).

2.  Kliknij prawym przyciskiem myszy wpisy w **stosów równoległych** okna, aby wyświetlić dostępne opcje w menu skrótów.

    Możesz wykonywać różne akcje te menu kliknij prawym przyciskiem myszy, ale w tym samouczku pokazano, jeden z tych szczegółów w **równoległego wyrażenia kontrolnego** okna (w kolejnych sekcjach).

    > [!NOTE]
    > Jeśli interesuje Cię bardziej wyświetlania listy, wyświetlania informacji dotyczących każdego wątku, należy użyć **wątków** okna zamiast tego. Zobacz [wskazówki: debugowanie aplikacji wielowątkowych](../debugger/how-to-use-the-threads-window.md).

## <a name="set-a-watch-on-a-variable"></a>Ustawianie wyrażenia kontrolnego na zmiennej

1. Otwórz **równoległego wyrażenia kontrolnego** okna, wybierając **Debuguj > Windows > równoległe wyrażenie kontrolne > równoległa Czujka 1**.

2. Kliknij komórkę tam, gdzie zobaczysz `<Add Watch>` tekstu (lub komórki nagłówka puste kolumny 4), typ `data`, i naciśnij klawisz Enter.

    Wartości dla zmiennej danych dla każdego wątku są wyświetlane w oknie.

3. Kliknij ponownie przycisk w komórce tam, gdzie zobaczysz `<Add Watch>` tekstu (lub komórki nagłówka puste kolumny 5), typ `count`, i naciśnij klawisz Enter.

    Wartości dla zmiennej liczby dla każdego wątku są wyświetlane w oknie. (Jeśli nie widzisz jeszcze tym dużo informacji, spróbuj nacisnąć klawisz F11 kilka razy więcej pomocnych wykonywanie wątków w debugerze.)

    ![Równoległe okno czujki](../debugger/media/dbg-multithreaded-parallel-watch.png "ParallelWatchWindow")

4. Kliknij prawym przyciskiem myszy jeden z wierszy w oknie, aby wyświetlić dostępne opcje.

## <a name="flagging-and-unflagging-threads"></a>Flagami i Unflagging wątków  
Można Oflaguj wątki, które chcesz poświęcić szczególną uwagę. Flagowanie wątków jest dobrym sposobem na śledzenie ważnych wątków i ignorowanie wątki, które nie są istotne informacje.  
  
#### <a name="to-flag-threads"></a>Do oflagowania wątków  

1. W **równoległego wyrażenia kontrolnego** okna, naciśnij i przytrzymaj klawisz SHIFT i wybierz opcję wiele wierszy.

2. Kliknij prawym przyciskiem myszy i wybierz polecenie **flagi**.

    Teraz wybrane wątki są oflagowane. Teraz możesz filtrować Pokaż tylko oflagowane wątki.
  
3.  W **równoległego wyrażenia kontrolnego** oknie Znajdź **Pokaż tylko oflagowane wątki** przycisk ![Pokaż oflagowane wątki](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker").  
  
4.  Kliknij przycisk **Pokaż tylko oflagowane wątki** przycisku.  
  
    Na liście pojawi się teraz tylko wątków oflagowanych.

    > [!TIP]
    > Gdy flagą niektóre wątki mogą kliknij prawym przyciskiem myszy linię kodu w edytorze kodu i wybierz polecenie **Uruchom oflagowane wątki do kursora** (Upewnij się, że wybrany kod wszystkich wątków oflagowanych będzie korzystał z). To spowoduje wstrzymanie wątków na wybrany wiersz kodu, dzięki czemu łatwiej jest kontrolować kolejność wykonywania przez [zawiesza się i odblokowania wątków](#bkmk_freeze).

5.  Kliknij przycisk **Pokaż tylko oflagowane wątki** przycisk, aby powrócić do **Pokaż wszystkie wątki** trybu.
    
#### <a name="to-unflag-threads"></a>Aby usuwanie oflagowania wątków

Aby usuwanie oflagowania wątków, kliknąć prawym przyciskiem myszy jeden lub więcej wątków oflagowanych w **równoległego wyrażenia kontrolnego** oknie i wybierz polecenie **Unflag**.

## <a name="bkmk_freeze"></a> Zawiesza się i odblokowania wykonywanie wątków 

> [!TIP]
> Można blokowanie i odblokowywanie (Wstrzymanie i wznowienie) wątków, aby kontrolować kolejność, w którym wątków wykonywania pracy. Może to pomóc Ci rozwiązać problemy ze współbieżnością, takich jak zakleszczenia i wyścigu.
  
#### <a name="to-freeze-and-unfreeze-threads"></a>Zablokuj i Odblokuj wątki  
  
1.  W **równoległego wyrażenia kontrolnego** okna z wszystkich wybranych wierszy, kliknij prawym przyciskiem myszy i wybierz pozycję **Freeze**.

    W drugiej kolumnie ikona Wstrzymaj pojawi się dla każdego wiersza. Ikona Wstrzymaj wskazuje, że wątek jest zablokowane.

2.  Usuń zaznaczenie wiersze, klikając przycisk tylko jeden wiersz.

3.  Kliknij prawym przyciskiem myszy wiersz, a następnie wybierz pozycję **Odblokuj**.

    Ikona Wstrzymaj stanie się niepotrzebna ten wiersz, wskazujący, że wątek nie jest już jest zamrożona.

4.  Przejdź do edytora kodu, a następnie kliknij przycisk **F11**. Uruchamia odblokowanej wątku.

    Aplikacja może również tworzy kilka nowych wątków. Należy zauważyć, że wszystkie nowe wątki są bez flagi, a nie są zablokowane.

## <a name="bkmk_follow_a_thread"></a> Postępuj zgodnie z jednego wątku za pomocą warunkowe punkty przerwania

Czasami może być przydatne z wykonywania jest jeden wątek w debugerze. Jednym ze sposobów, możesz to zrobić, jest zawiesza się wątki, które nie są zainteresowani, ale w niektórych scenariuszach możesz chcieć wykonać pojedynczego wątku, nie zawiesza się inne wątki (Odtwórz określonego usterek, na przykład). Aby wykonać wątek bez zawiesza się inne wątki, można uniknąć wejście do kodu, z wyjątkiem w wątku, który Cię interesuje. Można to zrobić, ustawiając [warunkowego punktu przerwania](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).

Możesz ustawić punkty przerwania dla różnych warunków, takich jak nazwa wątku lub identyfikator wątku. Innej metody, które mogą być pomocne jest ustawienie dla warunku na danych, który będzie unikatowy dla każdego wątku. Jest to typowy scenariusz debugowania, w którym interesuje Cię bardziej niż w żadnym z wątków niektóre wartości określone dane.

#### <a name="to-follow-a-single-thread"></a>Z jednego wątku

1. Kliknij prawym przyciskiem myszy punkt przerwania został wcześniej utworzony, a następnie wybierz **warunki**.

2. W **ustawienia punktu przerwania** okna, typ `data == 5` dla wyrażenia warunkowego.

    ![Warunkowego punktu przerwania](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

    > [!TIP]
    > Jeśli interesuje Cię bardziej w określonym wątku, należy następnie rozważyć Nazwa wątku lub identyfikator wątku dla warunku. Aby to zrobić w **ustawienia punktu przerwania** wybierz **filtru** zamiast **wyrażenia warunkowego**i postępuj zgodnie z poradami filtru. Można nazwać wątki w kodzie aplikacji (ponieważ wątki identyfikatory zmiany po ponownym uruchomieniu debugera).

3. Zamknij **ustawienia punktu przerwania** okna.

4. Kliknij przycisk Uruchom ponownie ![ponowne uruchomienie aplikacji](../debugger/media/dbg-tour-restart.png "RestartApp") przycisk, aby ponownie uruchomić sesję debugowania.

    Spowoduje przerwanie połączenia do kodu w wątku, dla której zmienna danych wynosi 5. Wyszukaj żółta strzałka (bieżący kontekst debugera) **równoległego wyrażenia kontrolnego** okna, aby sprawdzić, czy.

5. Można teraz Przekrocz (F10) kod i wkroczyć do kodu (F11) i postępuj zgodnie z jednym wątkiem wykonywania.

    Tak długo, jak warunek punktu przerwania jest unikatowy dla wątku i debuger nie trafień inne punkty przerwania w innych wątkach (może być konieczne ich wyłączyć), możesz Przekrocz nad kodem i wejdź do kodu bez przełączania dla innych wątków.

    > [!NOTE]
    > Po dojściu jest debugera, zostaną uruchomione wszystkie wątki. Jednak debuger nie będzie Wejdź do kodu w innych wątkach, chyba że jeden z innych wątków trafienia punktu przerwania. 
  
## <a name="more-about-the-multithreaded-debugging-windows"></a>Więcej informacji na temat wielowątkowe debugowanie systemu windows 

#### <a name="to-switch-to-another-thread"></a>Aby przełączyć się do innego wątku 

- Aby przełączyć się do innego wątku, zobacz [porady: przełączanie do innego wątku podczas debugowania](../debugger/how-to-switch-to-another-thread-while-debugging.md) 

#### <a name="to-learn-more-about-the-parallel-stack-and-parallel-watch-windows"></a>Aby dowiedzieć się więcej na temat okna stosów równoległych i równoległego wyrażenia kontrolnego  
  
- Zobacz [porady: Korzystanie z okna równoległego stosu](../debugger/using-the-parallel-stacks-window.md) 

- Zobacz [porady: Korzystanie z okna równoległego wyrażenia kontrolnego](../debugger/how-to-use-the-parallel-watch-window.md) 
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji wielowątkowych](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Porady: przełączanie na inny wątek w trakcie debugowania](../debugger/how-to-switch-to-another-thread-while-debugging.md)
