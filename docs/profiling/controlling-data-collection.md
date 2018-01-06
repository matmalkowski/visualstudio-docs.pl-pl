---
title: Kontrolowanie zbierania danych | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- advanced tasks for profiling tools
- profiling tools, advanced tasks
ms.assetid: e713ad63-b948-46f3-8db9-59b30922ebe5
caps.latest.revision: "27"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8cbbbb2ce9002512eeba4e838edf0d4d960b38c8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="controlling-data-collection"></a>Kontrolowanie zbierania danych
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Narzędzia profilowania umożliwiają podczas profilowania danych zbieranych podczas sesji wydajności, a także określać funkcje, które są profilowaniu. W tej sekcji opisano sposób uruchomić i zatrzymać zbieranie danych z **Eksplorator wydajności** i **kontroli zbierania danych** systemu windows oraz sposób ograniczyć liczbę obiektów, dla których są zbierane dane profilowania.  
  
## <a name="common-tasks"></a>Typowe zadania  
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Rozpoczęcie i zatrzymanie profilowania:** można uruchomić do profilu aplikacji podczas uruchamiania aplikacji, lub można dołączanie profilera do procesu, który jest już uruchomiony. Kiedy aplikacja docelowa jest uruchomiona, można wstrzymywać i wznawiać zbierania danych. Zakończysz sesję profilowania przez zamknięcie aplikacji docelowej lub odłączanie profilera z uruchomiony proces.|-   [Porady: rozpoczęcia i zakończenia zbierania danych o wydajności](../profiling/how-to-start-and-end-performance-data-collection.md)<br />-   [Porady: dołączanie lub odłączanie narzędzi wydajności do uruchomionego procesu](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md)<br />-   [Porady: wstrzymywanie i wznowienie zbierania danych o wydajności](../profiling/how-to-pause-and-resume-performance-data-collection.md)|  
|**Skonfiguruj profilowanie, aby ograniczyć zebranych danych Instrumentacji:** można użyć właściwości konfiguracji sesji wydajności, aby ograniczyć dane, które są zbierane w profilowania działa, które używają metody instrumentacji. Można uwzględnić lub wykluczyć pliki dll określonych, obszary nazw, klasy i funkcje. Można również wykluczyć funkcje, które nie spełniają próg rozmiaru, który określisz.|-   [Porady: ograniczanie Instrumentacji do określonych bibliotek DLL](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)<br />-   [Porady: ograniczanie Instrumentacji do określonych funkcji](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [Porady: wykluczanie lub uwzględnianie krótkich funkcji z Instrumentacji](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)|  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Eksplorator wydajności](../profiling/performance-explorer.md)