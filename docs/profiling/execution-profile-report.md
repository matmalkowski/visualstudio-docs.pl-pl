---
title: Raport profilu wykonania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Profile Report
ms.assetid: c8128472-a8ed-46f4-b1c8-a25358d6f2c1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b2f878efffd658cbfa243ae4947613603db59777
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="execution-profile-report"></a>Raport profilu wykonania
Raport profilu wykonania jest profil próbkowania tradycyjnych. Pobierane są mniej więcej co milisekund okresach po wątek jest uruchomiony na rdzenia logicznego i Concurrency Visualizer kompilacje drzewo wywołań typowe przez sortowanie skumulowany zbiór stosy próbki. Dane w tej tabeli może wpłynąć na bieżącego zakresu czasu i ukrytych wątków, a te filtry, które mogą być stosowane:  
  
-   Jeśli wybrano opcję tylko mój kod, są wyświetlane tylko ramek stosu mających kod użytkownika, a także jeden poziom w dół kodu użytkownika.  
  
-   Jeśli ustawiono wartość redukcji szumu, posortowane stosach, które mają mniej niż określona częstotliwość są odfiltrowywane z raportu  
  
 W poniższej tabeli przedstawiono kolumny w raporcie.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|Nazwa|Nazwa funkcji dla każdego poziomu stosu wywołań.|  
|Przykłady włącznie|Łączna liczba próbek, które są zbierane dla wszystkich stosy Rzutowanie na tym poziomie drzewa stosu wywołań. Liczba włącznie jest sumą wyłącznych próbek dla tej funkcji i włącznie liczniki dla wszystkich węzłów podrzędnych.|  
|Wyłącznych próbek|Łączna liczba próbek zebranych, dla których ta funkcja jest najniższa stosu wywołań.|  
|% Łącznie|Procent całkowitej liczby próbek wyświetlanym w kolumnie przykłady włącznie. Wartości procentowe są zaokrąglane do dwóch miejsc po przecinku.|  
|% Na wyłączność|Procent całkowitej liczby próbek wyświetlanym w kolumnie wyłącznych próbek. Wartości procentowe są zaokrąglane do dwóch miejsc po przecinku.|  
|Szczegóły|Pełna nazwa funkcji. Obejmuje to liczba wierszy, gdy jest ona dostępna.|  
  
 Ta tabela raportu można przejrzeć w [czas wykonywania (Widok wątków)](../profiling/execution-time-threads-view.md) widoku.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wątków](../profiling/threads-view-parallel-performance.md)