---
title: Wyświetl wątki w debugerze | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/25/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.threads
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b464213f6443ecbdf07c225fc3698697e91b5c11
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "35677473"
---
# <a name="view-threads-in-the-debugger-in-visual-studio-using-the-threads-window"></a>Widok wątków w debugerze programu Visual Studio za pomocą okna wątków
W **wątków** okna, możesz sprawdzić i Praca z wątkami w aplikacji, na którym wykonujesz debugowanie. Aby uzyskać szczegółowe instrukcje dotyczące sposobu używania **wątków** okna, zobacz [wskazówki: debugowanie za pomocą okna wątki](../debugger/how-to-use-the-threads-window.md).
  
 **Wątków** okno zawiera tabelę, w którym każdy wiersz reprezentuje wątek w aplikacji. Domyślnie w tabeli wymieniono wszystkie wątki w swojej aplikacji, ale można filtrować listę, aby wyświetlić wątki, które Cię interesują. Każda kolumna zawiera inny typ danych. Można także ukryć niektóre kolumny. Jeśli wyświetlane są wszystkie kolumny, zostaną wyświetlone następujące informacje, od lewej do prawej:  
  
-   Kolumna flagi, gdzie można oznaczyć wątek, do którego chcesz zwrócić szczególną uwagę. Aby uzyskać informacje o sposobie Flagowanie wątku, zobacz [jak: Flaga i usuwanie oflagowania wątków](../debugger/how-to-flag-and-unflag-threads.md).  
  
-   Bieżący wątek kolumna, w której żółta strzałka wskazuje bieżący wątek (konspektu Strzałka wskazuje bieżący kontekst debugera dla wątku innej niż bieżąca).
  
-   **Identyfikator** kolumny, która zawiera numer identyfikacyjny dla każdego wątku.  
  
-   **Zarządzanych identyfikator** kolumny, która zawiera numery identyfikacyjne zarządzanych dla wątków zarządzanych.  
  
-   **Kategorii** kolumny, która klasyfikuje wątki wątki interfejsu użytkownika, obsługa wywołania procedury zdalnej lub wątków roboczych. Kategoria specjalne identyfikuje wątku głównego aplikacji.  
  
-   **Nazwa** kolumny, która zidentyfikować każdy wątek przy użyciu nazwy, jeśli taki istnieje, lub jako \<Brak nazwy >.  
  
-   **Lokalizacji** kolumny, które pokazują, w którym wątek jest uruchomiony. Można rozwinąć tej lokalizacji, aby wyświetlić pełny stos wywołania dla wątku.  
  
-   **Priorytet** kolumny, która zawiera priorytet lub pierwszeństwo przypisana przez system do każdego wątku.  
  
-   **Maska koligacji** kolumny, która jest kolumną Zaawansowane (zazwyczaj ukryta). Ta kolumna zawiera Maska koligacji procesorów dla każdego wątku. W systemie wieloprocesorowym Maska koligacji Określa, które procesory, na których można uruchomić wątku.  
  
-   **Zawieszone liczba** kolumny (zazwyczaj ukryta), zawiera licznik wstrzymany, co jest zazwyczaj ukryta. Liczba ta określa, czy można uruchomić wątku. Aby uzyskać wyjaśnienie licznik wstrzymany zobacz "Zawiesza się i rozgrzewania wątki" w dalszej części tego tematu.  
  
-   **Nazwy procesu** kolumny (zazwyczaj ukryta), zawierający proces, do której należy każdego wątku. Ta kolumna może być przydatne podczas debugowania wielu procesów.  
  
### <a name="to-display-the-threads-window-in-break-mode-or-run-mode"></a>Aby wyświetlić okno wątków w trybie przerwania lub w trybie uruchamiania  
  
-   Podczas debugowania, wybierz **debugowania** menu wskaż **Windows**, a następnie kliknij przycisk **wątków**.  
  
### <a name="to-display-or-hide-a-column"></a>Aby wyświetlić lub ukryć kolumny  
  
-   Na pasku narzędzi u góry **wątków** okna, kliknij przycisk **kolumn**, a następnie zaznacz lub wyczyść nazwę kolumny, który chcesz wyświetlić lub ukryć.    

