---
title: Profilowanie i bezpieczeństwo systemu Windows Vista | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,security
- performance tools, security
ms.assetid: 842112fc-b886-4801-8cd7-a25b314b0393
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f64483ff7c296e8a428d845018ac9630419c037e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="profiling-and-windows-vista-security"></a>Profilowanie i bezpieczeństwo systemu Windows Vista
W zależności od [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)] ustawienia uprawnień dostępu użytkownika, które administrator komputera ma zostać udostępnione, użytkownik może mieć uprawnienia zabezpieczeń do profilu procesu na tym komputerze. Poniższe przykłady przedstawiają możliwe różnice między użytkowników:  
  
-   W przypadku niektórych użytkowników może uzyskać dostępu do profilowania funkcje zaawansowane, gdy administrator ustawił sterownik i uruchomienie usługi.  
  
-   Użytkownicy domeny może uzyskać dostępu do przykładowej tylko profilowania.  
  
-   W przypadku niektórych użytkowników może uniemożliwić dostęp do profilowania do innych użytkowników.  
  
 Aby uzyskać więcej informacji, zobacz Opcje administratora w [VSPerfCmd](../profiling/vsperfcmd.md).  
  
## <a name="cross-session-profiling"></a>Krzyżowego sesji profilowania  
 *Krzyżowego sesji profilowania* jest możliwość procesu, który jest uruchamiany w ramach sesji logowania innego profilu. Na przykład większość usługi uruchamiane w sesji 0, a użytkownicy nie mogą uruchamiać bezpośrednio w sesji 0. Za pomocą **dołączyć do procesu** przycisk na pasku narzędzi Eksplorator wydajności lub / dołączyć opcję VSPerfCmd — narzędzie wiersza polecenia, można profilu większość procesów w sesjach logowania innego.  
  
 Można wyświetlić listę procesów, które są dostępne przez ustawienie opcji profilowania między procesami. Te opcje są dostępne w **dołączyć do procesu** okna, który jest wyświetlany po kliknięciu **dołączyć do procesu**:  
  
-   **Pokaż procesy wszystkich użytkowników**  
  
     Gdy ta opcja nie jest zaznaczona, na liście zostaną wyświetlone tylko procesy, które należą do firmy przez bieżącego użytkownika. Gdy **Pokaż procesy wszystkich użytkowników** jest zaznaczona, na liście zostaną wyświetlone procesy wszystkich użytkowników.  
  
-   **Pokaż procesy we wszystkich sesjach**  
  
     Gdy ta opcja nie jest zaznaczona, zostanie wyświetlona lista procesów w bieżącej sesji. Gdy ta opcja jest zaznaczona, na liście zostaną wyświetlone procesy we wszystkich sesjach.  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie](../profiling/overviews-performance-tools.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Porady: dołączanie do procesu uruchomionego](http://msdn.microsoft.com/en-us/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4)