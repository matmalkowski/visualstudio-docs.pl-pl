---
title: Debugowanie aplikacji wielowątkowych
description: Debugowanie za pomocą okna wątki i narzędzi lokalizacji debugowania w programie Visual Studio
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
ms.openlocfilehash: 37a9161011031c53ed16a9ab0918eb498f5fa270
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31926244"
---
# <a name="walkthrough-debug-a-multithreaded-application-in-visual-studio-using-the-threads-window"></a>Wskazówki: Debugowanie aplikacji wielowątkowych w programie Visual Studio za pomocą okna wątki
Program Visual Studio udostępnia **wątków** okna i innych użytkowników interface elementy, aby pomóc w debugowaniu aplikacji wielowątkowych. Ten samouczek przedstawia sposób użycia **wątków** okna i **debugowania lokalizacji** paska narzędzi. Aby uzyskać informacje na temat innych narzędzi, zobacz [rozpocząć debugowanie aplikacji wielowątkowych](../debugger/get-started-debugging-multithreaded-apps.md). W tym samouczku zajmuje tylko kilka minut, ale jego wypełnieniu umożliwia zapoznanie się z funkcjami do debugowania aplikacji wielowątkowych.   
  
Aby rozpocząć tego samouczka, należy projekt aplikacji wielowątkowych. Wykonaj wszystkie czynności opisane tutaj, aby utworzyć tego projektu.  
  
#### <a name="to-create-the-multithreaded-app-project"></a>Aby utworzyć projekt aplikacji wielowątkowych  
  
1.  Na **pliku** menu, wybierz **nowy** , a następnie kliknij przycisk **projektu**.  
  
     **Nowy projekt** zostanie wyświetlone okno dialogowe.  
  
2.  W **typu projektu**s kliknij preferowanego języka: **Visual Basic**, **Visual C#**, lub **Visual C++**.  
  
3.  W **szablony** wybierz **aplikacji konsoli**.  
  
4.  W **nazwa** wpisz nazwę MyThreadWalkthroughApp.  
  
5.  Kliknij przycisk **OK**.  
  
     Zostanie wyświetlony nowy projekt console. Po utworzeniu projektu, zostanie wyświetlony plik źródłowy. W zależności od wybranego języka plik źródłowy może mieć nazwę Module1.vb, Program.cs lub MyThreadWalkthroughApp.cpp  
  
6.  Usuń kod, który pojawia się w pliku źródłowym i zastąp go przykładowy kod, który pojawia się w sekcji "Tworzenie wątku" tematu [Tworzenie wątków i przekazywanie danych w chwili uruchomienia](/dotnet/standard/threading/creating-threads-and-passing-data-at-start-time).  
  
7.  Na **pliku** menu, kliknij przycisk **Zapisz wszystko**.  
  
#### <a name="to-begin-the-tutorial"></a>Aby rozpocząć samouczka  
  
-   Wyszukaj następujący kod w edytorze kodu źródłowego:  
  
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
  
1.  Kliknij w lewym odstępu dla `Console.WriteLine` instrukcji, aby wstawić nowego punktu przerwania.  
  
     W odstępu po lewej stronie Edytor kodu źródłowego pojawi się czerwone kółko. Oznacza to, że punkt przerwania jest teraz ustawić w tej lokalizacji.  
  
2.  Na **debugowania** menu, kliknij przycisk **Rozpocznij debugowanie** (**F5**).  
  
     Rozpoczyna debugowania, Twojej uruchomieniu aplikacji konsoli, aby uruchomić, a następnie zatrzymuje w punkt przerwania.  
  
