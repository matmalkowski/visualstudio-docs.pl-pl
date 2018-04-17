---
title: Znaczniki zakresu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.span
ms.assetid: 736b7765-9c71-44d7-85e5-79787d13d91c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 697603cea62087163dea5115a74aae4c401b2c2c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="span-markers"></a>Znaczniki zakresu
Znacznik zakresu reprezentuje fazę opisową aplikacji. Na przykład można użyć zakres do reprezentowania przedział czasu, w którym element roboczy w szczególności jest przetwarzana. Długość jego reprezentuje czas trwania fazy odpowiedniej aplikacji. Ta ilustracja przedstawia zakres w Concurrency Visualizer:  
  
 ![Znacznik zakresu na Concurrency Visualizer](../profiling/media/cvmarkerspan.png "CVMarkerSpan")  
Znacznik zakresu na Concurrency Visualizer  
  
## <a name="span-category"></a>Kategoria zakresu  
 Znacznik zakresu jest wyświetlany w jednym z pięciu różnych kolorach, w zależności od jego kategorii. Kolory są powtarzane, jeśli istnieje więcej niż pięć kategorii. Kategoria może być liczbą całkowitą. Na ilustracji przedstawiono pięć możliwych kolorów:  
  
 ![Pięć zakresów w różnych kategoriach](../profiling/media/cvmarkerspancategory.png "CVMarkerSpanCategory")  
Kolory pierwsze pięć kategorii zakresu  
  
## <a name="span-aggregation-markers"></a>Agregacja znaczniki zakresu  
 Czasami zakresu znaczników występują tak blisko siebie w Concurrency Visualizer, że nie można ich indywidualnie wstawiany. Jeśli ten problem wystąpi, szary *znacznika agregacji zakresu* czy reprezentuje podstawowej zakresy są widoczne. Po wskaźnika myszy na ikony, jest wyświetlana etykieta liczba podstawowej zakresy, które są przedstawiane. Aby wyświetlić zakresy, powiększania. Powiększ do końca, nadal jest wyświetlany znacznik agregacji zakresu można wyświetlić podstawowy znaczniki zakresu w [raport dotyczący znaczników](../profiling/markers-report.md). Na ilustracji przedstawiono znacznika zakresu agregacji:  
  
 ![Wartość zagregowana span znacznik Concurrency Visualizer](../profiling/media/cvmarkerspanaggregate.png "CVMarkerSpanAggregate")  
Znacznik span agregacji  
  
## <a name="see-also"></a>Zobacz też  
 [Znaczniki CONCURRENCY Visualizer](../profiling/concurrency-visualizer-markers.md)   
 [Zestaw SDK narzędzia Concurrency Visualizer](../profiling/concurrency-visualizer-sdk.md)