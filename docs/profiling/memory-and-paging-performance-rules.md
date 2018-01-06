---
title: "Pamięci oraz stronicowanie reguły wydajności | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f37972b2-efe4-4a1c-a5d1-a246ccd76817
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c6466db86c8c27f660fd5a5755f30372efdc7f6c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="memory-and-paging-performance-rules"></a>Reguły wydajności pamięci i stronicowania
Reguły wydajności pamięci i stronicowania kategorii zidentyfikować aktywności stronicowania w przebiegu profilowania, która może wpłynąć na wydajność aplikacji i elastyczność.  
  
|||  
|-|-|  
|[DA0014: Skrajnie intensywne stronicowanie aktywnej pamięci na dysk](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md)|Występuje skrajnie intensywne stronicowanie aktywnej pamięci do i z dysku wystąpił w przebiegu profilowania. Stronicowanie kursy na ten poziom zwykle wpływu na wydajność aplikacji i czas odpowiedzi. Rozważ zmniejszenie przez modyfikowanie algorytmów alokacji pamięci. Masz może również wziąć pod uwagę wymagania dotyczące pamięci aplikacji. Spróbuj uruchomić ponownie profilowania na komputerze, który ma więcej pamięci. Ta zasada generowane, gdy działanie stronicowania przekroczy próg górny reguły D0017.|  
|[DA0017: Intensywne stronicowanie aktywnej pamięci na dysk](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|Stosunkowo wysoki stopień stronicowania aktywnej pamięci do i z dysku wystąpił w przebiegu profilowania. Stronicowanie kursy na ten poziom zwykle wpływu na wydajność aplikacji i czas odpowiedzi. Rozważ zmniejszenie przez modyfikowanie algorytmów alokacji pamięci. Masz może również wziąć pod uwagę wymagania dotyczące pamięci aplikacji. Spróbuj uruchomić ponownie profilowania na komputerze, który ma więcej pamięci.|