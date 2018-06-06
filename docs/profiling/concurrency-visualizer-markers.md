---
title: Znaczniki CONCURRENCY Visualizer | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.markersui
ms.assetid: c4692d17-6cd2-4ad1-8590-d7275c771c70
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4f59167b356f4a04b4b37e699fbe49f1ea82943e
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34692304"
---
# <a name="concurrency-visualizer-markers"></a>Znaczniki CONCURRENCY Visualizer
Narzędzia Concurrency Visualizer znaczniki są ikony, które reprezentują zdarzenia w aplikacji.  Zwykle aplikacja generuje te zdarzenia do wyznaczenia fazy lub wystąpień w aplikacji.  Zdarzenia mogą być generowane przez aplikację lub biblioteki i środowisk uruchomieniowych, który korzysta z aplikacji.  
  
## <a name="kinds-of-markers"></a>Rodzaje znaczników  
 Narzędzia Concurrency Visualizer używa trzy rodzaje znaczników do reprezentowania aplikacji zdarzenia: flagi wiadomości i obejmuje.  
  
1.  Użyj *flagi* wskazująca interesujące punktu w czasie w aplikacji.  Na przykład można użyć flagi do reprezentowania osiągnięcie w wartości zmiennej pewnej wartości progowej lub został zgłoszony wyjątek.  
  
2.  A *komunikat* również znaczniki punktu w czasie, ale może być używany dla stylu dziennika śledzenia.  Na przykład co może mieć zostały utworzyć zrzutu w pliku dziennika, który może teraz zawijać w wywołaniu wiadomości, aby można go śledzenia i wyświetlać go w Concurrency Visualizer. Umożliwia także Concurrency Visualizer do eksportowania tych danych do pliku CSV.  
  
3.  A *span* reprezentuje interwał czasu w aplikacji, na przykład jeden z jego faz.  
  
## <a name="marker-linkage-to-threads"></a>Połączenie znacznika wątków  
 Każdy wątek, który generuje znaczników ma kanału oddzielne osi czasu.  Identyfikator wątku, który jest odpowiedzialny za generowanie zdarzeń znaczników jest wyświetlany obok opis kanału znacznika.  Identyfikator, który jest wyświetlany po lewej stronie kanał znacznika odpowiada identyfikator inny wątek w bieżącym procesie.  
  
## <a name="marker-importance"></a>Znaczenie znacznika  
 Znaczniki może mieć jedną z czterech poziomów ważności: Niski, normalne wysokiej i krytyczne.  Można filtrować źródeł znaczników na podstawie poziomu ważności.  Na przykład, jeśli chcesz zobaczyć znaczniki z danego źródła z normalnym lub krytyczne znaczenie, można skonfigurować filtr w [Zaawansowane ustawienia](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) okno dialogowe. Znaczenie znacznik jest wyświetlany w jego etykietka narzędzia, a w [raport dotyczący znaczników](../profiling/markers-report.md).  
  
## <a name="marker-category"></a>Kategoria znacznika  
 Kategoria znacznika wskazuje grupę znacznika zdarzenia, które pochodzą z tego samego źródła.  Concurrency Visualizer używa kolorów, aby odróżnić różne kategorie flagi i zakresami. Można skonfigurować Concurrency Visualizer na używanie kategorii do filtrowania zdarzeń znacznika od dostawcy określonego zdarzenia.  Użyj [Zaawansowane ustawienia](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) okno dialogowe, aby skonfigurować filtr.  
  
## <a name="known-sources-of-markers"></a>Znane źródeł znaczników  
 U innego dostawcy ETW mogą generować znaczniki, tak długo, jak dostawca działa zgodnie z określonymi ograniczeniami. Można skonfigurować Concurrency Visualizer do nasłuchiwania źródła zdarzeń dodatkowe znaczniki. Domyślnie nasłuchuje go do tych źródeł zdarzeń:  
  
-   [Zestaw SDK narzędzia Concurrency Visualizer](../profiling/concurrency-visualizer-sdk.md)  
  
-   [Biblioteka zadań równoległych (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl)  
  
-   [Przepływ danych](/dotnet/standard/parallel-programming/dataflow-task-parallel-library)  
  
-   [Równoległe LINQ (PLINQ)](/dotnet/standard/parallel-programming/parallel-linq-plinq)  
  
-   [Środowisko uruchomieniowe współbieżności](/cpp/parallel/concrt/concurrency-runtime)  
  
-   [Obsługa znaczników scenariusza](http://msdn.microsoft.com/en-us/e3b55bc2-b451-4214-ae00-0c7f5a5baec8)  
  
-   [C++ AMP (C++ Accelerated Massive Parallelism)](/cpp/parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism)  
  
 Można użyć karty znaczników w [Zaawansowane ustawienia](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) okno dialogowe do kontrolowania, czy w Concurrency Visualizer i są wyświetlane znaczniki z różnych źródeł można filtrować według kategorii i ważności znaczników.  
  
## <a name="markers-from-eventsource"></a>Znaczniki od elementu EventSource  
 Narzędzia Concurrency Visualizer można również wyświetlić zdarzenia EventSource.  Aby uzyskać więcej informacji, zobacz [EventSource wizualizowanie zdarzeń jako znaczniki](../profiling/visualizing-eventsource-events-as-markers.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Znaczniki typu Flaga](../profiling/flag-markers.md)   
 [Znaczniki komunikatu](../profiling/message-markers.md)   
 [Znaczniki zakresu](../profiling/span-markers.md)   
 [Wizualizowanie zdarzeń EventSource znaczników](../profiling/visualizing-eventsource-events-as-markers.md)