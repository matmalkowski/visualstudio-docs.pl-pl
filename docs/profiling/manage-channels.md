---
title: Zarządzanie kanałami | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.tools.managechannels
helpviewer_keywords:
- Concurrency Visualizer, Manage Channels
ms.assetid: 507b06e9-bb56-4a72-8fd5-f91f958da6fc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 89c5727b8bc294ae28f48a6e1fc3194b258b9555
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34844435"
---
# <a name="manage-channels"></a>Zarządzanie kanałami
W **Widok wątków** w narzędzia Concurrency Visualizer można organizować kanały procesu, aby zbadać konkretnych wzorców. Można sortować kanały, przenieś je w górę i w dół i Ukryj lub je wyświetlić.  
  
## <a name="sort-by"></a>Sortuj według  
 Sortuj według formantu służy do sortować wątki różnych kryteriów, w oparciu o bieżący poziom powiększenia. Jest to szczególnie przydatne podczas wyszukiwania określonego wzorca. Można sortować według tych kryteriów:  
  
|Kryteria|Definicja|  
|--------------|----------------|  
|Godzina rozpoczęcia|Sortuje wątków według ich godziny rozpoczęcia. Jest to domyślny porządek sortowania.|  
|Godzina zakończenia|Sortuje wątków według ich zakończenia.|  
|Wykonanie|Wartość procentowa czasu przeznaczonego na wykonanie sortowania wątków.|  
|Synchronizacja|Procent czasu poświęcana w synchronizacji podczas sortowania wątków.|  
|WE/WY|Sortowania wątków procent czasu, który jest przeznaczony na We/Wy (odczytywania i zapisywania danych).|  
|uśpienia|Sortuje wątków według wartości procentowej czasu, przez który odbywa się w trybie uśpienia.|  
|Stronicowania|Procent czasu poświęcana w stronicowania sortowania wątków.|  
|Wywłaszczanie|Procent czasu poświęcana w wywłaszczanie sortowania wątków.|  
|Przetwarzanie interfejsu użytkownika|Wartość procentowa czasu przeznaczonego na przetwarzania interfejsu użytkownika podczas sortowania wątków.|  
  
## <a name="move-selected-channel-up-or-down"></a>Przeniesienie wybranego kanału w górę lub w dół  
 Formanty umożliwia przenoszenie kanał w górę lub w dół na liście. Można na przykład pozycji powiązanych kanały obok siebie, aby sprawdzić określonego wzorca lub relacji między wątkami.  
  
## <a name="move-selected-channel-to-top-or-bottom"></a>Przenieś wybrany kanał do góry lub u dołu  
 Wybrane kanały można przenieść do góry lub u dołu listy, aby zbadać określonego wzorca lub przenoszenia niektórych kanałów przeszkadza podczas badania innych.  
  
## <a name="hide-selected-channels"></a>Ukryj wybranych kanałów  
 Wybierz ten formant, jeśli chcesz ukryć kanałów. Na przykład jeśli wątek to 100 procent synchronizacji przez cały okres istnienia procesu zarządzanego komputera, zostanie można ukryta jak inne wątki.  
  
> [!NOTE]
>  Ukrywanie wątku spowoduje również usunięcie go z czas obliczeń, który jest wyświetlany w legendzie active i w raportach profilu.  
  
## <a name="show-all-channels"></a>Pokaż wszystkie kanały  
 Ten formant jest aktywny, gdy jeden lub więcej kanały są ukryte. Jeśli zostanie wybrana, wszystkie elementy ukryte są wyświetlane i nastąpi powrót do obliczenia czasu.  
  
## <a name="move-markers-to-top"></a>Przenieś na początek znaczników  
 Jeśli śledzenia zawiera znacznika zdarzenia, można użyć tego polecenia, aby przenieść kanały znacznika do góry osi czasu. Ich kolejność względne są zachowywane.  
  
## <a name="group-markers-by-thread"></a>Znaczniki grupy przez wątek  
 Jeśli śledzenie zawiera znacznika zdarzenia, można użyć tego polecenia, do grupy znacznika kanałów w wątku, który wygenerował zdarzenia znacznika.  Kanały dysku zostaną przeniesione na początku listy kanałów i kanały GPU zostaną przeniesione do dołu.  
  
## <a name="see-also"></a>Zobacz także  
 [Formant powiększania (Widok wątków)](../profiling/zoom-control-threads-view.md)   
 [Tryb pomiarowy wł. / wył.](../profiling/measure-mode-on-off.md)   
 [Widok wątków](../profiling/threads-view-parallel-performance.md)