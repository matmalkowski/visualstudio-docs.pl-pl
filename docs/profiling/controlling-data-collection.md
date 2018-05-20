---
title: Kontrolowanie zbierania danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- advanced tasks for profiling tools
- profiling tools, advanced tasks
ms.assetid: e713ad63-b948-46f3-8db9-59b30922ebe5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: deafe488fdb44216f0a6750f532c2e0d2363b453
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="control-data-collection"></a>Kontrola zbierania danych
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Narzędzia profilowania umożliwiają podczas profilowania danych zbieranych podczas sesji wydajności, a także określać funkcje, które są profilowaniu. W tej sekcji opisano sposób uruchomić i zatrzymać zbieranie danych z **Eksplorator wydajności** i **kontroli zbierania danych** systemu windows oraz sposób ograniczyć liczbę obiektów, dla których są zbierane dane profilowania.  
  
## <a name="common-tasks"></a>Wspólne zadania
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Rozpoczęcie i zatrzymanie profilowania:** można uruchomić do profilu aplikacji podczas uruchamiania aplikacji, lub można dołączanie profilera do procesu, który jest już uruchomiony. Kiedy aplikacja docelowa jest uruchomiona, można wstrzymywać i wznawiać zbierania danych. Zakończysz sesję profilowania przez zamknięcie aplikacji docelowej lub odłączanie profilera z uruchomiony proces.|-   [Porady: rozpoczęcia i zakończenia zbierania danych o wydajności](../profiling/how-to-start-and-end-performance-data-collection.md)<br />-   [Porady: dołączanie lub odłączanie narzędzi wydajności do uruchomionego procesu](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md)<br />-   [Porady: wstrzymywanie i wznawianie zbierania danych o wydajności](../profiling/how-to-pause-and-resume-performance-data-collection.md)|  
|**Skonfiguruj profilowanie, aby ograniczyć zebranych danych Instrumentacji:** można użyć właściwości konfiguracji sesji wydajności, aby ograniczyć dane, które są zbierane w profilowania działa, które używają metody instrumentacji. Można uwzględnić lub wykluczyć pliki dll określonych, obszary nazw, klasy i funkcje. Można również wykluczyć funkcje, które nie spełniają próg rozmiaru, który określisz.|-   [Porady: ograniczanie Instrumentacji do określonych bibliotek DLL](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)<br />-   [Porady: ograniczanie Instrumentacji do określonych funkcji](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [Porady: wykluczanie lub uwzględnianie krótkich funkcji z Instrumentacji](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)|  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)  
  
## <a name="see-also"></a>Zobacz także  
 [Eksplorator wydajności](../profiling/performance-explorer.md)