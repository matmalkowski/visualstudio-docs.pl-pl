---
title: Widok szczegółów wątku - dane Kontencji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.threaddetails
helpviewer_keywords:
- Thread Details view
ms.assetid: 874c3b1c-88d8-479a-bb35-1291d9aa8e67
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 241a3d9640e96cb7280321caacfedb406cd52e40
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="thread-details-view---contention-data"></a>Widok szczegółów wątku - dane Kontencji
Widok szczegółów wątku przedstawia wykres osi czasu blokowania zdarzeń w wątku wybranego przebiegu profilowania, które zostały spowodowane kontencji zasobów. To blokującego zdarzenie występuje, gdy wątek jest wymuszone wstrzymania wykonywania, ponieważ inny wątek został zablokowany dostęp do zasobu.  
  
 Ten widok przedstawia osi czasu wykonywania wątku, co poziomy pasek i blokowania zdarzenia jako pasek pionowy na osi poziomej dla wątku. W razie potrzeby można powiększyć sekcji osi czasu, aby wyświetlić poszczególne zdarzenia. Aby wyświetlić ścieżka wykonywania funkcji, które doprowadziły do zdarzenia, kliknij na pasku zdarzeń. Funkcje są wyświetlane w oknie stosu wywołań. Kod źródłowy dla funkcji jest dostępny, kliknięcie nazwę funkcji, aby edytować pliku źródłowego w środowisku IDE programu Visual Studio.  
  
## <a name="navigating-the-timeline"></a>Nawigowanie po osi czasu  
  
#### <a name="to-zoom-in-on-a-timeline-segment"></a>Aby powiększyć segment osi czasu  
  
-   Kliknij i przeciągnij wskaźnik myszy, aby wybrać obszar osi czasu.  
  
     Po zwolnieniu przycisku myszy widoku powiększa do segmentu wybrana wartość czasu. Możesz powtarzać proces powiększenie większej liczby szczegółów. Pole przewijania na pasku przewijania czasu reprezentuje rozmiar względny segmentu czas, który jest wyświetlany w widoku.  
  
#### <a name="to-zoom-out-on-a-timeline"></a>Aby pomniejszyć na osi czasu  
  
-   Kliknij przycisk **Pomniejsz** aby powrócić do poprzedniego poziomu powiększenia.  
  
-   Kliknij przycisk **zresetować powiększenie** do wyświetlenia całego osi czasu w widoku.  
  
#### <a name="to-view-the-call-stack-of-an-event"></a>Aby wyświetlić stos wywołań zdarzeń  
  
-   Na wykresie osi czasu kliknij przycisk pionowy pasek, który reprezentuje zdarzenia.  
  
#### <a name="to-view-or-edit-the-source-code-of-a-function-in-the-call-stack"></a>Aby wyświetlić lub edytować kodu źródłowego funkcji w stosie wywołań  
  
-   W oknie stos wywołań kliknij nazwę funkcji.  
  
 Kod źródłowy funkcja musi być częścią bieżącego projektu.  
  
#### <a name="to-view-the-contention-events-of-a-resource-in-all-threads-in-the-profiling-run"></a>Aby wyświetlić zdarzenia rywalizacji zasobu w wszystkie wątki w przebiegu profilowania  
  
-   Na wykresie osi czasu kliknij nazwę lub identyfikator zasobu.  
  
     [Widok szczegółów zasobów](../profiling/resource-details-view-contention-data.md) pojawia się dla wybranego zasobu.  
  
#### <a name="to-view-the-thread-contention-data-in-the-processes-window"></a>Aby wyświetlić dane kontencji wątku w oknie procesów  
  
-   Na wykresie osi czasu, kliknij przycisk **całkowita**.  
  
     [Widok procesu](../profiling/process-view-contention-data.md) występuje z wątku wybrane.