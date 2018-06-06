---
title: 'Porady: zbieranie danych licznika Procesora | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.cpucounters
helpviewer_keywords:
- profiling tools, using portable CPU counters
- performance tools, portable CPU counters
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ee77d340eec13c42588511575c6047b5c8f28d16
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34765102"
---
# <a name="how-to-collect-cpu-counter-data"></a>Porady: zbieranie danych licznika Procesora

Licznik zdarzeń Procesora służy do zbierania danych wydajności dotyczących sprzętu. W tym artykule przedstawiono sposób zbieranie danych licznika zdarzeń, gdy używasz metoda profilowania instrumentacji.

Występują dwa typy zdarzeń licznika Procesora:

- Przenośne zdarzeń — zdarzenia Procesora, które mogą zostać pobrane niezależnie od określonego procesora CPU.

- Platforma zdarzeń — zdarzenia Procesora, które są powiązane do określonego procesora CPU.

 Przenośne zdarzenia zawierają ogólne zdarzenia, takie jak instrukcje wycofane i nie został zatrzymany cykle, Procesora buforu zdarzeń rozgałęziania zdarzenia i zdarzenia pamięci podręcznej L2. Liczniki zdarzeń dostępną platformę zależą od producenta procesora.

 Kategorie zdarzeń może być współużytkowana platforma i przenośne liczniki. Na przykład następujące kategorie danych są często wspólne dla obu typów:

- Zdarzenia pamięci.

- Zdarzenia frontonu.

- Zdarzenia gałęzi.

 Można zbierać dane liczników wydajności w profilera dwa sposoby:

- Zbieranie danych z jednego lub kilku liczników podczas profilu za pomocą Instrumentacji.

- Określ zdarzenia licznika jako interwał próbkowania, gdy profilu za pomocą próbkowania. Aby uzyskać więcej informacji, zobacz [porady: Wybieranie zdarzeń pobierania próbek](../profiling/how-to-choose-sampling-events.md).

## <a name="to-collect-cpu-performance-counter-data-when-you-profile-by-instrumentation"></a>Do zbierania danych licznika wydajności procesora CPU, gdy profilu za pomocą Instrumentacji

1. W tej sesji wydajności **strony właściwości**, kliknij przycisk **liczniki CPU.**

2. Wybierz **zbieranie liczniki CPU** pole wyboru.

3. Rozwiń węzeł **dostępnych liczników wydajności** drzewa do momentu znalezienia zdarzenia próbkowania, które mają być zbierane.

4. Dla każdego zdarzenia, które chcesz zebrać, wybierz zdarzenie, a następnie kliknij strzałkę w prawo, aby dodać zdarzenie do **wybrane liczniki** listy.

    > [!NOTE]
    > **Dostępnych liczników wydajności** jest włączone, tylko jeśli wybierzesz **liczniki CPU zbieranie** pole wyboru.

## <a name="see-also"></a>Zobacz także

[Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)  
[Właściwości sesji wydajności](../profiling/performance-session-properties.md)  
[Liczniki procesora CPU i systemu Windows](../profiling/cpu-and-windows-counters.md)  
[Instrukcje: wybieranie zdarzeń próbkowania](../profiling/how-to-choose-sampling-events.md)