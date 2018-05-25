---
title: Zapoznanie z wartościami danych próbkowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method
- Profiling Tools, sampling
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a6eb52273633e0b65aa4a7a7049198c49c20633d
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2018
---
# <a name="understand-sampling-data-values"></a>Zrozumienie wartościami danych próbkowania

*Próbkowania* metoda Visual Studio Profiling Tools profilowania przerwań procesora komputera w ustalonych odstępach czasu i zbiera stosu wywołań funkcji. A *stosu wywołań* jest strukturą dynamicznych, która przechowuje informacje dotyczące funkcji, które są wykonywane na procesor.

Analiza profilera Określa, czy procesor jest wykonywanie kodu w procesie docelowym. Jeśli procesor nie jest wykonywanie kodu w procesie docelowym, przykładowej zostaną odrzucone.

Jeśli procesor jest wykonywanie kodu docelowego, profilera zwiększa liczby próbki dla każdej funkcji w stosie wywołań. W tym czasie próbki tylko jednej funkcji w stosie wywołań jest w trakcie wykonywania kodu. Inne funkcje na stosie są nadrzędnych w hierarchii wywołania funkcji, które oczekują na ich elementy podrzędne do zwrócenia.

Przykładowe zdarzenia zwiększa profilera *wyłącznego* przykładowe liczby funkcji, która jest w trakcie wykonywania instrukcji. Ponieważ wyłącznego próbki jest również częścią łączną (*włącznie*) również jest zwiększany przykłady funkcji liczność próbki włącznie funkcji obecnie aktywne.

 Profiler zwiększa liczność próbki z wartościami granicznymi innych funkcji w stosie wywołań.

## <a name="inclusive-samples"></a>Przykłady włącznie

Łączna liczba próbek, które są zbierane podczas wykonywania funkcji docelowej.

Dotyczy to również przykłady, które są zbierane podczas bezpośrednie wykonywanie kodu funkcji i przykłady, które są zbierane podczas wykonywania funkcji podrzędne, które są wywoływane przez funkcję docelowej.

## <a name="exclusive-samples"></a>Wyłącznych próbek

Liczba próbek, zebrane podczas bezpośrednie wykonywanie instrukcji funkcja docelowej.

Wyłącznych próbek nie zawierają przykłady, które są zbierane podczas wykonywania funkcji wywoływanych przez funkcję docelowej.

## <a name="inclusive-percent"></a>Procent włącznie

Wartość procentowa całkowita liczba włącznie przykłady w przebiegu profilowania, które są włącznie przykłady zakresu funkcji lub danych.

## <a name="exclusive-percent"></a>Procent wyłączności

Procent całkowitej liczby wyłącznych próbek w przebiegu profilowania, które są wyłącznych próbek zakres funkcji lub danych.

## <a name="see-also"></a>Zobacz także

[Instrukcje: wybieranie metod zbierania](../profiling/how-to-choose-collection-methods.md)  
[Analizowanie danych dotyczących narzędzi do oceny wydajności](../profiling/analyzing-performance-tools-data.md)