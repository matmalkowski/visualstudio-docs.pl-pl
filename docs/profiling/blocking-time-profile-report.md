---
title: Czasu blokowania raport profilowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.blocking
helpviewer_keywords:
- Concurrency Visualizer, Blocking Time Profile Report
ms.assetid: 3bc45af0-3ba6-4fa3-a336-be8e9ae95107
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5c18e3124bb602b65d087a2acf74a7107b754708
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="blocking-time-profile-report"></a>Raport profilowania czasu blokowania
Raporty profilu zapewnienia agregacji danych czasu blokowania stosy wywołań, które są specyficzne dla każdej kategorii blokowania (na przykład "We/wy" lub "Synchronizacji"). Raport wywłaszczanie zawiera listę procesów, które są zastępowane wraz z liczbą wystąpień wywłaszczanie bieżącego procesu. Aby zbudować blokowania raport profilu, narzędzie zbiera blokowania wywołań interfejsu API i sumuje ich do drzewa stosy wywołań. Dane wyświetlane w tych raportach różni się od przez bieżącego zakresu czasu, ukrytych wątków oraz następujące dwa filtry, które mogą być stosowane:  
  
-   Jeśli wybrano opcję tylko mój kod, prezentowane są tylko ramek stosu, które mają kod użytkownika i jeden poziom poniżej kod użytkownika.  
  
-   Jeśli ustawiono wartość redukcji szumu, sortowane stosach, które mają mniej niż określona częstotliwość są pomijane.  
  
 Rozwiń drzewo wywołań zapis wiersza kodu, w którym jest zużywany czas blokowania. Aby zlokalizować wiersz źródła dla wpisu, jego menu skrótów, wybierz **Wyświetl źródło**. Aby zlokalizować wiersza kodu, który wywołał to jeden, w menu skrótów wybierz **wyświetlanie wywołań witryn**. Jeśli tylko jedna lokacja wywołanie jest dostępny, polecenie nawiązuje połączenie ze wyróżniony wiersz kodu dla wywołania. Jeśli dostępnych jest wiele witryn wywołanie, polecenie otwiera okno dialogowe, w którym można zaznacz wpis, a następnie wybierz pozycję **przejdź do źródła** przycisk, aby zlokalizować miejsce wywołania zaznaczony. Często jest najbardziej przydatne wyświetlić kod źródłowy miejsce wywołania z najbardziej wystąpień i/lub najwięcej czasu.  
  
## <a name="blocking-time-report-columns"></a>Blokowanie kolumn raportu czasu  
 W poniższej tabeli przedstawiono kolumn dla każdego blokowania czasu raportu.  
  
|Nazwa kolumny|Opis|  
|-----------------|-----------------|  
|Nazwa|Nazwa funkcji dla każdego poziomu stosu wywołań.|  
|Wystąpienia|Liczba wystąpień blokady wywołań w okresie widoczne.|  
|Całkowity czas blokowania|Suma czasu przeznaczonego dla wszystkich stosy Rzutowanie na tym poziomie drzewa stosu wywołań blokowania. Liczba włącznie jest sumą własny czas blokowania dla tej funkcji i własny czas blokowania dla wszystkich węzłów podrzędnych.|  
|Własny czas blokowania|Łączny czas blokowania przeznaczonego na podczas której ta funkcja jest najniższa stosu wywołań. Wpis stosu wywołań unikatowy, która ma wysoką własny czas blokowania może być funkcją zainteresowań.|  
|Interfejs API/Wait kategorii|Wyświetlane tylko dla funkcji na najniższym poziomie stosu wywołań. W przypadku, gdy podpisu blokowania połączenia zostanie rozpoznany, znajduje się nazwa blokowania interfejsu API. Jeśli podpis nie został rozpoznany, który został zgłoszony przez jądro informacje.|  
|Szczegóły|Pełna nazwa funkcji. Obejmuje to liczba wierszy, gdy jest ona dostępna.|  
  
### <a name="synchronization"></a>Synchronizacja  
 Raport synchronizacji zawiera wywołań, które są odpowiedzialne za segmentów, które blokują synchronizacji i agregacji blokuje razy każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [czas synchronizacji](../profiling/synchronization-time.md)  
  
### <a name="sleep"></a>uśpienia  
 Raport stanu uśpienia zawiera wywołań, które są odpowiedzialne za blokuje czas, który został przypisany czas przeznaczony uśpienia i łączny czas blokowania każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [czas uśpienia](../profiling/sleep-time.md).  
  
### <a name="io"></a>WE/WY  
 We/Wy przedstawia wywołania, które są odpowiedzialne za segmentów, które blokują na We/Wy i agregacji blokuje razy każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [czas operacji We/Wy (Widok wątków)](../profiling/i-o-time-threads-view.md).  
  
### <a name="memory-management"></a>Zarządzanie pamięcią  
 Zarządzanie pamięcią przedstawia wywołania, które są odpowiedzialne za segmentów, które blokują na operacji zarządzania pamięci i agregacji blokuje razy każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [czas zarządzania pamięcią](../profiling/memory-management-time.md).  
  
### <a name="preemption"></a>Wywłaszczanie  
 Wywłaszczanie raport zawiera listę procesów, które są zastępowane bieżącego procesu wraz z liczbą wystąpień.  Można rozwinąć każdy proces, aby wyświetlić określone wątków, które zastąpione wątków w bieżącym procesie i wyświetlić podział wystąpień wywłaszczanie na wątek. Ten raport blokowania jest mniej możliwością od innych, ponieważ wywłaszczanie zwykle nakłada się na potrzeby procesu przez system operacyjny, a nie przez problem w kodzie. Aby uzyskać więcej informacji, zobacz [czas Wywłaszczania](../profiling/preemption-time.md).  
  
### <a name="ui-processing"></a>Przetwarzanie interfejsu użytkownika  
 Raport przetwarzania interfejsu użytkownika zawiera wywołań, które są odpowiedzialne za blokuje segmentów, które blokują na bloki przetwarzania interfejsu użytkownika i agregacji blokuje razy każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [czas przetwarzania interfejsu użytkownika](../profiling/ui-processing-time.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wątków](../profiling/threads-view-parallel-performance.md)