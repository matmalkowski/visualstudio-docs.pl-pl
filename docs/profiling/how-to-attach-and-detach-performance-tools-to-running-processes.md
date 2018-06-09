---
title: 'Porady: dołączanie lub odłączanie narzędzi wydajności do uruchomionego procesu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.attach
helpviewer_keywords:
- performance tools, attach process
- profiling tools, detach process
- profiling tools, attach process
- performance tools, detach process
- profiler
ms.assetid: 56a99c39-e7f6-4f48-ae56-04ab8e022bf7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ea9b35192eb2584f92856e5ab9c50eac22da85f7
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2018
ms.locfileid: "35237230"
---
# <a name="how-to-attach-and-detach-performance-tools-to-running-processes"></a>Porady: dołączanie lub odłączanie narzędzi wydajności do uruchomionego procesu
Profiler może służyć do dołączenia do lub odłączyć od uruchomionego procesu, aby ułatwić pobierania próbek i gromadzenia danych wydajności. Ta metoda służy do profilowania procesu, gdy chce się uniknąć zbierania danych dotyczących czasu ładowania aplikacji lub do monitorowania wydajności procesu po nim osiągnie określony stan.  
  
> [!NOTE]
>  Poniższe kroki dotyczą Dołączanie i odłączanie procesów z poziomu [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] zintegrowane environmnent rozwoju (IDE). Aby dowiedzieć się, jak używać narzędzi wiersza polecenia, zobacz [profilu z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md). Informacje o sposobie profilu usługi, zobacz [profilu usługi](../profiling/command-line-profiling-of-services.md).  
  
 Procesy, które są dostępne do profilu są zależne od uprawnień dostępu użytkowników, które są ustawione przez administratora komputera. Konto użytkownika na przykład uprawnień dla żadnej z następujących czynności:  
  
-   Zaawansowane profilowanie funkcji, gdy administrator ustawił sterownik i uruchomienie usługi.  
  
-   Przykład profilowania tylko (użytkownicy domeny).  
  
-   Odmowa dostępu do profilowania dla wszystkich.  
  
 Aby uzyskać więcej informacji, zobacz [zabezpieczeń profilowania i Windows Vista](../profiling/profiling-and-windows-vista-security.md) i opcje administratora w [VSPerfCmd](../profiling/vsperfcmd.md).  
  
### <a name="to-attach-to-a-running-process"></a>Aby dołączyć do uruchomionego procesu  
  
1.  Na **debugowania** menu wskaż **profilera**, następnie **Eksplorator wydajności**, a następnie kliknij przycisk **Attach**.    
  
     **Dołącz Profiler do procesu** zostanie wyświetlone okno dialogowe.  
  
2.  Kliknij nazwę procesu, który chcesz dołączyć do.  
  
3.  Kliknij przycisk **dołączyć**.  
  
### <a name="to-detach-from-a-running-process"></a>Można odłączyć od uruchomionego procesu  
  
1.  n **debugowania** menu wskaż **profilera**, następnie **Eksplorator wydajności**, a następnie kliknij przycisk **Detach**. 
  
     **Dołącz Profiler do procesu** zostanie wyświetlone okno dialogowe.  
  
2.  Kliknij nazwę obrazu, z którego chcesz odłączyć.  
  
3.  Kliknij przycisk **odłączyć**.  
  
## <a name="see-also"></a>Zobacz także  
 [Kontrola zbierania danych](../profiling/controlling-data-collection.md)   
 [Sesja wydajności — omówienie](../profiling/performance-session-overview.md)   
 [Porady: rozpoczęcia i zakończenia zbierania danych o wydajności](../profiling/how-to-start-and-end-performance-data-collection.md)   
 [Profilowanie i bezpieczeństwo systemu Windows Vista](../profiling/profiling-and-windows-vista-security.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)