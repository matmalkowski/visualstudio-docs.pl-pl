---
title: What's New in profilowania | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- profiling
- what's new
ms.assetid: d4736cc8-8961-4089-be9e-d5190ce8353c
caps.latest.revision: "42"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8529bc4cc9708ea58a0480d61327c50c96c996fc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="whats-new-in-profiling-tools-in-includevsdev15miscincludesvsdev15mdmd"></a>Nowości w narzędziach profilowania w[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]
Narzędzia diagnostyki obejmują nowe wizualizacje pomoże zidentyfikować problemy w swojej aplikacji, które wymagają ustalania. Narzędzia diagnostyki teraz obejmuje obsługę aplikacji programu ASP.NET.

Aby uzyskać dodatkowe informacje, zobacz [informacje o wersji dla [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] ](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes#debuggingdiag).

A **Podsumowanie** kartę został dodany do narzędzia, które pozwala skupić się na kluczowe dla analizy wydajności. Na tej karcie pokazuje, ile zdarzenia wystąpiły, można wykonać migawki sterty i pozwala szybko włączyć zbierania danych użycia procesora CPU. Ten widok przedstawia żadnego [usługi Application Insights](https://azure.microsoft.com/en-us/documentation/articles/app-insights-visual-studio/) lub [interfejsu użytkownika analizy](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes#UIAnalysis) zdarzenia. Ponadto dla programu Visual Studio Enterprise, w tym widoku również wyświetlane zdarzenia funkcji IntelliTrace.

![Karta Podsumowanie narzędzi diagnostycznych](../profiling/media/DiagToolsSummaryTab-2.png "DiagToolsSummaryTab")

Narzędzie użycia procesora CPU ma [nowe](../profiling/Beginners-Guide-to-Performance-Profiling.md) pomoże zidentyfikować funkcje, które najprawdopodobniej będzie powodować problemy z wydajnością. Nowy **wywołujący/wywoływany** widoku umożliwia sprawdzenie kosztów wywołania funkcji do i z wybranej funkcji.

![Widok wywoływany obiekt wywołujący narzędzi diagnostycznych](../profiling/media/DiagToolsCallerCallee.png "DiagToolsCallerCallee")
  
## <a name="see-also"></a>Zobacz też  
 [Profilowanie w programie Visual Studio](../profiling/index.md)  
 [Przegląd funkcji profilowania](../profiling/profiling-feature-tour.md)