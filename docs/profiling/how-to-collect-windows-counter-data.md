---
title: 'Porady: zbieranie danych licznika Windows | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.syscounter
- vs.performance.property.wincounter
helpviewer_keywords:
- windows counters
- performance tools, using windows counters
- profiling tools, using windows counters
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4ea074024e605d2dcc91500fb00fe0d7b6781692
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "35677244"
---
# <a name="how-to-collect-windows-counter-data"></a>Porady: zbieranie danych licznika Windows

Liczniki Windows są liczniki wydajności systemu, które mogą być zbierane podczas profilowania w ustalonych odstępach czasu. W widoku znaczniki raportu narzędzi profilowania z wiersza jest oznaczona etykietą **AutoMark** dla każdego interwału zbierania. Wiersz zawiera kolumny, które opisują wartości licznika wydajności, w tym odstępach czasu. Aby ograniczyć analizę do okresu czasu między dwoma określonymi znacznikami, zaznacz znaki, kliknij prawym przyciskiem myszy, a następnie wybierz **Filtruj wg** > **znaczniki** z menu skrótów.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagają znaczących zmian w taki sposób, programu Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows również wymagają nowych technik zbierania. Zobacz [narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="to-collect-windows-counter-data"></a>Aby zebrać dane Windows

1. W Eksploratorze wydajności, kliknij prawym przyciskiem myszy sesję, dla której chcesz skonfigurować liczniki Windows, a następnie wybierz pozycję **właściwości**.

2. W **stron właściwości**, kliknij przycisk **liczniki Windows**.

3. Wybierz **zbierania liczników Windows** pole wyboru.

4. W **interwał zbierania (MS)** tekstu wpisz przedział czasu.

5. Wybierz kategorię z **kategorii licznika** listy rozwijanej.

6. Wybierz domyślne wystąpienie z **wystąpienia** listy rozwijanej.

7. Wybierz liczniki, które chcesz użyć podczas profilowania aplikacji.

8. Kliknij przycisk **zastosowania.**

## <a name="see-also"></a>Zobacz także

[Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)  
[Właściwości sesji wydajności](../profiling/performance-session-properties.md)  
[Liczniki procesora CPU i systemu Windows](../profiling/cpu-and-windows-counters.md)