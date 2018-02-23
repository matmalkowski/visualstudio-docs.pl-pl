---
title: "Wspólne wzorce dla nieprawidłowo działających aplikacji wielowątkowych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.cv.threads.tools.gallery
helpviewer_keywords:
- Concurrency Visualizer, common patterns for poorly-behaved multithreaded applications
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: bd8f389efcde93d9a618fbbac272b0f0b2cf5c75
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2018
---
# <a name="common-patterns-for-poorly-behaved-multithreaded-applications"></a>Typowe nieprawidłowo działające wzorce dla aplikacji wielowątkowych

Narzędzia Concurrency Visualizer ułatwia deweloperom zachowanie aplikacji wielowątkowych wizualizacji. To narzędzie zawiera galerię wspólne wzorce dla aplikacji wielowątkowych, które zachowują się nieprawidłowo. Galeria zawiera typowe i rozpoznawalnych visual wzorców, które są udostępniane za pomocą narzędzia, wraz z wyjaśnieniem zachowanie jest reprezentowana przez każdego wzorca prawdopodobnie wynik tego zachowania oraz najczęściej go rozwiązać.

## <a name="lock-contention-and-serialized-execution"></a>Kolizje blokad oraz wykonywania serializacji

![Blokowanie rywalizacji, co powoduje wykonanie serializacji](../profiling/media/lockcontention_serialized.png "LockContention_Serialized")

Czasami zrównoleglone aplikacji stubbornly kontynuuje wykonywanie pojedynczo, nawet jeśli ma kilka wątków i komputer ma wystarczającej liczby rdzeni logicznych. Pierwszy objaw jest niska wydajność wielowątkowe, czasem wręcz nieco wolniej niż serial implementacji. W widoku wątków nie ma wiele wątki uruchomione równolegle; Zamiast tego możesz sprawdzić, czy tylko jeden wątek jest wykonywany w dowolnym momencie. W tym momencie po kliknięciu segmentu synchronizacji w wątku widać stosu wywołań dla wątku zablokowanych (blokujący stos wywołań) i wątku, który usunąć warunek blokowania (stosu wywołań odblokowywania). Ponadto jeśli w proces analizowania występuje stosu wywołań odblokowywania, wyświetlany jest łącznik gotowości wątku. Z tego punktu można przejść do kodu z stosy wywołań blokowania i odblokowywania, aby zbadać przyczynę serializacji jeszcze więcej.

Jak pokazano na poniższej ilustracji, Concurrency Visualizer również może narazić ten symptom w widoku wykorzystania procesora CPU, where, niezależnie od obecności wielu wątków aplikacji wymaga tylko jednego rdzenia logicznego.

