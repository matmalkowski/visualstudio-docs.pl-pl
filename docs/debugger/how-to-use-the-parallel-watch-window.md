---
title: Ustaw czujki w zmiennych w równoległych wątków | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/25/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.parallelwatch
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel watch window
ms.assetid: 28004d9b-420c-48f7-b80e-ab1519802558
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9a142b512c5bbaf5d93dc0302aa39db92fb7c7ae
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="set-a-watch-on-variables-in-parallel-threads-in-visual-studio"></a>Ustaw czujki w zmiennych w równoległych wątków w programie Visual Studio
Okno czujki równoległej może jednocześnie wyświetlać wartości, które posiada jedno wyrażenie w wielu wątkach. Każdy wiersz reprezentuje wątku, który działa w aplikacji, ale może być reprezentowany przez wątek w wielu wierszach. W szczególności każdy wiersz reprezentuje wywołanie funkcji, w której funkcja Podpis pasuje do funkcji w bieżącej ramki stosu. Można sortować, zmienianie kolejności, usuwanie i grupować elementy, które są w kolumnach. Można Flaga, Usuń flagę ze, Zablokuj (Wstrzymaj) i odblokowania wątków (Wznów). Następujące kolumny są wyświetlane w **czujki równoległej** okno:  
  
-   Kolumna flagi zaznacz wątku, który chcesz zwrócić szczególną uwagę na.  
  
-   Bieżąca kolumna wątku, w którym żółta strzałka wskazuje bieżący wątek (zieloną strzałkę z nawiasy tail oznacza, że wątek długoterminowe ma bieżącego kontekstu debugera).  
  
-   Można konfigurować kolumny wyświetlające maszyny, proces, kafelków, zadań i wątku.  
  
    > [!TIP]
    >  Umożliwia wyświetlenie informacjach o zadaniu w **czujki równoległej** okna, należy najpierw otworzyć **zadań** okna.  
  
-   Puste *Dodaj wyrażenie kontrolne* kolumn, w których można użyć wyrażenia, aby obejrzeć.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-display-the-parallel-watch-window"></a>Aby wyświetlić okno czujki równoległej  
  
1.  Ustaw punkt przerwania w kodzie.  
  
2.  Na pasku menu wybierz **debugowania**, **Rozpocznij debugowanie**. Poczekaj, aż aplikacji do punktu przerwania.  
  
3.  Na pasku menu wybierz **debugowania**, **Windows**, **czujki równoległej**, a następnie wybierz Okno czujki. Możesz otworzyć maksymalnie cztery systemu windows.  
  
### <a name="to-add-a-watch-expression"></a>Aby dodać wyrażenia czujki  
  
-   Wybierz jedną z pustym *Dodaj wyrażenie kontrolne* kolumny, a następnie wprowadź wyrażenie czujki.  
  
### <a name="to-flag-or-unflag-a-thread"></a>Flaga lub usuwanie oflagowania wątków  
  
-   Wybierz kolumnę flagi wiersza (pierwszej kolumny) lub Otwórz menu skrótów dla wątku i wybierz polecenie **flagi** lub **Unflag**.  
  
### <a name="to-display-only-flagged-threads"></a>Aby wyświetlić tylko oflagowane wątki  
  
-   Wybierz **Pokaż tylko oflagowane** przycisk w lewym górnym rogu **czujki równoległej** okna.  
  
### <a name="to-switch-to-another-thread"></a>Aby przełączyć się do innego wątku  
  
-   Kliknij dwukrotnie kolumnę bieżącego wątku (druga kolumna). (Klawiatury: zaznacz wiersz, a następnie naciśnij klawisz Enter.)  
  
### <a name="to-sort-a-column"></a>Aby posortować kolumnę  
  
-   Wybierz nagłówek kolumny.  
  
### <a name="to-group-threads"></a>Do grupy wątków  
  
-   Otwórz menu skrótów okna czujki równoległej, wybierz pozycję **Group By**i wybierz element odpowiednie podmenu.  
  
### <a name="to-freeze-or-thaw-threads"></a>Aby zablokować lub odblokować wątków  
  
-   Otwórz menu skrótów wiersza i wybierz polecenie **Freeze** lub **odblokowania**.  
  
### <a name="to-export-the-data-in-the-parallel-watch-window"></a>Aby wyeksportować dane z okna czujki równoległej  
  
-   Wybierz **Otwórz w programie Excel** przycisk, a następnie wybierz pozycję **Otwórz w programie Excel** lub **Eksportuj do pliku CSV**.  
  
### <a name="to-filter-by-a-boolean-expression"></a>Aby filtrować według wyrażenie logiczne  
  
-   Wprowadź wyrażenie logiczne w **Filtruj według wyrażenie warunkowe** pole. Debuger oblicza wyrażenie dla każdego wątku kontekstu. Tylko wiersze, dla których wartość jest `true` są wyświetlane.  
  
## <a name="see-also"></a>Zobacz też  
 [Debuguj aplikacje wielowątkowe](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Porady: Korzystanie z okna wątków GPU](../debugger/how-to-use-the-gpu-threads-window.md)   
 [Przewodnik: debugowanie aplikacji C++ AMP](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)