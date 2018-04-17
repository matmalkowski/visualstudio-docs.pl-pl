---
title: 'Porady: zbieranie danych liczników systemu Windows | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
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
ms.openlocfilehash: b7f0d4c329ba2b33e6b1b564143c103b5090ad9a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-collect-windows-counter-data"></a>Porady: zbieranie danych liczników systemu Windows

Liczniki systemu Windows to liczniki wydajności systemu, które mogą być zbierane w ustalonych odstępach czasu podczas profilowania. W widoku raportu narzędzi profilowania znaki, jest oznaczony wiersz **AutoMark** dla każdego interwału zbierania. Wiersz zawiera kolumny, które opisano w tym interwał wartości licznika wydajności. Aby ograniczyć analizę do okresu czasu między dwoma określonymi znacznikami, wybierz znaczniki, kliknij prawym przyciskiem myszy, a następnie wybierz **filtru przez** ->  **znaczniki** z menu skrótów.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagane znaczących zmian w sposobie profilera Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowe techniki kolekcji. Zobacz [narzędzi wydajności w przypadku aplikacji systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="to-collect-windows-counter-data"></a>Aby zebrać dane z systemem Windows

1. W Eksploratorze wydajności, kliknij prawym przyciskiem myszy sesji, dla której chcesz skonfigurować liczniki systemu Windows i wybierz **właściwości**.

2. W **strony właściwości**, kliknij przycisk **liczników systemu Windows**.

3. Wybierz **zbierania liczników systemu Windows** pole wyboru.

4. W **interwał zbierania (MS)** tekstu wpisz przedział czasu.

5. Wybierz kategorię z **kategorii licznika** listy rozwijanej.

6. Wybierz wystąpienie z **wystąpienia** listy rozwijanej.

7. Wybierz liczniki, które ma być używany, gdy w profilu aplikacji.

8. Kliknij przycisk **zastosowania.**

## <a name="see-also"></a>Zobacz także

[Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)  
[Właściwości sesji wydajności](../profiling/performance-session-properties.md)  
[Procesor CPU i liczniki systemu Windows](../profiling/cpu-and-windows-counters.md)