Aby uzyskać więcej informacji, zobacz "Wydajności wzorzec 1: Identyfikowanie rywalizacji blokad" w Hazim Shafi [Parallel Performance Tools For Windows](http://go.microsoft.com/fwlink/?LinkID=160569) blogu w witrynie MSDN blog sieci Web.

![Lock Contention](../profiling/media/lockcontention_2.png "LockContention_2")

## <a name="uneven-workload-distribution"></a>Rozkład normalny obciążenia

![Nierówna obciążeń](../profiling/media/unevenworkload_1.png "UnevenWorkLoad_1")

W przypadku nieprawidłowych rozkład pracy między kilka równoległych wątków w aplikacji, wzorzec typowe schodki jest widoczne jako każdy wątek nie ukończy pracy, jak pokazano na poprzedniej ilustracji. Narzędzia Concurrency Visualizer zawiera najczęściej ścisłe czasu dla każdego wątku współbieżnych. Jednak te wątków zwykle zakończona w nieprawidłowy sposób zamiast końcowy jednocześnie. Ten wzorzec wskazuje nieregularne dystrybucji pracy grupie równoległych wątków, które może spowodować zmniejszenie wydajności. Na przykład problem najlepiej Aby obliczyć ponownie algorytm za pomocą którego został podzielony między równoległych wątków roboczych.

Jak pokazano na poniższej ilustracji, Concurrency Visualizer również może narazić ten symptom w widoku wykorzystania procesora CPU jako stopniowego step-down użycia procesora CPU.

![Nierówna obciążeń](../profiling/media/unevenworkload_2.png "UnevenWorkload_2")

## <a name="oversubscription"></a>Nadsubskrypcji

![Nadsubskrypcji](../profiling/media/oversubscription.png "Nadsubskrypcji")

W przypadku nadsubskrypcji liczba aktywnych wątków w procesie jest większa niż liczba dostępnych rdzenie logiczne w systemie. Na poprzedniej ilustracji przedstawiono wyniki nadsubskrypcji z pominiętym wywłaszczanie znaczących w wszystkie aktywne wątki. Ponadto Legenda pokazuje spędzony znaczną część czasu w wywłaszczanie (procent 84 w tym przykładzie). Może to oznaczać, że proces jest zapytaniem systemu można wykonać większą liczbę jednoczesnych wątków niż liczba rdzeni logicznych. Jednak może to także oznaczać czy inne procesy w systemie korzystają z zasobów, które zostały zakłada, że mają być dostępne dla tego procesu.

Podczas oceny ten problem, należy rozważyć następujące:

- Może być oversubscribed całego systemu. Należy wziąć pod uwagę, że inne procesy w systemie może preempting Twojego wątków. W przypadku wstrzymania przez segment wywłaszczanie w widoku wątków etykietka narzędzia określi wątku i procesu wywłaszczone wątku. Ten proces nie jest niekoniecznie ten, który jest wykonywany podczas procesu została przeniesiona przez cały czas, ale stanowi wskazówkę o co utworzone wykorzystania wywłaszczanie względem procesu.

- Należy ocenić, jak procesu Określa odpowiedniej liczby wątków wykonywania w tej fazie pracy. Jeśli procesie oblicza bezpośrednio liczba aktywnych wątków równoległe, należy rozważyć zmodyfikowanie tego algorytmu kontu lepsze liczby dostępne rdzenie logiczne w systemie. Jeśli używasz współbieżności środowiska wykonawczego, biblioteka zadań równoległych lub PLINQ te biblioteki wykonały obliczania liczby wątków.

## <a name="inefficient-io"></a>Nieefektywne we/wy

![Inefficient I&#47;O](../profiling/media/inefficient_io.png "Inefficient_IO")

Nadmierne zużycie lub ich nieuprawnione użycie operacji We/Wy jest częstą przyczyną wydajność w aplikacjach. Należy wziąć pod uwagę poprzedniej ilustracji. Profil widocznej osi czasu pokazuje, że 42 procent czasu widoczne wątku jest używany przez operacje We/Wy. Oś czasu pokazuje dużo operacji We/Wy, co oznacza, że profilowana aplikacja często jest zablokowana z powodu operacji We/Wy. Aby wyświetlić szczegółowe informacje o rodzajach We/Wy i gdy program jest zablokowany, powiększenie fragmentu regionów powodować problemy, przejrzyj profil widocznej osi czasu, a następnie kliknij określonego bloku we/wy, aby wyświetlić bieżące stosy wywołań.

## <a name="lock-convoys"></a>Konwojów blokady

![Blokowanie konwojów](../profiling/media/lock_convoys.png "Lock_Convoys")

Blokady konwojów wystąpić, gdy aplikacja uzyskuje blokady w kto, obsługiwane w pierwszej kolejności i przyjęcia szybkości blokady jest wyższy niż częstotliwość nabycia. Kombinacja tych dwóch sytuacji powoduje, że żądania blokady rozpocząć tworzenie kopii zapasowej. Jednym ze sposobów zwalczania tego problemu polega na użyciu "nieuczciwych" blokad, blokad, które zapewniają dostęp do pierwszego wątku je znaleźć w Stanach odblokowane. Na poprzedniej ilustracji przedstawiono to zachowanie który. Rozwiązuje problem, spróbuj zmniejszyć rywalizacji o obiektów synchronizacji i spróbuj użyć nieuczciwej blokad.

## <a name="see-also"></a>Zobacz także

[Widok wątków](../profiling/threads-view-parallel-performance.md)