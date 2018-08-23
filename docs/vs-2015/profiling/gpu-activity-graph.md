---
title: Wykres aktywności GPU | Dokumentacja firmy Microsoft
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
- vs.cv.cpu.graph.gpu
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d5a0ef828b221219c3abae0e46ec40d21b6b045c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42684712"
---
# <a name="gpu-activity-graph"></a>Wykres aktywności GPU
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [wykres aktywności GPU](https://docs.microsoft.com/visualstudio/profiling/gpu-activity-graph).  
  
Wykres aktywności procesora GPU w Wizualizatorze współbieżności przedstawia poziomu aktywności DirectX w systemie, gdyż jest mierzone przez liczbę aparatów DirectX, które są używane wraz z upływem czasu.  Wykres nie pokazuje, które określonych aparatów były używane.  Aparat uznaje się będzie używana, jeśli przetwarza wszystkie działanie procesora GPU.  
  
## <a name="gpu-activity-graph-colors"></a>Kolory wykres aktywności procesora GPU  
 Zielony oznacza zużycia silników DirectX w bieżącym procesie.  
  
 Jasny zwykle wskazuje zużycia silników DirectX przez inne procesy w systemie. Aby zmniejszyć zużycia silników DirectX przez inne procesy, Zmniejsz liczbę innych procesów uruchomionych w systemie.  
  
 Oficjalny wskazuje dostępność nieużywane aparatów DirectX w systemie. Silników są dostępne dla procesu, jeśli możesz znaleźć dodatkowe możliwości w celu ich wykorzystania. Niektóre aparaty należy używać tylko dla określonych typów zadań.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wykorzystania](../profiling/utilization-view.md)



