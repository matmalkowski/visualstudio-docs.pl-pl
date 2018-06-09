---
title: Pamięci oraz stronicowanie reguły wydajności | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f37972b2-efe4-4a1c-a5d1-a246ccd76817
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ec1acb6763d408f9f13ec3044e2cd8137d34e634
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2018
ms.locfileid: "35237656"
---
# <a name="memory-and-paging-performance-rules"></a>Pamięci oraz stronicowanie reguły wydajności
Reguły wydajności pamięci i stronicowania kategorii zidentyfikować aktywności stronicowania w przebiegu profilowania, która może wpłynąć na wydajność aplikacji i elastyczność.  
  
|||  
|-|-|  
|[DA0014: Skrajnie intensywne stronicowanie aktywnej pamięci na dysk](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md)|Występuje skrajnie intensywne stronicowanie aktywnej pamięci do i z dysku wystąpił w przebiegu profilowania. Stronicowanie kursy na ten poziom zwykle wpływu na wydajność aplikacji i czas odpowiedzi. Rozważ zmniejszenie przez modyfikowanie algorytmów alokacji pamięci. Masz może również wziąć pod uwagę wymagania dotyczące pamięci aplikacji. Spróbuj uruchomić ponownie profilowania na komputerze, który ma więcej pamięci. Ta zasada generowane, gdy działanie stronicowania przekroczy próg górny reguły D0017.|  
|[DA0017: Intensywne stronicowanie aktywnej pamięci na dysk](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|Stosunkowo wysoki stopień stronicowania aktywnej pamięci do i z dysku wystąpił w przebiegu profilowania. Stronicowanie kursy na ten poziom zwykle wpływu na wydajność aplikacji i czas odpowiedzi. Rozważ zmniejszenie przez modyfikowanie algorytmów alokacji pamięci. Masz może również wziąć pod uwagę wymagania dotyczące pamięci aplikacji. Spróbuj uruchomić ponownie profilowania na komputerze, który ma więcej pamięci.|