## <a name="display-flagged-threads"></a>Wyświetlanie oflagowane wątki  
 Można flagę wątku, który chcesz poświęcić szczególną uwagę, oznaczając je za pomocą ikony w **wątków** okna. Aby uzyskać więcej informacji, zobacz [jak: Flaga i usuwanie oflagowania wątków](../debugger/how-to-flag-and-unflag-threads.md). W **wątków** okna, które można wybrać, aby wyświetlić wszystkie wątki lub tylko oflagowane wątki.  
  
#### <a name="to-display-only-flagged-threads"></a>Aby wyświetlić tylko oflagowane wątki  
  
-   Wybierz **Pokaż wątki tylko oflagowane** znajdujący się u góry **wątków** okna. (Jeśli jest przyciemniony, musisz najpierw oflagowania wątków.) 

## <a name="freeze-and-thaw-threads"></a>Zablokuj i Odblokuj wątki  
 Zablokowanie wątku systemu nie zostaną uruchomione wykonywanie wątku, nawet jeśli zasoby są dostępne.  
  
 W kodzie natywnym można wstrzymać lub wznowić wątków przez wywołanie funkcji Windows `SuspendThread` i `ResumeThread` lub funkcje MFC [CWinThread::SuspendThread](/cpp/mfc/reference/CWinThread-class#suspendthread) i [CWinThread::ResumeThread](/cpp/mfc/reference/CWinThread-class#resumethread). Jeśli wywołasz `SuspendThread` lub `ResumeThread`, możesz zmienić *zawieszone liczba*, który pojawia się w **wątków** okna. Jednak jeśli blokowanie lub odblokowywanie wątków natywnych, możesz nie zmieniaj licznik wstrzymany. W kodzie natywnym wątku nie można wykonać, chyba że jest rozmrożone i został wstrzymany liczbę zero.  
  
 W kodzie zarządzanym zawiesza się lub rozgrzewania wątku zmienić licznik wstrzymany. W kodzie zarządzanym zablokowanego wątku został wstrzymany liczbę 1. W kodzie natywnym zablokowanego wątku ma liczba wstrzymanych 0, chyba że wątek został wstrzymany `SuspendThread` wywołania.  
  
> [!NOTE]
>  Podczas debugowania wywołań z kodu natywnego do zarządzanego kodu, kod zarządzany działa w tym samym wątku fizycznym jako kodu natywnego, która nazwała go. Zawieszanie lub zawiesza się Wątek macierzysty również zawiesza się kod zarządzany.  
  
#### <a name="to-freeze-or-thaw-execution-of-a-thread"></a>Na blokowanie lub odblokowywanie wykonanie wątku  
  
-   Na pasku narzędzi u góry **wątków** okna, kliknij przycisk **Zablokuj wątki** lub **Odblokuj wątki**.  
  
     Ta akcja dotyczy tylko wątki, które są wybrane w **wątków** okna. 

### <a name="switch-to-another-thread"></a>Przełączanie na inny wątek 

Żółta strzałka wskazuje bieżący wątek (i lokalizacja wskaźnik wykonania). Zielona strzałka z zakręconym ogonkiem wskazuje, że innym niż bieżący wątek jest bieżący kontekst debugera.

#### <a name="to-switch-to-another-thread"></a>Aby przełączyć się do innego wątku  
  
-   Wykonaj jedną z następujących czynności:  
  
    -   Kliknij dwukrotnie wątek.  
  
    -   Kliknij prawym przyciskiem myszy wątku, a następnie kliknij przycisk **Przełącz do wątku**.

## <a name="group-and-sort-threads"></a>Grupy i wątki sortowania  
 Grupowanie wątków nagłówek pojawia się w tabeli dla każdej grupy. Nagłówek zawiera opis grupy, na przykład "Wątek procesu roboczego" lub "Bez flagi wątki", a kontrolka drzewa. Wątki elementu członkowskiego każdej grupy pojawiają się pod nagłówkiem grupy. Jeśli chcesz ukryć wątków członka grupy, można użyć kontrolki drzewa, aby zwinąć grupy.  
  
 Grupowanie ma pierwszeństwo przed sortowania, można Grupuj wątki według kategorii, na przykład i sortować je według Identyfikatora w ramach każdej kategorii.  
  
#### <a name="to-sort-threads"></a>Aby posortować wątków  
  
1.  Na pasku narzędzi u góry **wątków** okna, kliknij przycisk u góry dowolnej kolumny.  
  
     Wątki, teraz są sortowane według wartości w tej kolumnie.  
  
2.  Jeśli chcesz odwrócić porządek sortowania, kliknij ponownie przycisk ten sam.  
  
     Wątki, które znajdowały się u góry listy teraz pojawiają się na dole.  
  
#### <a name="to-group-threads"></a>Grupa wątków  
  
-   W **wątków** pasek narzędzi okna, kliknij przycisk **Grupuj według** , a następnie zaznacz kryteria, które chcesz grupowanie wątków przez.  
  
#### <a name="to-sort-threads-within-groups"></a>Aby posortować wątków w grupach  
  
1.  Na pasku narzędzi u góry **wątków** okna, kliknij przycisk **Grupuj według** , a następnie zaznacz kryteria, które chcesz grupowanie wątków przez.  
  
2.  W **wątków** okna, kliknij przycisk u góry dowolnej kolumny.  
  
     Wątki, teraz są sortowane według wartości w tej kolumnie.  
  
#### <a name="to-expand-or-collapse-all-groups"></a>Rozwiń lub Zwiń wszystkie grupy  
  
-   Na pasku narzędzi u góry **wątków** okna, kliknij przycisk **Rozwiń grupy** lub **Zwiń grupy**.  
  
## <a name="search-for-specific-threads"></a>Wyszukaj określone wątki  
 W [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], możesz wyszukać wątki, które pasują do określonego ciągu. Podczas wyszukiwania dla wątków w **wątków** okna, okno wyświetla wszystkie wątki, które pasuje do ciągu wyszukiwania w dowolnej kolumnie. Te informacje zawierają lokalizacji wątku, który pojawia się w górnej części stosu wywołań w **lokalizacji** kolumny. Domyślnie jednak pełny stos wywołania nie będzie przeszukiwana.  
  
#### <a name="to-search-for-specific-threads"></a>Aby wyszukać określone wątki  
  
-   Na pasku narzędzi u góry **wątków** okna, przejdź do **wyszukiwania** pole, a następnie:  
  
    -   Należy wpisać wyszukiwany ciąg, a następnie naciśnij klawisz ENTER.  
  
         \- lub —  
  
    -   Kliknij przycisk listy rozwijanej obok **wyszukiwania** polu, a następnie wybierz wyszukiwany ciąg z poprzedniego wyszukiwania.  
  
-   (Opcjonalnie) Aby dołączyć pełny stos wywołań wyszukiwania, wybierz **stos wywołań wyszukiwania**.   
  
## <a name="display-thread-call-stacks-and-switching-between-frames"></a>Wyświetlanie stosy wywołań wątku i przełączanie ramek  
W programie wielowątkowym każdy wątek ma swój własny stos wywołań. **Wątków** okna zapewnia wygodny sposób, aby wyświetlić te stosów.

> [!TIP]
> Wizualna reprezentacja stos wywołań dla każdego wątku, można użyć [stosów równoległych](../debugger/get-started-debugging-multithreaded-apps.md) okna.
  
#### <a name="to-view-the-call-stack-of-a-thread"></a>Aby wyświetlić stos wywołań wątku  
  
-   W **lokalizacji** kolumny, kliknij trójkąt odwróconą obok lokalizacji wątku.  
  
     Lokalizacja rozwija Pokaż stos wywołań dla wątku.  
  
#### <a name="to-view-or-collapse-the-call-stacks-of-all-threads"></a>Aby wyświetlić lub Zwiń stosy wywołań wszystkich wątków  
  
-   Na pasku narzędzi u góry **wątków** okna, kliknij przycisk **rozwiń stosy wywołań** lub **Zwiń stosy wywołań**.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji wielowątkowych](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Rozpoczynanie debugowania aplikacji wielowątkowych](../debugger/get-started-debugging-multithreaded-apps.md)