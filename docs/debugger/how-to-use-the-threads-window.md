---
title: Debugowanie aplikacji wielowątkowych
description: Debugowanie za pomocą okna wątki i narzędzi debugowania lokalizacji, w programie Visual Studio
ms.custom: ''
ms.date: 05/18/2017
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
ms.assetid: adfbe002-3d7b-42a9-b42a-5ac0903dfc25
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 65626bc483d7794c2adae141903783238a97eddd
ms.sourcegitcommit: 0cf1e63b6e0e6a0130668278489b21a6e5038084
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39468468"
---
# <a name="walkthrough-debug-a-multithreaded-application-in-visual-studio-using-the-threads-window"></a>Przewodnik: Debugowanie aplikacji wielowątkowych w programie Visual Studio za pomocą okna wątków
Program Visual Studio udostępnia **wątków** okna i inny użytkownik interfejsu elementy, aby pomóc w debugowaniu aplikacji wielowątkowych. W tym samouczku pokazano, jak używać **wątków** okna i **Lokalizacja debugowania** paska narzędzi. Aby uzyskać informacje na temat innych narzędzi, zobacz [Rozpoczynanie debugowania aplikacji wielowątkowych](../debugger/get-started-debugging-multithreaded-apps.md). Ten samouczek zawiera tylko kilka minut, ale jego ukończenia umożliwia zapoznanie się z funkcjami debugowania aplikacji wielowątkowych.   
  
Do wykonywania kroków opisanych w tym samouczku, potrzebny jest projektu aplikacji wielowątkowych. Wykonaj kroki wymienione w tym miejscu do utworzenia tego projektu.  
  
#### <a name="to-create-the-multithreaded-app-project"></a>Aby utworzyć projekt aplikacji wielowątkowych  
  
1.  Na **pliku** menu, wybierz **New** a następnie kliknij przycisk **projektu**.  
  
     **Nowy projekt** pojawi się okno dialogowe.  
  
2.  W **typu projektu**s kliknij wybranego przez siebie języka: **języka Visual Basic**, **Visual C#**, lub **Visual C++**.  
  
3.  W obszarze **pulpitu Windows**, wybierz **aplikacja Konsolowa**.  
  
4.  W **nazwa** wpisz nazwę MyThreadWalkthroughApp.  
  
5.  Kliknij przycisk **OK**.  
  
     Pojawi się nowy projekt konsoli. Po utworzeniu projektu, zostanie wyświetlony plik źródłowy. W zależności od języka wybranego pliku źródłowego może mieć nazwę Module1.vb, Program.cs lub MyThreadWalkthroughApp.cpp  
  
6.  Usuń kod, który pojawia się w pliku źródłowym i zastąp go przykładowy kod, który pojawia się w sekcji "Tworzenie wątek" tego tematu [Tworzenie wątków i przekazywanie danych na czas rozpoczęcia](/dotnet/standard/threading/creating-threads-and-passing-data-at-start-time).  
  
7.  Na **pliku** menu, kliknij przycisk **Zapisz wszystko**.  
  
#### <a name="to-begin-the-tutorial"></a>Aby rozpocząć samouczka  
  
-   W edytorze kodu źródłowego Wyszukaj następujący kod:  
  
    ```VB  
    Thread.Sleep(3000)   
    Console.WriteLine()
    ```  
  
    ```csharp  
    Thread.Sleep(3000);  
    Console.WriteLine();  
    ```  
  
    ```C++  
    Thread::Sleep(3000);  
    Console.WriteLine();  
    ```  
  
#### <a name="to-start-debugging"></a>Aby rozpocząć debugowanie  
  
1.  Kliknij na lewym marginesie z `Console.WriteLine` instrukcję, aby wstawić nowy punkt przerwania.  
  
     Na marginesie po lewej stronie Edytor kodu źródłowego pojawi się czerwone kółko. Oznacza to, że punkt przerwania są teraz ustawione w tej lokalizacji.  
  
2.  Na **debugowania** menu, kliknij przycisk **Rozpocznij debugowanie** (**F5**).  
  
     Rozpoczyna debugowania, uruchamiania aplikacji konsoli, aby uruchomić i następnie zatrzymuje w punkcie przerwania.  
  
