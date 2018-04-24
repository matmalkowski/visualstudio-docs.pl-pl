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
ms.openlocfilehash: f29251a7b8f5e38e5b74a6aabd17ae0ccfec7651
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
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
  
 [Visual C++ Blog: Pamięci profilowania w programie Visual C++ 2015](https://blogs.msdn.microsoft.com/vcblog/2015/10/21/memory-profiling-in-visual-c-2015/)  

## <a name="see-also"></a>Zobacz też
 [Profilowanie w programie Visual Studio](../profiling/index.md)  
 [Przegląd funkcji profilowania](../profiling/profiling-feature-tour.md)