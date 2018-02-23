---
title: "Zapoznanie z alokacją pamięci i danych o okresie istnienia obiektu wartości | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET memory profiling method
- Profiling Tools, .NET memory method
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 7d7594ea2356c737d555423082f3c3010835cc7f
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2018
---
# <a name="understanding-memory-allocation-and-object-lifetime-data-values"></a>Zapoznanie z alokacją pamięci i wartościami danych o okresie istnienia obiektu

*Alokacji pamięci .NET* profilowania metody [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędziach profilowania zbiera informacje o rozmiarze i liczba obiektów, które zostały utworzone w alokacji lub zniszczone w wyrzucania elementów bezużytecznych i dodatkowe informacje na temat funkcji *stosu wywołań* wystąpienia zdarzenia. A *stosu wywołań* jest strukturą dynamicznych, która przechowuje informacje dotyczące funkcji, które są wykonywane na procesor.

Profiler pamięci przerwań procesora komputera na każdej alokacji obiektu .NET Framework w profilowanych aplikacji. Jeśli są zbierane również informacje o okresie istnienia obiektu, profiler przerywa działanie procesora po każdym zdarzeniu wyrzucania elementów bezużytecznych w środowisku .NET Framework. Dane są agregowane dla każdej funkcji profilowanych i dla każdego typu obiektu.

## <a name="allocation-data"></a>Alokacja danych

Po wystąpieniu zdarzenia .memory całkowitej liczby i rozmiarów obiektów pamięci przydzielony lub niszczone są zwiększane.

Po wystąpieniu zdarzenia alokacji .memory profilera zwiększa liczby próbki dla każdej funkcji w stosie wywołań. Podczas zbierania danych tylko jednej funkcji w stosie wywołań jest aktualnie wykonywany kod w jego treści funkcji. Inne funkcje na stosie są nadrzędnych w hierarchii wywołań funkcji, które oczekują na funkcje, które są nazywane do zwrócenia.

- Zdarzenia alokacji, zwiększa profilera *wyłącznego* przykładowe liczby funkcji, która jest w trakcie wykonywania instrukcji. Ponieważ wyłącznego próbki jest również częścią łączną (*włącznie*) również jest zwiększany przykłady funkcji liczność próbki włącznie funkcji obecnie aktywne.

- Profiler zwiększa liczność próbki z wartościami granicznymi innych funkcji w stosie wywołań.

## <a name="lifetime-data"></a>Okres istnienia danych

Moduł zbierający elementy bezużyteczne programu .NET Framework zarządza alokacji i wersji pamięci dla aplikacji. Aby zoptymalizować wydajność modułu zbierającego elementy bezużyteczne, sterty zarządzanej jest podzielony na trzy generacje: 0, 1 i 2. Moduł zbierający elementy bezużyteczne czasu wykonywania przechowuje nowych obiektów generacji 0. Obiekty, które pozostają aktualne po kolekcje są awansowane i przechowywane w generacji 1 i 2.

Moduł zbierający elementy bezużyteczne zwraca pamięci przez dealokowanie całego generowania obiektów. Dla obiektów utworzonych przez profilowana aplikacja widok okresu istnienia obiektu Wyświetla liczbę i rozmiar obiektów i generowania, gdy są one odzyskać.