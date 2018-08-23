---
title: 'Porady: dołączanie i odłączanie narzędzi wydajności do uruchomionego procesu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.attach
helpviewer_keywords:
- performance tools, attach process
- profiling tools, detach process
- profiling tools, attach process
- performance tools, detach process
- profiler
ms.assetid: 56a99c39-e7f6-4f48-ae56-04ab8e022bf7
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 373e697826540a3636d8cb6295119f7405c95c53
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42688738"
---
# <a name="how-to-attach-and-detach-performance-tools-to-running-processes"></a>Porady: dołączanie i odłączanie narzędzi wydajności do uruchomionego procesu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [jak: Dołącz i Odłącz wydajności narzędzi do uruchamiania procesów](https://docs.microsoft.com/visualstudio/profiling/how-to-attach-and-detach-performance-tools-to-running-processes).  
  
Program profilujący może służyć do dołączenia do lub odłączyć od uruchomionego procesu, aby ułatwić pobierania próbek i zbieranie danych wydajności. Ta metoda umożliwia profilować proces w przypadku, gdy chcesz uniknąć zbierania danych o czas ładowania aplikacji lub do monitorowania wydajności procesu po nim osiągnie określony stan.  
  
> [!NOTE]
>  Poniższe kroki dotyczą Dołączanie i odłączanie procesów z poziomu [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] zintegrowane environmnent programowania (IDE). Aby uzyskać informacje o tym, jak używać narzędzi wiersza polecenia, zobacz [profilowania z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md). Aby uzyskać informacji dotyczących usług profilu, zobacz [usług profilowania](../profiling/command-line-profiling-of-services.md).  
  
 Procesy, które są dostępne dla profilu zależą od uprawnień dostępu użytkowników, które są ustawiane przez administratora komputera. Konto użytkownika może na przykład mają uprawnienie do żadnego z następujących czynności:  
  
-   Zaawansowane funkcje, profilowania, gdy administrator ustawił sterownik i uruchomienie usługi.  
  
-   Przykład profilowanie tylko (użytkowników domeny).  
  
-   Odmowa dostępu do profilowania, aby wszyscy.  
  
 Aby uzyskać więcej informacji, zobacz [profilowania i Windows Vista zabezpieczeń](../profiling/profiling-and-windows-vista-security.md) i opcje administratora w [VSPerfCmd](../profiling/vsperfcmd.md).  
  
### <a name="to-attach-to-a-running-process"></a>Aby dołączyć do uruchomionego procesu  
  
1.  Na **analizy** menu wskaż **Profiler** a następnie kliknij przycisk **Attach/Detach**.  
  
     \- lub —  
  
     W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij **Attach/Detach**.  
  
     **Dołączyć Profiler do procesu** pojawi się okno dialogowe.  
  
2.  Kliknij nazwę, którą chcesz dołączyć do procesu.  
  
3.  Kliknij przycisk **dołączyć**.  
  
### <a name="to-detach-from-a-running-process"></a>Można odłączyć od uruchomionego procesu  
  
1.  Na **analizy** menu wskaż **Profiler** a następnie kliknij przycisk **Attach/Detach**.  
  
     \- lub —  
  
     W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij **Attach/Detach**.  
  
     **Dołączyć Profiler do procesu** pojawi się okno dialogowe.  
  
2.  Kliknij nazwę obrazu, z którego chcesz odłączyć.  
  
3.  Kliknij przycisk **odłączyć**.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolowanie zbierania danych](../profiling/controlling-data-collection.md)   
 [Sesja wydajności — omówienie](../profiling/performance-session-overview.md)   
 [Porady: rozpoczęcia i zakończenia zbierania danych o wydajności](../profiling/how-to-start-and-end-performance-data-collection.md)   
 [Profilowanie i bezpieczeństwo programu Windows Vista](../profiling/profiling-and-windows-vista-security.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)



