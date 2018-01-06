---
title: "Wyświetl wątków w debugerze | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 04/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.threads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- Thread.Name property
- debugger, Threads window
- SetThreadName function
- Threads window
- '@TIB'
- debugging [Visual Studio], threads
ms.assetid: 590ffd57-0556-43d8-8962-ee27e5b2b7d7
caps.latest.revision: "44"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: bde9f1c8aa09f8e5961bd228a5f1947c2fc30f82
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="view-threads-in-the-debugger-in-visual-studio-using-the-threads-window"></a>Widok wątków w debugerze programu Visual Studio za pomocą okna wątki
W **wątków** okna, możesz sprawdzić i pracy z wątków w aplikacji, która debugowania. Aby uzyskać szczegółowe instrukcje dotyczące sposobu używania **wątków** okna, zobacz [wskazówki: debugowanie za pomocą okna wątki](../debugger/how-to-use-the-threads-window.md).
  
 **Wątków** okna zawiera tabelę, w której każdy wiersz reprezentuje wątku w aplikacji. Domyślnie w tabeli wymieniono wszystkie wątki w aplikacji, ale można filtrować listę, aby wyświetlić wątków, które są potrzebne. Każda kolumna zawiera inny typ danych. Można również ukryć niektóre kolumny. Jeśli wyświetlane są wszystkie kolumny, poniższe informacje pojawia się, od lewej do prawej:  
  
-   Kolumna flagi, gdzie można oznaczyć wątek, do którego chcesz zwrócić szczególną uwagę. Informacje o sposobie Flaga wątku, zobacz [porady: Flaga i usuwanie oflagowania wątków](../debugger/how-to-flag-and-unflag-threads.md).  
  
-   Bieżący wątek kolumna, w którym żółta strzałka wskazuje bieżący wątek (konspektu Strzałka wskazuje bieżący kontekst debugera z systemem innym niż bieżący wątek).
  
-   **Identyfikator** kolumny, która zawiera numer identyfikacyjny dla każdego wątku.  
  
-   **Zarządzane identyfikator** kolumny, która zawiera numery identyfikacyjne zarządzanego dla wątków zarządzanych.  
  
-   **Kategorii** kolumny, która kategoryzuje wątków jako wątki interfejsu użytkownika, programy obsługi wywołanie procedury zdalnej lub wątków roboczych. Specjalne kategorii identyfikuje wątku głównego aplikacji.  
  
-   **Nazwa** kolumny, które identyfikują każdy wątek według nazwy, jeśli ma ona lub jako \<bez nazwy >.  
  
-   **Lokalizacji** kolumny, która zawiera, gdy wątek jest uruchomiony. Można rozwinąć tej lokalizacji można wyświetlić stosu wywołań pełne wątku.  
  
-   **Priorytet** kolumny, która zawiera priorytet lub priorytet, który system został przypisany do każdego wątku.  
  
-   **Maska koligacji** kolumny, która jest kolumną Zaawansowane (zwykle ukryte). Ta kolumna zawiera Maska koligacji procesorów dla każdego wątku. W systemie wieloprocesorowym Maska koligacji Określa, które procesory, na których można uruchomić wątku.  
  
-   **Zawieszone liczba** kolumny (zazwyczaj ukryta), który zawiera liczba zawieszonych i zwykle jest ukryty. Liczba ta określa, czy można uruchomić wątku. Wyjaśnienie liczba zawieszonych zobacz "Zamrażanie i rozgrzewania wątków" w dalszej części tego tematu.  
  
-   **Nazwa procesu** kolumny (zazwyczaj ukryta), który zawiera proces, do którego należy każdy wątek. Ta kolumna może być przydatne podczas debugowania wiele procesów.  
  
### <a name="to-display-the-threads-window-in-break-mode-or-run-mode"></a>Aby wyświetlić okno wątków w trybie przerwania lub w trybie uruchamiania  
  
-   Podczas debugowania, wybierz **debugowania** menu wskaż **Windows**, a następnie kliknij przycisk **wątków**.  
  
### <a name="to-display-or-hide-a-column"></a>Aby wyświetlić lub ukryć kolumny  
  
