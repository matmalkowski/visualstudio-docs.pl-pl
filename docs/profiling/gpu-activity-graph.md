---
title: "Wykres aktywności GPU | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.cv.cpu.graph.gpu
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 964846b5a2cc06eaf03fa695e4f1c0aeb9efdca4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="gpu-activity-graph"></a>Wykres aktywności GPU
Wykres aktywności GPU w Concurrency Visualizer Wyświetla poziom aktywności DirectX w systemie mierzony liczbę aparatów DirectX, które są używane wraz z upływem czasu.  Wykres nie pokazuje, które określonych aparaty były używane.  Aparat jest uznawany za będzie używana w przypadku przetwarzania pracę procesora GPU.  
  
## <a name="gpu-activity-graph-colors"></a>Kolory wykres aktywności GPU  
 Zielony oznacza użycie aparatów DirectX przez bieżący proces.  
  
 Szary światła wskazuje zużycie aparatów DirectX przez inne procesy w systemie. Aby zmniejszyć zużycie aparatów DirectX przez inne procesy, Zmniejsz liczbę innych procesów uruchomionych w systemie.  
  
 Białe wskazuje dostępność nieużywane aparaty DirectX w systemie. Te aparaty są dostępne dla procesu, jeśli można znaleźć więcej możliwości i wykorzystać je. Niektóre aparaty można używać tylko dla różnych rodzajów zadań.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wykorzystania](../profiling/utilization-view.md)