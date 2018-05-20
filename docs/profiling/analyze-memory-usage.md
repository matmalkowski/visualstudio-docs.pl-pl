---
title: Analizowanie użycia pamięci w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/02/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 20c483b40cf1cc45b730ea67bf01ea452c42af1e
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="analyze-memory-usage"></a>Analizowanie użycia pamięci
Użyj zintegrowanych debugera **użycie pamięci** narzędzia diagnostycznego, aby znaleźć przecieki pamięci i użycie pamięci nieefektywne. Narzędzie umożliwia wykorzystanie pamięci, należy wykonać co najmniej jeden *migawki* sterty pamięci zarządzanego i natywnego. Można zbierać migawki .NET, Tryb natywny lub mieszane (.NET i natywnego) aplikacji.  
  
-   Można analizować jedna migawka, aby zrozumieć względną wpływ typów obiektów na wykorzystanie pamięci i znaleźć kodu w aplikacji używającej Niewydajne pamięci.  
  
-   Można także porównać (diff) dwiema migawkami aplikacji można znaleźć w kodzie obszarów powodujących wykorzystanie pamięci zwiększyć wraz z upływem czasu.  

Aby uzyskać szczegółowe instrukcje, zobacz [Analizowanie użycia pamięci](../profiling/memory-usage.md) samouczka. Aby Analiza użycia pamięci bez dołączanie debugera, zobacz [użycia pamięci bez debuger](memory-usage-without-debugging2.md).
  
## <a name="blogs-and-videos"></a>Blogi i filmy wideo  

|         |         |
|---------|---------|
|  ![Ikona aparatu film wideo](../install/media/video-icon.png "obejrzeć film wideo")  |    [Obejrzyj film](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Profiling-with-Diagnostics-Tools-in-Visual-Studio-2017-daHnzMD6D_9211787171) przy użyciu narzędzia diagnostyczne, które pokazuje, jak Analiza użycia pamięci i procesora w Visual Studio 2017 r. |

 [Analizowanie Procesora i pamięci podczas debugowania](https://blogs.msdn.microsoft.com/visualstudio/2016/02/15/analyze-cpu-memory-while-debugging/)  
  
 [Visual C++ blogu: profilowanie pamięci w programie Visual C++ 2015](https://blogs.msdn.microsoft.com/vcblog/2015/10/21/memory-profiling-in-visual-c-2015/)  

## <a name="see-also"></a>Zobacz także
 [Profilowanie w programie Visual Studio](../profiling/index.md)  
 [Przewodnik po funkcjach profilowania](../profiling/profiling-feature-tour.md)