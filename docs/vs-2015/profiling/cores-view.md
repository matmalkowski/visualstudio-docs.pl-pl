---
title: Widok rdzeni | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.view.cores
helpviewer_keywords:
- Concurrency Visualizer, Cores View
ms.assetid: e47af672-9785-4899-bd45-4d9dda3c396f
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bce1c1ca458b8d06af89c669a76a2a93371fad5a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42682792"
---
# <a name="cores-view"></a>Widok rdzeni
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [widoku rdzeni](https://docs.microsoft.com/visualstudio/profiling/cores-view).  
  
Widok rdzeni pokazuje, jak wykonanie wątku został zamapowany na rdzeni procesora logicznego. Jeśli piszesz aplikacje serwera, ten widok może pomóc w optymalizacji wydajności pamięci podręcznej przy użyciu przystawki Zarządzanie puli wątków koligacji lub wątku. Może również pomóc możesz sprawdzić przypadki, w którym korzystanie z koligacji wątku może mieć pogorszyła problem migracji między różnymi rdzeniami. Widok rdzeni ma dwie części, wykresu i legenda.  
  
 Na wykresie widać rdzenie logiczne na osi y i godziny na osi x. Każdy wątek na wykresie ma unikatowy kolor, więc możliwe jest śledzenie jego ruchu między rdzeniami wraz z upływem czasu. Wątki na tym wykresie można filtrować, wybierając je w obszarze legendy.  
  
 W obszarze legendy ma wpis dla każdego koloru na wykresie. Każdy wpis zawiera kolor wątku i nazwę, liczba przełączeń kontekstu między rdzeniami, całkowita liczba przełączeń kontekstu i procent przełączeń kontekstu przecinających rdzenie. Legendy są posortowane według liczby przełączeń kontekstu między rdzeniami, w kolejności malejącej. Wyświetla listę wątków, które wykonywane w czasie wyświetlane.  Lista jest aktualizowana, jeśli użytkownik przybliżanie/Oddalanie lub przesuwanie.  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzie CONCURRENCY Visualizer](../profiling/concurrency-visualizer.md)   
 [Widok wykorzystania](../profiling/utilization-view.md)   
 [Widok wątków](../profiling/threads-view-parallel-performance.md)



