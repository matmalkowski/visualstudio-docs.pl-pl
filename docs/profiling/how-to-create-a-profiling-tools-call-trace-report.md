---
title: 'Porady: Tworzenie raportu śledzenia wywołań narzędzi profilowania | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, viewing ETW data
- ETW [Visual Studio ALM], viewing data
ms.assetid: 7640520a-7d3c-456c-b184-872a5d2f82f3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 19c611644b7bfcc1995d1289742901325e02d975
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-create-a-profiling-tools-call-trace-report"></a>Porady: tworzenie raportu śledzenia wywołań narzędzi profilowania
*Raportu śledzenia wywołań* dla [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia profilowania Wyświetla informacje o chronometrażu dla każdego punktu wejścia i wyjścia funkcji aplikacji i każde wywołanie innych funkcji w funkcji. Wywołanie śledzenia raporty są dostępne dla danych profilowania tylko wtedy, gdy został zebrany przy użyciu metody instrumentacji.  
  
> [!NOTE]
>  Nie można wyświetlić raportów śledzenia wywołań w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Należy użyć **VSPerfReport** narzędzia wiersza polecenia, aby wygenerować plik wartości rozdzielanych przecinkami (.csv) lub plik Xml. Aby uzyskać więcej informacji o tym narzędziu, zobacz [VSPerfReport](../profiling/vsperfreport.md).  
  
### <a name="to-create-a-call-trace-report"></a>Aby utworzyć raportu śledzenia wywołań  
  
1.  Otwórz **wiersza polecenia**Połącz okna.  
  
2.  W wierszu polecenia wpisz następujące polecenie:  
  
     *ToolsPath* **VSPerfReport** *Plik_vsp* **/calltrace [XML]**  
  
    |||  
    |-|-|  
    |*ToolsPath*|Ścieżka narzędzi wiersza polecenia narzędzi profilowania. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*Plik_vsp*|Profilowania (Vsp lub vsps) pliku danych. Ścieżki pełne i częściowe są akceptowane.|  
    |Xml|Generuje raport w formacie Xml.|  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: zbieranie zdarzeń śledzenia dla danych systemu Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)   
 [Interfejsy API narzędzi profilowania](../profiling/profiling-tools-apis.md)