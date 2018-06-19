---
title: Wyświetlanie wątków GPU w debugerze | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.gputthreads
- vs.debug.gputhreads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, GPU threads window
ms.assetid: c647c502-a9f0-48e0-a430-976744a5fa51
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c99e0e1bf64a6a88778d4bfcf27a796916a0f044
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31476731"
---
# <a name="how-to-use-the-gpu-threads-window"></a>Porady: korzystanie z okna wątków GPU
Okno wątków GPU można zbadać i pracy z wątków, które są uruchomione na procesor GPU w aplikacji, która debugowania. Aby uzyskać więcej informacji na temat aplikacji uruchamianych na procesora GPU, zobacz [Przegląd C++ AMP](/cpp/parallel/amp/cpp-amp-overview).  
  
 Okno wątków GPU zawiera tabelę, w której każdy wiersz reprezentuje zestaw wątki GPU, które mają takie same wartości we wszystkich kolumn. Można sortować, zmienianie kolejności, usuwanie i grupować elementy, które są w kolumnach. Można Flaga, Usuń flagę ze, Zablokuj (Wstrzymaj) i odblokowania wątków (Wznów) z okna wątków GPU. Okno wątków GPU wyświetlane są następujące kolumny:  
  
-   Kolumna flagi zaznacz wątku, który chcesz zwrócić szczególną uwagę na.  
  
-   Bieżący wątek kolumna, w którym żółta strzałka wskazuje bieżący wątek.  
  
-   **Liczba wątków** kolumny, która wskazuje liczbę wątków w tej samej lokalizacji.  
  
-   **Wiersza** kolumny, która wyświetla wiersz kodu, w którym znajduje się każdej grupy wątków.  
  
-   **Adres** kolumny, która wyświetla adres instrukcji, w którym znajduje się każdej grupy wątków. Domyślnie ta kolumna jest ukryta.  
  
-   **Lokalizacji** kolumny, który znajduje się w kodzie źródłowym.  
  
-   **Stan** kolumny, która wskazuje, czy wątek jest aktywne, zablokowany, nie jest uruchomiona lub pełna.  
  
-   **Kafelek** kolumny, która zawiera indeks kafelka wątki w wierszu.  
  
 Nagłówek tabeli przedstawiono kafelków i wątku będzie wyświetlany.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-display-the-gpu-threads-window"></a>Aby wyświetlić okno wątków GPU  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów projektu, a następnie wybierz pozycję **właściwości**.  
  
2.  W **strony właściwości** okna dla projektu, w obszarze **właściwości konfiguracji**, wybierz **debugowanie**.  
  
3.  W **debugera, aby uruchomić** listy, wybierz **lokalnego debugera systemu Windows**. W **typ debugera** listy, wybierz **GPU tylko**. Musisz wybrać ten debuger podziału na punkty przerwania w kodzie, który jest uruchamiany na procesorze GPU.  
  
4.  Wybierz **OK** przycisku.  
  
5.  Ustaw punkt przerwania w kodzie procesora GPU.  
  
6.  Na pasku menu wybierz **debugowania**, **Rozpocznij debugowanie**. Poczekaj, aż aplikacji do punktu przerwania.  
  
7.  Jeden na pasku menu wybierz **debugowania**, **Windows**, **wątki GPU**.  
  
### <a name="to-switch-to-a-different-thread"></a>Aby przełączyć się do innego wątku  
  
-   Kliknij dwukrotnie kolumnę. (Klawiatury: zaznacz wiersz i wybierz polecenie wprowadź.)  
  
### <a name="to-display-a-particular-tile-and-thread"></a>Aby wyświetlić kafelka określonego i wątku  
  
1.  Wybierz **rozwiń przełącznik wątku** przycisk okno wątków GPU.  
  
2.  Wprowadź wartości kafelków i wątku w polach tekstowych.  
  
3.  Wybierz przycisk mającym strzałkę.  
  
### <a name="to-display-or-hide-a-column"></a>Aby wyświetlić lub ukryć kolumny  
  
-   Otwórz menu skrótów okna wątków GPU, wybierz pozycję **kolumny**, a następnie wybierz kolumnę, którą chcesz wyświetlić lub ukryć.  
  
### <a name="to-sort-by-a-column"></a>Aby sortować według kolumny  
  
-   Wybierz nagłówek kolumny.  
  
### <a name="to-group-threads"></a>Do grupy wątków  
  
-   Otwórz menu skrótów okna wątków GPU, wybierz pozycję **Group By**, a następnie wybierz jedno wyświetlane nazwy kolumny. Wybierz **Brak** rozgrupować wątki.  
  
### <a name="to-freeze-or-thaw-a-row-of-threads"></a>Aby zablokować lub odblokować wiersza wątków  
  
-   Otwórz menu skrótów wiersza i wybierz polecenie **Freeze** lub **odblokowania**.  
  
### <a name="to-flag-or-unflag-a-row-of-threads"></a>Flaga lub usuwanie oflagowania wątków wiersza  
  
-   Wybierz kolumnę flagę wątku, lub Otwórz menu skrótów dla wątku i wybierz polecenie **flagi** lub **Unflag**.  
  
### <a name="to-display-only-flagged-threads"></a>Aby wyświetlić tylko oflagowane wątki  
  
-   Kliknij przycisk flagi w okno wątków GPU.  
  
## <a name="see-also"></a>Zobacz też  
 [Debuguj aplikacje wielowątkowe](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Porady: Korzystanie z okna czujki równoległej](../debugger/how-to-use-the-parallel-watch-window.md)   
 [Przewodnik: debugowanie aplikacji C++ AMP](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)