3.  Jeśli okno konsoli w aplikacji ma fokus w tym momencie, kliknij w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] okna powrót do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
4.  W Edytor kodu źródłowego zlokalizuj wiersz, który zawiera następujący kod:  
  
    ```VB  
    Thread.Sleep(5000)   
    ```  
  
    ```csharp  
    Thread.Sleep(3000);  
    ```  
  
    ```C++  
    Thread::Sleep(3000);  
    ```
  
#### <a name="to-discover-the-thread-marker"></a>Aby odnaleźć znacznika wątku  

1.  Na pasku narzędzi debugowania kliknij **Pokaż wątki w źródle** przycisk ![Pokaż wątki w źródle](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker"). 
  
2.  Spójrz na oprawę w lewej części okna. W tym wierszu, zostanie wyświetlony *znacznika wątku* ikonę ![znacznika wątku](../debugger/media/dbg-thread-marker.png "ThreadMarker") o podobny dwoma wątkami ręczników. Znacznika wątku wskazuje, że wątek został zatrzymany w tej lokalizacji.  
  
3.  Umieść wskaźnik myszy nad znacznika wątku. Pojawi się DataTip. DataTip informuje numer identyfikacyjny nazwy i wątku dla każdego wątku zatrzymania. W tym przypadku istnieje tylko jeden wątek, którego nazwa jest prawdopodobnie `<noname>`.  

    > [!TIP]
    > Może okazać się przydatne do identyfikowania pustego wątków, zmieniając ich nazwę. W oknie wątków wybierz **Zmień nazwę** po kliknięciu prawym przyciskiem myszy na **nazwa** kolumny w wierszu wątku.
  
4.  Kliknij prawym przyciskiem myszy znacznika wątku, aby wyświetlić dostępne opcje w menu skrótów. 
    
  
## <a name="flagging-and-unflagging-threads"></a>Flagami i Unflagging wątków  
Można Oflaguj wątki, które chcesz poświęcić szczególną uwagę. Flagowanie wątków jest dobrym sposobem na śledzenie ważnych wątków i ignorowanie wątki, które nie są istotne informacje.  
  
#### <a name="to-flag-threads"></a>Do oflagowania wątków   

1.  Na **widoku** menu wskaż **pasków narzędzi**.  
  
    Upewnij się, że **Lokalizacja debugowania** pasek narzędzi jest zaznaczony.

2.  Przejdź do **Lokalizacja debugowania** paska narzędzi i kliknij przycisk **wątku** listy.  
  
    > [!NOTE]
    >  Można rozpoznać tego paska narzędzi przez trzy listy wyraźną: **procesu**, **wątku**, i **ramki stosu**.  
  
3.  Zwróć uwagę, jak wiele wątków, są wyświetlane na liście.  
  
4.  Wróć do Edytor kodu źródłowego i kliknij prawym przyciskiem myszy znacznika wątku ![znacznika wątku](../debugger/media/dbg-thread-marker.png "ThreadMarker") ponownie.  
  
5.  W menu skrótów wybierz polecenie **flagi**, a następnie kliknij nazwę wątku i numerem Identyfikacyjnym.  
  
6.  Wróć do **debugowania lokalizacji** narzędzi i Znajdź **Pokaż tylko oflagowane wątki** ikonę ![Pokaż oflagowane wątki](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker") do po prawej stronie **wątku** listy.  
  
    Ikony flag przycisk został wyszarzony przed. Teraz jest aktywny przycisk.  
  
7.  Kliknij przycisk **Pokaż tylko oflagowane wątki** ikony.  
  
    Na liście pojawi się teraz tylko wątków oflagowanych. (Możesz kliknąć przycisk pojedynczej flagi, aby powrócić do **Pokaż wszystkie wątki** tryb.)

8. Otwórz okno wątków, wybierając **Debuguj > Windows > wątków**.

    ![Okno wątków](../debugger/media/dbg-threads-window.png "ThreadsWindow")  
  
    W **wątków** oknie wątków oflagowanych zawiera ikonę wyraźną czerwona flaga podłączone do niego.

    > [!TIP]
    > Gdy flagą niektóre wątki mogą kliknij prawym przyciskiem myszy linię kodu w edytorze kodu i wybierz polecenie **Uruchom oflagowane wątki do kursora** (Upewnij się, że wybrany kod wszystkich wątków oflagowanych będzie korzystał z). To spowoduje wstrzymanie wątków na wybrany wiersz kodu, dzięki czemu łatwiej kontrolować kolejność wykonywania przez [zawiesza się i odblokowania wątków](#bkmk_freeze).
  
11. W edytorze kodu źródłowego kliknij prawym przyciskiem myszy znacznika wątku ponownie.  
  
     Zwróć uwagę, jakie opcje są teraz dostępne w menu skrótów. Zamiast **flagi**, pojawi się informacja **Unflag**. Nie klikaj **Unflag**.  

     Aby dowiedzieć się, jak i usuwanie oflagowania wątków, przejdź do następnej procedury.  
  
#### <a name="to-unflag-threads"></a>Aby usuwanie oflagowania wątków  
  
1.  W **wątków** okna, kliknij prawym przyciskiem myszy wiersz odpowiadający wątków oflagowanych.  
  
     Zostanie wyświetlone menu skrótów. Ma funkcje umożliwiające **Unflag** i **Usuń flagę ze wszystkich wątków**.  
  
2.  Aby Usuń flagę z wątku, kliknij przycisk **Unflag**.  

    Przyjrzyj się **debugowania lokalizacji** narzędzi ponownie. **Pokaż tylko oflagowane wątki** przycisk jest wygaszony, ponownie. Oflagowanie jest tylko wątków oflagowanych. Ponieważ nie istnieją wątki oflagowane, pasek narzędzi stała się wstecz do **Pokaż wszystkie wątki** trybu. Kliknij przycisk **wątku** listy i sprawdź, czy można wyświetlić wszystkie wątki.  
  
5.  Wróć do **wątków** okna i zbadaj kolumny informacji.  
  
    W pierwszej kolumnie zauważysz ikony flagi konturu w każdym wierszu listy wątków. (Konturu oznacza, że wątek jest bez flagi).  
  
6.  Kliknij flagę ikony konspektu dwoma wątkami drugie i trzecie w dolnej części listy. 

    Ikony flag stają się czerwony, zamiast pustego konturów.  
  
7.  Kliknij przycisk w górnej części kolumny flag.  
  
    Kolejność listy wątków zmieniany, gdy kliknięto przycisk. Lista wątków jest obecnie posortowana w oflagowane wątki na górze.  
  
8.  Ponownie kliknij przycisk w górnej części kolumny flag.  
  
    Jej ponownie zmienić porządek sortowania.  
  
## <a name="more-about-the-threads-window"></a>Więcej informacji na temat okna wątków  
  
#### <a name="to-learn-more-about-the-threads-window"></a>Aby dowiedzieć się więcej na temat okna wątków  
  
1.  W **wątków** oknie Sprawdź trzecia kolumna z lewej strony. Przycisk w górnej części w tej kolumnie jest wyświetlany komunikat **identyfikator**.  
  
2.  Kliknij przycisk **identyfikator**.  
  
     Lista wątków jest teraz posortowane według numer identyfikacyjny wątku.  
  
3.  Kliknij prawym przyciskiem myszy dowolnego wątku, na liście. W menu skrótów kliknij **wyświetlanie szesnastkowe**.  
  
     Format liczb identyfikator wątku jest zmieniany.  
  
4.  Umieść wskaźnik myszy nad **lokalizacji** kolumny dla każdego wątku, na liście.  
  
     Po chwili przechwytują pojawia się DataTip. Przedstawia on częściowe stosu dla wątku.

     > [!TIP]
     > Graficzne przedstawienie stosy wywołań dla wątków, można otworzyć [stosów równoległych](../debugger/using-the-parallel-stacks-window.md) okna (podczas debugowania, wybierz **debugowanie / Windows / stosów równoległych**).  
  
5.  Przyjrzyj się czwartej kolumnie z lewej strony, która jest oznaczona etykietą **kategorii**. Wątki są przydzielane do kategorii.  
  
     Pierwszym wątkiem utworzone w procesie jest nazywana wątku głównego. Znajdź je w listy wątków.  
  
6.  Kliknij prawym przyciskiem myszy w wątku głównym, a następnie kliknij przycisk **Przełącz do wątku**.  
  
     A **trybu przerwania** zostanie wyświetlone okno. Informuje, że debuger nie wykonuje obecnie wszelki kod, który umożliwia wyświetlanie (ponieważ jest ona wątku głównego).   
  
7.  Przyjrzyj się **stos wywołań** okna i **Lokalizacja debugowania** paska narzędzi.  
  
     Zawartość **stos wywołań** okna uległy zmianie. 

## <a name="bkmk_freeze"></a> Zawiesza się i odblokowania wykonywanie wątków 

Można blokowanie i odblokowywanie (Wstrzymanie i wznowienie) wątków, aby kontrolować kolejność, w którym wątków wykonywania pracy. Może to pomóc Ci rozwiązać problemy ze współbieżnością, takich jak zakleszczenia i wyścigu.

> [!TIP]
> Jeśli chcesz wykonać pojedynczego wątku, nie zawiesza się inne wątki (również typowe debugowania scenariusz), zobacz [Rozpoczynanie debugowania aplikacji wielowątkowych](../debugger/get-started-debugging-multithreaded-apps.md#bkmk_follow_a_thread).
  
#### <a name="to-freeze-and-unfreeze-threads"></a>Zablokuj i Odblokuj wątki  
  
1.  W **wątków** okna, kliknij prawym przyciskiem myszy dowolnego wątku, a następnie kliknij przycisk **Freeze**.  
  
2.  Przyjrzyj się druga kolumna (bieżąca kolumna wątku). Ikona Wstrzymaj pojawi się dostępne. Te ikona Wstrzymaj wskazuje, czy wątek jest zablokowane.  
  
3.  Pokaż **zawieszone liczba** kolumny, wybierając je w **kolumn** listy.

    Wstrzymania liczenia wątku, jest teraz 1.  
  
4.  Kliknij prawym przyciskiem myszy zablokowanego wątku, a następnie kliknij przycisk **Odblokuj**.  
  
     Bieżąca kolumna wątku i **zawieszone liczba** zmiany kolumny. 
  
## <a name="switching-the-to-another-thread"></a>Przełączanie do innego wątku 
  
#### <a name="to-switch-threads"></a>Aby przełączyć wątków  
  
1.  W **wątków** okna, sprawdź w drugiej kolumnie z lewej strony (bieżąca kolumna wątku). Przycisk u góry tej kolumny nie ma tekstu lub ikonę.
  
2.  Przyjrzyj się kolumnie bieżącego wątku i zwróć uwagę, że jeden wątek ma żółta strzałka. Żółta strzałka wskazuje, że ten wątek jest w bieżącym wątku (jest to bieżąca lokalizacja wskaźnik wykonania).
  
    Zanotuj numer identyfikacyjny wątku tam, gdzie zobaczysz ikonę bieżącego wątku. Bieżąca ikona wątek zostanie przeniesione do innego wątku, ale konieczne będzie umieszczenie go ponownie, po zakończeniu. 
  
3.  Kliknij prawym przyciskiem myszy innego wątku, a następnie kliknij przycisk **Przełącz do wątku**.  
  
4.  Przyjrzyj się **stos wywołań** okno Edytor kodu źródłowego. Zmieniono zawartość.  
  
5.  Przyjrzyj się **Lokalizacja debugowania** paska narzędzi. Bieżąca ikona wątek został zmieniony, zbyt.  
  
6.  Przejdź do **Lokalizacja debugowania** paska narzędzi. Wybierz inny wątek z **wątku** listy.  
  
7.  Przyjrzyj się **wątków** okna. Bieżąca ikona wątek został zmieniony.  
  
8. W edytorze kodu źródłowego kliknij prawym przyciskiem myszy znacznika wątku. W menu skrótów wybierz polecenie **Przełącz do wątku** i kliknij numer Identyfikatora/nazwy wątku.  
  
     Zauważyliśmy już teraz trzy sposoby zmiany Bieżąca ikona wątku do innego wątku: przy użyciu **wątków** oknie **wątku** listy w **Lokalizacja debugowania** narzędzi i Wątek znaczników w edytorze kodu źródłowego.  
  
     Za pomocą znacznika wątku można przełączyć tylko na wątki, które zostały zatrzymane w tej konkretnej lokalizacji. Za pomocą **wątków** okna i **Lokalizacja debugowania** narzędzi można przełączyć na żadnym z wątków.   
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji wielowątkowych](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Porady: przełączanie na inny wątek w trakcie debugowania](../debugger/how-to-switch-to-another-thread-while-debugging.md)
