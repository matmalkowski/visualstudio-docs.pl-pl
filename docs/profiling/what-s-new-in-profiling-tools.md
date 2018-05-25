---
title: What's New in profilowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling
- what's new
ms.assetid: d4736cc8-8961-4089-be9e-d5190ce8353c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e53e9a29acf5258f3b225cde8211c4022b165bd7
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2018
---
# <a name="whats-new-in-profiling-tools-in-includevsdev15miscincludesvsdev15mdmd"></a>Nowości w narzędziach profilowania w [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]
Narzędzia diagnostyki obejmują nowe wizualizacje pomoże zidentyfikować problemy w swojej aplikacji, które wymagają ustalania. Narzędzia diagnostyki teraz obejmuje obsługę aplikacji programu ASP.NET.

Aby uzyskać dodatkowe informacje, zobacz [informacje o wersji [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] ](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes#debuggingdiag).

A **Podsumowanie** kartę został dodany do narzędzia, które pozwala skupić się na kluczowe dla analizy wydajności. Na tej karcie pokazuje, ile zdarzenia wystąpiły, można wykonać migawki sterty i pozwala szybko włączyć zbierania danych użycia procesora CPU. Ten widok przedstawia żadnego [usługi Application insights](https://azure.microsoft.com/en-us/documentation/articles/app-insights-visual-studio/) lub [interfejsu użytkownika analizy](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes#UIAnalysis) zdarzenia. Ponadto dla programu Visual Studio Enterprise, w tym widoku również wyświetlane zdarzenia funkcji IntelliTrace.

![Karta podsumowania narzędzi diagnostycznych](../profiling/media/DiagToolsSummaryTab-2.png "DiagToolsSummaryTab")

Narzędzie użycia procesora CPU ma [nowe](../profiling/Beginners-Guide-to-Performance-Profiling.md) pomoże zidentyfikować funkcje, które najprawdopodobniej będzie powodować problemy z wydajnością. Nowy **wywołujący/wywoływany** widoku umożliwia sprawdzenie kosztów wywołania funkcji do i z wybranej funkcji.

![Widok wywoływany obiekt wywołujący narzędzi diagnostycznych](../profiling/media/DiagToolsCallerCallee.png "DiagToolsCallerCallee")
  
## <a name="see-also"></a>Zobacz także  
 [Profil w programie Visual Studio](../profiling/index.md)  
 [Profil funkcji samouczka](../profiling/profiling-feature-tour.md)