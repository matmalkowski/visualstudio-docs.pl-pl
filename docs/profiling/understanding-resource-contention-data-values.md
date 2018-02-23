---
title: "Zapoznanie z wartościami danych Kontencji zasobów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 7158af10ccb7b34b6bf5836cd6176216fbdb6832
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2018
---
# <a name="understanding-resource-contention-data-values"></a>Zapoznanie z wartościami danych kontencji zasobów

Profilowanie kontencji zasobów zbiera szczegółowe informacje stosu wywołań zawsze się, że konkurencyjnych wątków w aplikacji zostało wymuszone oczekiwania na dostęp do zasobu udostępnionego.

Zasób rywalizacji raporty zawierają liczba rywalizacji i całkowity czas przeznaczony oczekiwania zasobu dla modułów, funkcje, wierszy kodu źródłowego i instrukcje, w których wystąpił oczekiwania.

- Wraz z wartościami granicznymi wartości wyświetlane liczba rywalizacji, których wymuszone funkcja oczekiwania przez kontencji zasobów i łączny czas oczekiwania funkcji.  Rywalizacji, które zostały spowodowane funkcje podrzędne, które zostały wywołane przez funkcję znajdują się w wartości włącznie.

- Wyłączny wartości są wyświetlane tylko liczba rywalizacji mających który wymuszone funkcja oczekiwania i które zostały spowodowane przez kod w treści funkcji. Rywalizacji spowodowane przez funkcje podrzędne nie są uwzględniane. Własny czas dla funkcji obejmuje również czasy oczekiwania, które zostały spowodowane instrukcje w treści funkcji.

Widoki raportu kontencji zasobów również obejmują wykresy oś czasu Pokaż zdarzenia rywalizacji indywidualnych wraz z upływem czasu i Pokaż stosy wywołań, które utworzone konkretnego zdarzenia. Aby uzyskać więcej informacji, zobacz jeden z następujących tematów:

- [Widok szczegółów wątku](../profiling/thread-details-view-contention-data.md)

- [Widok szczegółów zasobów](../profiling/resource-details-view-contention-data.md)

Aby uzyskać więcej informacji o trybie drugi profilowania współbieżności, zobacz [Concurrency Visualizer](../profiling/concurrency-visualizer.md).