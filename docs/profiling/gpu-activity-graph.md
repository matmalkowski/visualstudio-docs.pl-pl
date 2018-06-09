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
ms.openlocfilehash: 9dcadfdbfa52815fdd6d88f78afb88d421e203c7
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2018
ms.locfileid: "35237913"
---
# <a name="gpu-activity-graph"></a>Wykres aktywności GPU
Wykres aktywności GPU w Concurrency Visualizer Wyświetla poziom aktywności DirectX w systemie mierzony liczbę aparatów DirectX, które są używane wraz z upływem czasu.  Wykres nie pokazuje, które określonych aparaty były używane.  Aparat jest uznawany za będzie używana w przypadku przetwarzania pracę procesora GPU.  
  
## <a name="gpu-activity-graph-colors"></a>Kolory wykres aktywności GPU  
 Zielony oznacza użycie aparatów DirectX przez bieżący proces.  
  
 Szary światła wskazuje zużycie aparatów DirectX przez inne procesy w systemie. Aby zmniejszyć zużycie aparatów DirectX przez inne procesy, Zmniejsz liczbę innych procesów uruchomionych w systemie.  
  
 Białe wskazuje dostępność nieużywane aparaty DirectX w systemie. Te aparaty są dostępne dla procesu, jeśli można znaleźć więcej możliwości i wykorzystać je. Niektóre aparaty można używać tylko dla różnych rodzajów zadań.  
  
## <a name="see-also"></a>Zobacz także  
 [Widok wykorzystania](../profiling/utilization-view.md)