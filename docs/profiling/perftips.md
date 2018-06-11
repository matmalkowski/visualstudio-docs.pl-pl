---
title: Wskazówek | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 509d2d4f-48a5-4cdf-acad-6f7b75421303
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 53366b300c94166116c0dc03b108991fc80af013
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35255135"
---
# <a name="perftips"></a>Wskazówek
Debuger programu Visual Studio *wskazówek* i zintegrowane debugera **narzędzia diagnostyczne** ułatwiają monitorowanie i analizowanie wydajności aplikacji, podczas debugowania.  
  
 Mimo że debugera, zintegrowane narzędzia diagnostyczne są dobrym sposobem staje się znane problemy z wydajnością, gdy tworzysz, debuger może mieć znaczący wpływ na wydajność aplikacji. Aby zbierać dokładne dane dotyczące wydajności, należy rozważyć użycie Visual Studio tools diagnostyki działających poza debugerem zbyt jako dodatkową część Twojej dochodzenia wydajności. Zobacz [uruchomienie narzędzia z lub bez debuger profilowania](../profiling/running-profiling-tools-with-or-without-the-debugger.md).  
  
## <a name="perftips"></a>Wskazówek  
 Po zatrzymaniu debugera wykonanie przerwania lub operację wykonywania krokowego czas, który upłynął między przerwy i poprzedniego punktu przerwania jest wyświetlany jako wskazówkę w oknie edytora. Aby uzyskać więcej informacji, zobacz [wskazówek: informacje o wydajności na ułatwia podczas debugowania w programie Visual Studio](http://blogs.msdn.com/b/visualstudioalm/archive/2014/08/18/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio.aspx).  
  
 ![Element PerfTip](../profiling/media/dbgdiag_perf_perftip.png "DBGDIAG_PERF_PerfTip")  
  
## <a name="diagnostics-tools-window"></a>Okno narzędzia diagnostyczne  
 Punkty przerwania i danych o chronometrażu skojarzone są rejestrowane w **narzędzia diagnostyczne** okna.  
  
 Poniżej przedstawiono graficzne **narzędzia diagnostyczne** okna w Visual Studio 2015 Update 1:  
  
 ![DiagnosticTools&#45;Update1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-Update1")  
  
-   **Podziel zdarzenia** osi czasu Oznacz punkty przerwania, które zostały trafień podczas sesji debugowania. Kliknij zdarzenie, aby go zaznaczyć **debugera** listy szczegóły.  
  
-   **Użycie procesora CPU** wykres przedstawia zmiany w użyciu procesora CPU na wszystkich rdzeni procesora w sesji debugowania.  
  
-   **Zdarzenia** lista **debugera** okienka szczegółów obejmują elementy, dla każdego zdarzenia podziału.  
  
-   **Czas trwania** kolumny zdarzeń podziału przedstawia czas, który upłynął między zdarzeniem i poprzedniego punktu przerwania.  
  
## <a name="turn-perftips-on-or-off"></a>Włącz wskazówek lub wyłącz  
 Aby włączyć lub wyłączyć wskazówek:  
  
1.  Na **debugowania** menu, wybierz **opcje**.  
  
2.  Zaznacz lub usuń zaznaczenie **Pokaż upłynął element PerfTip podczas debugowania**.  
  
## <a name="turn-the-diagnostic-tools-window-on-or-off"></a>Włącz okno narzędzia diagnostyczne lub wyłącz  
 Aby włączyć lub wyłączyć okno narzędzia diagnostyczne:  
  
1.  Na **debugowania** menu, wybierz **opcje**.  
  
2.  Zaznacz lub usuń zaznaczenie **Włącz narzędzia diagnostyczne podczas debugowania**.

## <a name="see-also"></a>Zobacz także
 [Profilowanie w programie Visual Studio](../profiling/index.md)  
 [Przewodnik po funkcjach profilowania](../profiling/profiling-feature-tour.md)
