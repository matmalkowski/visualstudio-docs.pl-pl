---
title: Widok drzewa wywołań | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.calltree
helpviewer_keywords:
- Call Tree view
- profiling tools reports, Call Tree view
- performance reports, Call Tree view
- profiling tools, Call Tree view
ms.assetid: b2dbc033-bf95-4d10-8e51-f9462979133e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f8973f1536ded24d2fd327aa3eac1ceee795cb54
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34262450"
---
# <a name="call-tree-view"></a>Widok drzewa wywołań
Widok drzewa wywołań Wyświetla ścieżek wykonywania funkcji, które zostały przechodzić w profilowanych aplikacji. Korzeń drzewa jest punktem wejścia do aplikacji lub składnika. Każdy węzeł funkcja zawiera listę wszystkich funkcji mu i dane wydajności dotyczące tych wywołań funkcji.  
  
 Widok drzewa wywołań można rozwinąć i wyróżnij ścieżkę wykonywania funkcji wykorzystany najwięcej czasu lub zostało pobrane najczęściej. Aby wyświetlić wydajność najdroższych ścieżki, kliknij prawym przyciskiem myszy funkcji, a następnie kliknij przycisk **rozwiń aktywnej ścieżki**.  
  
 Każdy proces w przebiegu profilowania jest wyświetlana jako węzła głównego. Można ustawić węzeł początkowy widok drzewa wywołań prawym przyciskiem myszy węzeł, aby ustawić jako węzeł początkowy, a następnie wybierając **ustawić głównego**.  
  
 Po ustawieniu węzła głównego pozwala wyeliminować wszystkie wpisy z widoku, z wyjątkiem poddrzewo wybranego węzła. Do węzła przeglądana można zresetować węzła głównego. W oknie, widok drzewa wywołań, kliknij prawym przyciskiem myszy, a następnie wybierz **zresetować głównego**.  
  
 Widok drzewa wywołań można dostosować, aby dodać lub usunąć kolumny. Kliknij prawym przyciskiem myszy **paska tytułu nazwy kolumny**, a następnie wybierz **Dodaj/Usuń kolumny**.  
  
 Widok drzewa wywołań można skonfigurować dla redukcji szumu poprzez ograniczenie ilości danych, które są prezentowane. Za pomocą redukcji szumu, problemy z wydajnością jest większa w widoku. Jeśli problemy z wydajnością są łatwe rozróżnienie, analiza jest łatwiejsze. Aby uzyskać więcej informacji, zobacz [porady: Konfigurowanie redukcji szumu w widoku raportu](../profiling/how-to-configure-noise-reduction-in-report-views.md).  
  
> [!NOTE]
>  Jeśli skonfigurowano redukcji szumu wyświetlić ostrzeżenie, jeśli jest włączone, pasek informacyjny będą wyświetlane w raporcie.  
  
 Aby uzyskać więcej informacji o definicjach kolumn w widoku drzewa wywołań zobacz następujące tematy:  
  
 [Widok drzewa wywołań](../profiling/call-tree-view-sampling-data.md)  
  
 [Widok drzewa wywołań](../profiling/call-tree-view-instrumentation-data.md)  
  
 [Drzewie wywołań view - próbkowanie](../profiling/call-tree-view-dotnet-memory-sampling-data.md)  
  
 [Widok drzewa wywołań](../profiling/call-tree-view-contention-data.md)  
  
## <a name="see-also"></a>Zobacz także  
 [Widoki raportu wydajności](../profiling/performance-report-views.md)   
 [Zapoznanie z wartościami danych Instrumentacji](../profiling/understanding-instrumentation-data-values.md)   
 [Zapoznanie z wartościami danych próbkowania](../profiling/understanding-sampling-data-values.md)