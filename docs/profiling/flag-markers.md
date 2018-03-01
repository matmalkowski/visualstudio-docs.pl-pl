---
title: "Flaga znaczników | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.cv.markers.flag
ms.assetid: f3ec919e-63e5-484b-adbf-8f0e79342e75
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 79105e43cba14c12cf0f82edd05b57286c012ee5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="flag-markers"></a>Znaczniki typu flaga
Znacznik flagi reprezentuje coś, który wystąpił w chwili w czasie w aplikacji. Flaga może reprezentować wiele rodzajów zdarzeń aplikacji. Na przykład flagę pokazać po zaplanowano element roboczy w szczególności lub gdy został zgłoszony wyjątek. Środowisk uruchomieniowych, takich jak biblioteka zadań równoległych można również generować flagi.  
  
## <a name="flag-importance"></a>Flaga znaczenie  
 Flagi są wyświetlane w różnych rozmiarach, w zależności od ich ważności. Podobnie jak wszelkie znacznika znaczenie może być niski, normalne, wysoki lub krytyczne.  Na ilustracji przedstawiono wygląd znaczników przez poziom ważności:  
  
 ![Niski, normalny, wysoki i krytyczne znaczenie znaczniki](../profiling/media/cvmarkerimportance.png "CVMarkerImportance")  
Znaczniki przedstawiający znaczenie flagi  
  
## <a name="flag-category"></a>Flaga kategorii  
 Flaga jest wyświetlany w jednym z pięciu różnych kolorów w zależności od jego kategorii. Kolory są używane ponownie, jeśli istnieje więcej niż pięć kategorii. Nie można wybrać kolor. Podobnie jak wszelkie znacznika kategorii może być liczbą całkowitą. Na następnej ilustracji przedstawiono kolorów dla pierwsze pięć kategorii.  
  
 ![Pięć kolorów znaczników kategorii](../profiling/media/cvmarkercategory.png "CVMarkerCategory")  
Znaczniki przedstawiający kategorii  
  
## <a name="alerts"></a>Alerty  
 Alert jest flaga kolorze czerwony, która reprezentuje zdarzenie krytyczne aplikacji, takich jak wyjątek.  Oto alertu:  
  
 ![Znacznik alertu wizualizatora współbieżności](../profiling/media/cvmarkeralert.png "CVMarkerAlert")  
Znacznik alertu  
  
## <a name="aggregation-flags"></a>Flagi agregacji  
 Flagi wystąpić tak blisko siebie w Concurrency Visualizer, że nie można ich indywidualnie wstawiany. Jeśli ten problem wystąpi, szary *flagi agregacji* czy reprezentuje flagi podstawowej są widoczne. Po wskaźnika myszy na ikony, jest wyświetlana etykieta liczba podstawowej flagi, które są przedstawiane. Aby wyświetlić flagi, powiększania. W przypadku aż powiększanie i nadal otrzymywać flagi agregacji, możesz wyświetlić podstawowej flagi w [raport dotyczący znaczników](../profiling/markers-report.md).  
  
 Flagi agregacji są rysowane w różnych rozmiarach. Rozmiar zależy od poziomu ważności najważniejszych flagi w agregacji. Na poniższej ilustracji przedstawiono flagi agregacji w rosnącej kolejności znaczenie.  
  
 ![Agregacja flagi przedstawiający czterech poziomów ważności](../profiling/media/cvmarkeraggregate.png "CVMarkerAggregate")  
Agregacja flag poziom ważności  
  
## <a name="see-also"></a>Zobacz też  
 [Znaczniki CONCURRENCY Visualizer](../profiling/concurrency-visualizer-markers.md)   
 [Zestaw SDK narzędzia Concurrency Visualizer](../profiling/concurrency-visualizer-sdk.md)