---
title: Zapoznanie z wartościami danych Kontencji zasobów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
ms.assetid: 071c0f0f-1eba-4dc8-ae87-0810e4086dd0
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 10c06805db7ef817421f7c9f85e316af8d4b5b35
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42679006"
---
# <a name="understanding-resource-contention-data-values"></a>Zapoznanie z wartościami danych kontencji zasobów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [wartościami danych Kontencji zasobów opis](https://docs.microsoft.com/visualstudio/profiling/understanding-resource-contention-data-values).  
  
Profilowanie rywalizacji zasobów zbiera szczegółowe informacje stosu wywołań każdorazowo że konkurencyjne wątki w aplikacji są zmuszone czekać na dostęp do zasobu udostępnionego.  
  
 **Wymagania**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
 Raporty rywalizacji zasobów zawierają całkowitą liczbę zdarzeń rywalizacji oraz całkowity czas spędzony zasobu dla modułów, funkcje, wiersze kodu źródłowego i instrukcji, w których oczekiwaniu.  
  
-   Alternatywne wartości wyświetlane całkowita liczba rywalizacji, których wymuszone funkcja oczekiwania przez rywalizacje o zasoby i łączny czas oczekiwania funkcji.  Rywalizacji, które były spowodowane przez funkcje podrzędne, które zostały wywołane przez funkcję znajdują się w wartości włącznie.  
  
-   Wyłączne wartości są wyświetlane tylko liczbę rywalizacji, wymuszone funkcja oczekiwania i że zostały spowodowane przez kod w treści funkcji. Rywalizacji spowodowane przez funkcje podrzędne nie są uwzględniane. Własny czas funkcji obejmuje także czasy oczekiwania, które były spowodowane przez instrukcje w treści funkcji.  
  
 Widoki raportu rywalizacji zasobów również uwzględnić wykresy z osią czasu, które pokazują zdarzenia rywalizacji indywidualnych wraz z upływem czasu i Pokaż stosy wywołań, które tworzone określonego zdarzenia. Aby uzyskać więcej informacji, zobacz jeden z następujących tematów:  
  
-   [Widok szczegółów wątku](../profiling/thread-details-view-contention-data.md)  
  
-   [Widok szczegółów zasobów](../profiling/resource-details-view-contention-data.md)  
  
 Aby uzyskać więcej informacji na temat tryb drugiego profilowania współbieżności zobacz [Concurrency Visualizer](../profiling/concurrency-visualizer.md).



