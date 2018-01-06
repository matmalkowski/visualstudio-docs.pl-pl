---
title: "Grafika interfejsu API i statystyki pamięci | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 03/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.graphics.apistatistics
- vs.graphics.memorystatistics
ms.assetid: 27d2f303-e3ed-4219-9009-345a0d849506
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c34c505751153410896da66040c866676c3a7ee2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="graphics-api-and-memory-statistics"></a>Grafika interfejsu API i statystyki pamięci
<!-- VERSIONLESS -->
Visual Studio 2017 oraz lepsze wsparcie statystyki interfejsu API grafiki i narzędzia statystyki pamięci.  Tych dwóch narzędzi umożliwiają wyświetlanie różnych bitów danych na użycia interfejsu API programu Direct3D, a także zużycie pamięci procesora GPU z różnymi zasobami.

## <a name="graphics-api-statistics"></a>Statystyki interfejsu API grafiki
Statystyka interfejsu API grafiki w diagnostyki grafiki w programie Visual Studio umożliwia wyświetlenie wszystkich połączeń Direct3D, które zostały dokonane i liczba każdego wywołania.  Zaznacz, aby wyświetlić okno **Widok > Statystyki interfejsu API** elementu menu.

![Statystyki interfejsu API](media/gfx_diag_api_statistics.png)

To narzędzie może być przydatne w odnajdywaniu czy wprowadzania wywołań programu DirectX, że nie może zrealizować można lub wywołań tworzonego zbyt często.

Możesz kliknąć prawym przyciskiem myszy w oknie dane Kopiuj wszystko jako woluminu CSV, który można wkleić do ekran podobny do programu Excel w celu dalszej analizy.

## <a name="memory-statistics"></a>Statystyki pamięci
To narzędzie wyświetli, ile sterownik karty graficznej jest przydzielanie zasobów pamięci, możesz utworzyć w ramce.  Aby wyświetlić to okno, wybierz **Widok > Statystyki pamięci** elementu menu.

![Statystyki pamięci](media/gfx_diag_memory_statistics.png)

**Alokacji procesora GPU** kolumna wyświetlana jest ilość pamięci używanej przez zdarzenia wyświetlane w **zdarzeń** kolumny.  Możesz też wybrać ikona monitorowania ![ikona monitorowania](media/gfx_watch.png) Aby wyświetlić [historii zasobów](graphics-event-list.md#resource-history) dla wybranego zdarzenia.

Jak za pomocą narzędzia interfejsu API statystyki możesz kliknąć prawym przyciskiem myszy w oknie dane Kopiuj wszystko jako woluminu CSV, który można wkleić do ekran podobny do programu Excel w celu dalszej analizy.

## <a name="see-also"></a>Zobacz też  
[Diagnostyka grafiki (debugowania grafiki DirectX)](visual-studio-graphics-diagnostics.md)   
[Historia zasobów](graphics-event-list.md#resource-history)
<!-- /VERSIONLESS -->