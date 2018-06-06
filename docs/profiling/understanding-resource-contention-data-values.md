---
title: Zapoznanie z wartościami danych Kontencji zasobów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c06722e9270269ca674370d5bf8b1925d850ce00
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34477408"
---
# <a name="understand-resource-contention-data-values"></a>Zrozumienie wartościami danych kontencji zasobów

Profilowanie kontencji zasobów zbiera szczegółowe informacje stosu wywołań zawsze się, że konkurencyjnych wątków w aplikacji zostało wymuszone oczekiwania na dostęp do zasobu udostępnionego.

Zasób rywalizacji raporty zawierają liczba rywalizacji i całkowity czas przeznaczony oczekiwania zasobu dla modułów, funkcje, wierszy kodu źródłowego i instrukcje, w których wystąpił oczekiwania.

- Wraz z wartościami granicznymi wartości wyświetlane liczba rywalizacji, których wymuszone funkcja oczekiwania przez kontencji zasobów i łączny czas oczekiwania funkcji.  Rywalizacji, które zostały spowodowane funkcje podrzędne, które zostały wywołane przez funkcję znajdują się w wartości włącznie.

- Wyłączny wartości są wyświetlane tylko liczba rywalizacji mających który wymuszone funkcja oczekiwania i które zostały spowodowane przez kod w treści funkcji. Rywalizacji spowodowane przez funkcje podrzędne nie są uwzględniane. Własny czas dla funkcji obejmuje również czasy oczekiwania, które zostały spowodowane instrukcje w treści funkcji.

Widoki raportu kontencji zasobów również obejmują wykresy oś czasu Pokaż zdarzenia rywalizacji indywidualnych wraz z upływem czasu i Pokaż stosy wywołań, które utworzone konkretnego zdarzenia. Aby uzyskać więcej informacji, zobacz jeden z następujących tematów:

- [Widok szczegółów wątku](../profiling/thread-details-view-contention-data.md)

- [Widok szczegółów zasobów](../profiling/resource-details-view-contention-data.md)

Aby uzyskać więcej informacji o trybie drugi profilowania współbieżności, zobacz [Concurrency Visualizer](../profiling/concurrency-visualizer.md).