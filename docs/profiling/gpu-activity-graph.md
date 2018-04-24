---
title: Wykres aktywności GPU | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph.gpu
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 41b7812db05b61c351346e5f0dcfa1bf4bd7bd1f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="gpu-activity-graph"></a>Wykres aktywności GPU
Wykres aktywności GPU w Concurrency Visualizer Wyświetla poziom aktywności DirectX w systemie mierzony liczbę aparatów DirectX, które są używane wraz z upływem czasu.  Wykres nie pokazuje, które określonych aparaty były używane.  Aparat jest uznawany za będzie używana w przypadku przetwarzania pracę procesora GPU.  
  
## <a name="gpu-activity-graph-colors"></a>Kolory wykres aktywności GPU  
 Zielony oznacza użycie aparatów DirectX przez bieżący proces.  
  
 Szary światła wskazuje zużycie aparatów DirectX przez inne procesy w systemie. Aby zmniejszyć zużycie aparatów DirectX przez inne procesy, Zmniejsz liczbę innych procesów uruchomionych w systemie.  
  
 Białe wskazuje dostępność nieużywane aparaty DirectX w systemie. Te aparaty są dostępne dla procesu, jeśli można znaleźć więcej możliwości i wykorzystać je. Niektóre aparaty można używać tylko dla różnych rodzajów zadań.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wykorzystania](../profiling/utilization-view.md)