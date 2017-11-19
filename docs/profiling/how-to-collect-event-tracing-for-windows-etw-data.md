---
title: "Porady: zbieranie zdarzeń śledzenia dla danych systemu Windows (ETW) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.performance.property.events
helpviewer_keywords:
- event trace providers, performance tools
- profiling tools, event trace providers
- performance tools, enabling event trace providers
ms.assetid: aa2261fe-d5f5-49fc-a171-d18842e1dc7d
caps.latest.revision: "26"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 66ad7c937ba6c3845e905abea31f4525198f8389
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2017
---
# <a name="how-to-collect-event-tracing-for-windows-etw-data"></a>Porady: zbieranie danych śledzenia zdarzeń dla systemu Windows (ETW)
Zdarzenia śledzenia dla systemu Windows (ETW) jest mechanizmem wydajne śledzenie poziomu jądra, umożliwiającą jądra dziennika profilera lub zdarzeń zdefiniowanych przez aplikację. Dane, które mają być zbierane z dostawcy zdarzeń można wyświetlać tylko przy użyciu /**Podsumowanie: ETW** opcji [VSPerfReport](../profiling/vsperfreport.md) narzędzia wiersza polecenia. Ten raport służy do określenia, gdzie występują problemy z wydajnością w aplikacji.  
  
 **Wymagania**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagane znaczących zmian w sposobie profilera Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowe techniki kolekcji. Zobacz [narzędzi wydajności w przypadku aplikacji systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
### <a name="to-enable-event-trace-providers"></a>Aby włączyć dostawcy śledzenia zdarzeń  
  
1.  W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij przycisk **właściwości**.  
  
2.  W **strony właściwości**, kliknij przycisk **zdarzeń systemu Windows** właściwości.  
  
3.  W **dostawcy śledzenia zdarzeń wybierz może zbierać dane z** wybierz dostawców zdarzeń, które chcesz użyć do profilu aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)