-   Na pasku narzędzi u góry **wątków** okna, kliknij przycisk **kolumny**, zaznacz lub wyczyść nazwa kolumny, które chcesz wyświetlić lub ukryć.    

## <a name="display-flagged-threads"></a>Wyświetl oflagowane wątki  
 Mogą oznaczać wątku, który chcesz nadać szczególną uwagę przez oznaczenie go za pomocą ikony w **wątków** okna. Aby uzyskać więcej informacji, zobacz [porady: usuwanie oflagowania wątków i flagi](../debugger/how-to-flag-and-unflag-threads.md). W **wątków** okna można wybrać, aby wyświetlić wszystkie wątki lub tylko oflagowane wątki.  
  
#### <a name="to-display-only-flagged-threads"></a>Aby wyświetlić tylko oflagowane wątki  
  
-   Wybierz **Pokaż wątki tylko oflagowane** przycisk w górnej części **wątków** okna. (Jeśli jest on nieaktywne, musisz najpierw Flaga niektórych wątków.) 

## <a name="freeze-and-thaw-threads"></a>Zablokowania i odblokowania wątków  
 Po zablokowaniu wątku systemu nie zostanie uruchomiona wykonanie wątku, nawet jeśli zasoby są dostępne.  
  
 W kodzie natywnym, można wstrzymać lub wznowić wątków przez wywoływanie funkcji Windows `SuspendThread` i `ResumeThread` lub funkcje MFC [CWinThread::SuspendThread](/cpp/mfc/reference/CWinThread-class.md#cwinthread__suspendthread) i [CWinThread::ResumeThread](/cpp/mfc/reference/CWinThread-class.md#cwinthread__resumethread). Połączeń `SuspendThread` lub `ResumeThread`, możesz zmienić *zawieszone liczba*, która jest wyświetlana w **wątków** okna. Jednak jeśli zablokować lub odblokować wątku macierzystego, nie Zmień liczbę zawieszone. W kodzie natywnym wątku nie można wykonać, chyba że jest rozmrożone i wstrzymaną liczba zero.  
  
 W kodzie zarządzanym zamrażanie lub rozgrzewania wątku Zmień liczbę zawieszone. W kodzie zarządzanym zablokowane wątku ma wstrzymane liczbę 1. W kodzie natywnym, zablokowane wątku ma wstrzymane liczba 0, chyba że wątek został wstrzymany `SuspendThread` wywołania.  
  
> [!NOTE]
>  Podczas debugowania wywołania kodu natywnego do zarządzanego kodu kodu zarządzanego działa w tym samym wątku fizycznych jako kodu macierzystego, który ją. Wstrzymanie lub zamrażanie Wątek macierzysty również zawiesza się kodu zarządzanego.  
  
#### <a name="to-freeze-or-thaw-execution-of-a-thread"></a>Aby zablokować lub odblokować wykonanie wątku  
  
-   Na pasku narzędzi u góry **wątków** okna, kliknij przycisk **Zablokuj wątków** lub **odblokowania wątków**.  
  
     Ta akcja dotyczy tylko wątków, które są wybrane w **wątków** okna. 

### <a name="switch-to-another-thread"></a>Przełączanie na inny wątek 

Żółta strzałka wskazuje bieżący wątek (i położenia wskaźnika wykonywania). Zielona strzałka z nawiasy tail wskazuje, że z systemem innym niż bieżący wątek został bieżącego kontekstu debugera.

#### <a name="to-switch-to-another-thread"></a>Aby przełączyć się do innego wątku  
  
-   Wykonaj jedną z następujących czynności:  
  
    -   Kliknij dwukrotnie którymkolwiek wątku.  
  
    -   Kliknij prawym przyciskiem myszy wątku, a następnie kliknij przycisk **Przełącz do wątku**.

## <a name="group-and-sort-threads"></a>Grupy i sortowania wątków  
 W przypadku grupowania wątków, nagłówek pojawia się w tabeli, dla każdej grupy. Nagłówek zawiera opis grupy, takie jak "Wątków roboczych" lub "Wątków bez flagi" i formantu drzewa. Wątki elementu członkowskiego każdej grupy są wyświetlane w polu nagłówka grupy. Jeśli chcesz ukryć wątków członka grupy, można użyć formantu drzewa Aby zwinąć grupie.  
  
 Ponieważ grupy ma pierwszeństwo przed sortowania, można grupy wątków według kategorii, na przykład i sortować je za pomocą Identyfikatora w każdej kategorii.  
  
#### <a name="to-sort-threads"></a>Aby posortować wątków  
  
1.  Na pasku narzędzi u góry **wątków** okna, kliknij przycisk u góry kolumny.  
  
     Wątki teraz są sortowane według wartości w tej kolumnie.  
  
2.  Jeśli chcesz odwrócić porządek sortowania, kliknij ponownie przycisk tego samego.  
  
     Wątków, które znajdowały się na początku listy, teraz są wyświetlane u dołu.  
  
#### <a name="to-group-threads"></a>Do grupy wątków  
  
-   W **wątków** pasek narzędzi okna, kliknij przycisk **Grupuj według** listy, a następnie kliknij kryteria, które mają być grupy wątków przez.  
  
#### <a name="to-sort-threads-within-groups"></a>Aby posortować wątków w grupach  
  
1.  Na pasku narzędzi u góry **wątków** okna, kliknij przycisk **Grupuj według** listy, a następnie kliknij kryteria, które mają być grupy wątków przez.  
  
2.  W **wątków** okna, kliknij przycisk u góry kolumny.  
  
     Wątki teraz są sortowane według wartości w tej kolumnie.  
  
#### <a name="to-expand-or-collapse-all-groups"></a>Rozwiń lub Zwiń wszystkie grupy  
  
-   Na pasku narzędzi u góry **wątków** okna, kliknij przycisk **grupy rozwiń** lub **Zwiń grupy**.  
  
## <a name="search-for-specific-threads"></a>Wyszukaj określonych wątków  
 W [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], możesz wyszukać wątków, które odpowiada określonego ciągu. Podczas wyszukiwania wątków w **wątków** okna, okno wyświetla wszystkie wątki odpowiadające ciągowi wyszukiwania w dowolnej kolumny. Te informacje zawierają lokalizacji wątku, wyświetlonym u góry stosu wywołań w **lokalizacji** kolumny. Domyślnie jednak stos wywołań pełne nie będzie przeszukiwana.  
  
#### <a name="to-search-for-specific-threads"></a>Aby wyszukać określonego wątków  
  
-   Na pasku narzędzi u góry **wątków** okna, przejdź do **wyszukiwania** pola, a następnie:  
  
    -   Wpisz ciąg wyszukiwania, a następnie naciśnij klawisz ENTER.  
  
         \-lub -  
  
    -   Kliknij obok listy rozwijanej **wyszukiwania** i wybierz wyszukiwany ciąg z poprzedniego wyszukiwania.  
  
-   (Opcjonalnie) Aby dołączyć stosu wywołań pełne wyszukiwanie, wybierz **stos wywołań wyszukiwania**.   
  
## <a name="display-thread-call-stacks-and-switching-between-frames"></a>Stosy wywołań wątku wyświetlania i przełączanie ramek  
W programie wielowątkowe każdy wątek ma własną stosu wywołań. **Wątków** okna oferuje wygodny sposób, aby wyświetlić te stosów.

> [!TIP]
> Wizualną reprezentację stos wywołań dla każdego wątku, można użyć [stosów równoległych](../debugger/get-started-debugging-multithreaded-apps.md) okna.
  
#### <a name="to-view-the-call-stack-of-a-thread"></a>Aby wyświetlić stos wywołań wątku  
  
-   W **lokalizacji** kolumny, kliknij przycisk odwrócony trójkąt obok lokalizacji wątku.  
  
     Lokalizacja zostanie rozwinięty, ukazując stos wywołań dla wątku.  
  
#### <a name="to-view-or-collapse-the-call-stacks-of-all-threads"></a>Aby wyświetlić lub zwinąć stosy wywołań wszystkich wątków  
  
-   Na pasku narzędzi u góry **wątków** okna, kliknij przycisk **rozwiń stosy wywołań** lub **stosy wywołań Zwiń**.  
  
## <a name="see-also"></a>Zobacz też  
 [Debuguj aplikacje wielowątkowe](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Rozpocząć debugowanie aplikacji wielowątkowych](../debugger/get-started-debugging-multithreaded-apps.md)