3.  Jeśli w oknie aplikacji konsoli ma fokus w tym momencie, kliknij [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] okno, aby wrócić fokus [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
4.  W edytorze kodu źródłowego odszukaj wiersz zawierający następujący kod:  
  
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

1.  Na pasku narzędzi debugowania, kliknij przycisk **Pokaż wątki w źródle** przycisk ![Pokaż wątki w źródle](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker"). 
  
2.  Spójrz na odstępu w lewej części okna. W tym wierszu, zostanie wyświetlony *znacznika wątku* ikona ![znacznika wątku](../debugger/media/dbg-thread-marker.png "ThreadMarker") o podobny dwoma wątkami materiału. Znacznika wątku wskazuje, że wątek został zatrzymany w tej lokalizacji.  
  
3.  Umieść kursor nad znacznika wątku. Zostanie wyświetlone etykietek danych. Etykietek danych zawiera numer identyfikacyjny nazwy i wątków dla każdego zatrzymanego wątku. W takim przypadku jest tylko jeden wątek, którego nazwa jest prawdopodobnie `<noname>`.  

    > [!TIP]
    > Może być przydatne do identyfikowania pustego wątków im nazwy. W oknie wątków wybierz **Zmień nazwę** po kliknięciu prawym przyciskiem myszy na **nazwa** kolumny w wierszu wątku.
  
4.  Kliknij prawym przyciskiem myszy znacznika wątku, aby wyświetlić opcje dostępne w menu skrótów. 
    
  
## <a name="flagging-and-unflagging-threads"></a>Flagami i Unflagging wątków  
Można Flaga wątków, które chcesz nadać szczególną uwagę. Flagowanie wątków jest dobrym sposobem do śledzenia ważnych wątków i Ignoruj wątków, które nie zależy Ci.  
  
#### <a name="to-flag-threads"></a>Aby oflagowania wątków   

1.  Na **widoku** menu wskaż **paski narzędzi**.  
  
    Upewnij się, że **debugowania lokalizacji** pasek narzędzi jest zaznaczony.

2.  Przejdź do **debugowania lokalizacji** narzędzi i kliknij przycisk **wątku** listy.  
  
    > [!NOTE]
    >  Ten pasek narzędzi może rozpoznać przez trzy listy poświęcone: **procesu**, **wątku**, i **ramki stosu**.  
  
3.  Zwróć uwagę, jak wiele wątków znajdują się na liście.  
  
4.  Przejdź do edytora kodu źródłowego i kliknij prawym przyciskiem myszy znacznika wątku ![znacznika wątku](../debugger/media/dbg-thread-marker.png "ThreadMarker") ponownie.  
  
5.  W menu skrótów polecenie **flagi**, a następnie kliknij nazwę wątku i identyfikator.  
  
6.  Wróć do **debugowania lokalizacji** narzędzi i Znajdź **Pokaż tylko oflagowane wątki** ikona ![Pokaż oflagowane wątki](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker") do prawo do **wątku** listy.  
  
    Ikona flagi na przycisku został nieaktywne przed. Teraz jest przycisk aktywne.  
  
7.  Kliknij przycisk **Pokaż tylko oflagowane wątki** ikony.  
  
    Na liście pojawi się teraz tylko oflagowane wątku. (Możesz kliknąć przycisk pojedynczego flagę, aby powrócić do **Pokaż wszystkie wątki** trybu.)

8. Otwórz okno wątków, wybierając **Debuguj > Windows > wątków**.

    ![Okno wątków](../debugger/media/dbg-threads-window.png "ThreadsWindow")  
  
    W **wątków** okno wątków oflagowanych ma ikonę poświęcone czerwona flaga do niego dołączony.

    > [!TIP]
    > Gdy flagą niektórych wątków, musisz kliknij prawym przyciskiem myszy linię kodu w edytorze kodu i wybrać **Uruchom oflagowane wątki do kursora** (Upewnij się, wybierz kod, że wszystkie oflagowane wątki osiągną). Spowoduje to wstrzymać wątków w wybranym wierszu kodu, dzięki czemu łatwiej kontrolować kolejność wykonywania przez [zamrażanie i odblokowania wątków](#bkmk_freeze).
  
11. W edytorze kodu źródłowego kliknij prawym przyciskiem myszy znacznika wątku ponownie.  
  
     Zwróć uwagę, jakie opcje są teraz dostępne w menu skrótów. Zamiast **flagi**, zobacz teraz **Unflag**. Nie klikaj pozycji **Unflag**.  

     Aby dowiedzieć się, jak i usuwanie oflagowania wątków, przejdź do następnej procedury.  
  
#### <a name="to-unflag-threads"></a>Aby usuwanie oflagowania wątków  
  
1.  W **wątków** okna, kliknij prawym przyciskiem myszy wiersz odpowiadający wątków oflagowanych.  
  
     Zostanie wyświetlone menu skrótów. Ma ona opcje **Unflag** i **Usuń flagę ze wszystkich wątków**.  
  
2.  Aby usuwanie oflagowania wątków, kliknij przycisk **Unflag**.  

    Przyjrzyj się **debugowania lokalizacji** narzędzi ponownie. **Pokaż tylko oflagowane wątki** przycisk jest wyszarzony ponownie. Unflagged jest tylko oflagowane wątku. Ponieważ nie ma żadnych oflagowane wątki, pasek narzędzi ma wstecz do **Pokaż wszystkie wątki** tryb. Kliknij przycisk **wątku** listy i sprawdź, czy widzą wszystkie wątki.  
  
5.  Wróć do **wątków** okna i sprawdź, czy kolumny informacji.  
  
    W pierwszej kolumnie można zauważyć ikony flagi konspektu w każdym wierszu na liście wątku. (Konturu oznacza, że wątek znajduje się bez flagi).  
  
6.  Kliknij flagę ikony konspektu dwoma wątkami drugie i trzecie w dolnej części listy. 

    Ikony flagi stają się czerwony, zamiast zawiera pusty.  
  
7.  Kliknij przycisk w górnej części kolumny flag.  
  
    Kolejność na liście wątku zmienione po kliknięciu przycisku. Lista wątków teraz jest sortowana według oflagowane wątki w górnej części.  
  
8.  Ponownie kliknij przycisk w górnej części kolumny flag.  
  
    Ponownie zmienić kolejność sortowania.  
  
## <a name="more-about-the-threads-window"></a>Więcej informacji na temat okna wątków  
  
#### <a name="to-learn-more-about-the-threads-window"></a>Aby dowiedzieć się więcej na temat okna wątków  
  
1.  W **wątków** okna, sprawdź trzeciej kolumny z lewej strony. Przycisk u góry tej kolumny mówi **identyfikator**.  
  
2.  Kliknij przycisk **identyfikator**.  
  
     Lista wątków teraz jest sortowana według identyfikator wątku.  
  
3.  Kliknij prawym przyciskiem myszy dowolnego wątku na liście. W menu skrótów kliknij **wyświetlacz**.  
  
     Format liczb identyfikator wątku zostanie zmieniona.  
  
4.  Umieść wskaźnik myszy nad **lokalizacji** kolumny w którymkolwiek wątku na liście.  
  
     Opóźnieniem chwilowo pojawi się etykietek danych. Przedstawia on stosu wywołań z częściowa wątku.

     > [!TIP]
     > Dla widoku graficznego stosy wywołań wątków, otwórz [stosów równoległych](../debugger/using-the-parallel-stacks-window.md) okna (podczas debugowania, wybierz **Debug / Windows / stosów równoległych**).  
  
5.  Szukaj w czwartej kolumnie z lewej strony, którego etykietą **kategorii**. Wątki są klasyfikowane na kategorie.  
  
     Pierwszym wątkiem utworzone w procesie jest określana jako głównego wątku. Znajdź go na liście wątku.  
  
6.  Kliknij prawym przyciskiem myszy wątku głównego, a następnie kliknij przycisk **Przełącz do wątku**.  
  
     A **Podziel tryb** zostanie wyświetlone okno. Informuje, że debuger nie wykonuje obecnie żadnego kodu, który będzie możliwe wyświetlenie (ponieważ jest wątku głównego).   
  
7.  Przyjrzyj się **stos wywołań** okna i **debugowania lokalizacji** paska narzędzi.  
  
     Zawartość **stos wywołań** okna zostały zmienione. 

## <a name="bkmk_freeze"></a> Zamrażanie i odblokowania wykonywanie wątków 

Możesz zablokować i odblokować (wstrzymywania i wznawiania) wątków, aby określić kolejność, w którym wątków wykonywania pracy. To może pomóc rozwiązać problemy ze współbieżnością, takich jak zakleszczenie i zastępować warunków.

> [!TIP]
> Jeśli chcesz wykonać, pojedynczego wątku nie zamrażanie innych wątków (również typowego debugowania scenariusza), zobacz [rozpocząć debugowanie aplikacji wielowątkowych](../debugger/get-started-debugging-multithreaded-apps.md#bkmk_follow_a_thread).
  
#### <a name="to-freeze-and-unfreeze-threads"></a>Aby blokowanie i odblokowywanie wątków  
  
1.  W **wątków** okna, kliknij prawym przyciskiem myszy dowolnego wątku, a następnie kliknij przycisk **Zablokuj**.  
  
2.  Przyjrzyj się kolumnie drugiej (bieżącej kolumny wątku). Ikona Wstrzymaj jest teraz wyświetlany. Te ikony Wstrzymaj wskazuje, że wątek jest zablokowana.  
  
3.  Pokaż **zawieszone liczba** kolumny, wybierz je w **kolumn** listy.

    Liczba wstrzymania wątku teraz wynosi 1.  
  
4.  Kliknij prawym przyciskiem myszy wątku zablokowane, a następnie kliknij przycisk **odblokowania**.  
  
     Bieżąca kolumna wątku i **zawieszone liczba** zmiany kolumny. 
  
## <a name="switching-the-to-another-thread"></a>Przełączenie do innego wątku 
  
#### <a name="to-switch-threads"></a>Aby przełączyć wątków  
  
1.  W **wątków** okna, sprawdź drugiej kolumnie z lewej strony (bieżącej kolumny wątku). Przycisk u góry tej kolumny nie ma tekstu ani ikony.
  
2.  Przyjrzyj się kolumnie bieżącego wątku i zwróć uwagę, że jeden wątek ma żółta strzałka. Żółta strzałka wskazuje, że ten wątek jest bieżący wątek (jest to bieżąca lokalizacja wskaźnika wykonywania).
  
    Zanotuj numer identyfikacyjny wątku gdzie widoczna ikona bieżącego wątku. Ikona bieżącego wątku zostanie przesunięty do innego wątku, ale trzeba będzie ją ponownie po zakończeniu. 
  
3.  Kliknij prawym przyciskiem myszy inny wątek, a następnie kliknij przycisk **Przełącz do wątku**.  
  
4.  Przyjrzyj się **stos wywołań** okna w edytorze kodu źródłowego. Zmieniono zawartość.  
  
5.  Przyjrzyj się **debugowania lokalizacji** paska narzędzi. Ikony bieżący wątek został zmieniony, zbyt.  
  
6.  Przejdź do **debugowania lokalizacji** paska narzędzi. Wybierz inny wątek z **wątku** listy.  
  
7.  Przyjrzyj się **wątków** okna. Ikony bieżący wątek został zmieniony.  
  
8. W edytorze kodu źródłowego kliknij prawym przyciskiem myszy znacznika wątku. W menu skrótów polecenie **Przełącz do wątku** i kliknij numer Identyfikatora/nazwy wątku.  
  
     Teraz przejrzane trzy sposoby zmiany bieżącego wątku ikony na inny wątek: przy użyciu **wątków** okna, **wątku** na liście **debugowania lokalizacji** narzędzi i Znacznik wątku w edytorze kodu źródłowego.  
  
     Z znacznika wątku można przełączyć tylko wątków, które zostały zatrzymane w określonej lokalizacji. Za pomocą **wątków** okna i **debugowania lokalizacji** narzędzi, możesz przełączyć się do dowolnego wątku.   
  
## <a name="see-also"></a>Zobacz też  
 [Debuguj aplikacje wielowątkowe](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Porady: przełączanie na inny wątek podczas debugowania](../debugger/how-to-switch-to-another-thread-while-debugging.md)
