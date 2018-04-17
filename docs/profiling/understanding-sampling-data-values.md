---
title: Zapoznanie z wartościami danych próbkowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method
- Profiling Tools, sampling
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4e26ba5b98308e536bdaf9401567d9891bac64c1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="understanding-sampling-data-values"></a>Zapoznanie z wartościami danych próbkowania

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

[Porady: Wybieranie metod kolekcji](../profiling/how-to-choose-collection-methods.md)  
[Analizowanie wydajności narzędzi danych](../profiling/analyzing-performance-tools-data.md)