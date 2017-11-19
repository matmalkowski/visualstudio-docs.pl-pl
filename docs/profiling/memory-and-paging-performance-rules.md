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
ms.openlocfilehash: 15b9963d10a2a51d34ef3a426ac7a2aba17c2430
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="memory-and-paging-performance-rules"></a>Reguły wydajności pamięci i stronicowania
Reguły wydajności pamięci i stronicowania kategorii zidentyfikować aktywności stronicowania w przebiegu profilowania, która może wpłynąć na wydajność aplikacji i elastyczność.  
  
|||  
|-|-|  
|[DA0014: Wyjątkowo wysoki stopień stronicowania aktywnej pamięci na dysk](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md)|Występuje skrajnie intensywne stronicowanie aktywnej pamięci do i z dysku wystąpił w przebiegu profilowania. Stronicowanie kursy na ten poziom zwykle wpływu na wydajność aplikacji i czas odpowiedzi. Rozważ zmniejszenie przez modyfikowanie algorytmów alokacji pamięci. Masz może również wziąć pod uwagę wymagania dotyczące pamięci aplikacji. Spróbuj uruchomić ponownie profilowania na komputerze, który ma więcej pamięci. Ta zasada generowane, gdy działanie stronicowania przekroczy próg górny reguły D0017.|  
|[DA0017: Wysoki stopień stronicowania aktywnej pamięci na dysk](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|Stosunkowo wysoki stopień stronicowania aktywnej pamięci do i z dysku wystąpił w przebiegu profilowania. Stronicowanie kursy na ten poziom zwykle wpływu na wydajność aplikacji i czas odpowiedzi. Rozważ zmniejszenie przez modyfikowanie algorytmów alokacji pamięci. Masz może również wziąć pod uwagę wymagania dotyczące pamięci aplikacji. Spróbuj uruchomić ponownie profilowania na komputerze, który ma więcej pamięci.|