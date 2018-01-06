---
title: "Zapoznanie z wartościami danych próbkowania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sampling profiling method
- Profiling Tools, sampling
ms.assetid: fad540a8-24b6-4ff9-91ce-e67e9a58399d
caps.latest.revision: "22"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 95869fd4c3b52853417c847d32f7507c90471c2d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="understanding-sampling-data-values"></a>Zapoznanie z wartościami danych próbkowania
*Próbkowania* profilowania metody [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzi profilowania przerwań procesora komputera w ustalonych odstępach czasu i zbiera stosu wywołań funkcji. A *stosu wywołań* jest strukturą dynamicznych, która przechowuje informacje dotyczące funkcji, które są wykonywane na procesor.  
  
 **Wymagania**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Wybieranie metod kolekcji](../profiling/how-to-choose-collection-methods.md)   
 [Analizowanie wydajności narzędzi danych](../profiling/analyzing-performance-tools-data.md)