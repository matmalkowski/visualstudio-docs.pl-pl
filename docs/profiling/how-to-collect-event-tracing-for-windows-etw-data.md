---
title: 'Porady: zbieranie zdarzeń śledzenia dla danych systemu Windows (ETW) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.events
helpviewer_keywords:
- event trace providers, performance tools
- profiling tools, event trace providers
- performance tools, enabling event trace providers
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cd8016b14d91157942ed8d5e4a987df0009f6af3
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766165"
---
# <a name="how-to-collect-event-tracing-for-windows-etw-data"></a>Porady: zbieranie danych funkcji Śledzenie zdarzeń systemu Windows ()

Zdarzenia śledzenia dla systemu Windows (ETW) jest mechanizmem wydajne śledzenie poziomu jądra, umożliwiającą jądra dziennika profilera lub zdarzeń zdefiniowanych przez aplikację. Dane, które mają być zbierane z dostawcy zdarzeń można wyświetlać tylko przy użyciu /**Podsumowanie: ETW** opcji [VSPerfReport](../profiling/vsperfreport.md) narzędzia wiersza polecenia. Ten raport służy do określenia, gdzie występują problemy z wydajnością w aplikacji.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagane znaczących zmian w sposobie profilera Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowe techniki kolekcji. Zobacz [narzędzi wydajności w przypadku aplikacji systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="to-enable-event-trace-providers"></a>Aby włączyć dostawcy śledzenia zdarzeń

1. W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij przycisk **właściwości**.

2. W **strony właściwości**, kliknij przycisk **zdarzeń systemu Windows** właściwości.

3. W **dostawcy śledzenia zdarzeń wybierz może zbierać dane z** wybierz dostawców zdarzeń, które chcesz użyć do profilu aplikacji.

## <a name="see-also"></a>Zobacz także

[Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)