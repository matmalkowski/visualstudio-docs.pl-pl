---
title: 'Porady: Tworzenie raportu ETW narzędzi profilowania | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: bf5547b3-f6c7-4989-9d47-2fe4f1261444
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a49ab3f00eb74edb3be3f733b3c0d70f8613d862
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-create-a-profiling-tools-etw-report"></a>Porady: tworzenie raportu ETW narzędzi profilowania
Raport zdarzenia śledzenia dla systemu Windows (ETW) zawiera listę zdarzeń funkcji ETW, które są rejestrowane w sesji wydajności [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędziach profilowania. Dane funkcji ETW są gromadzone w pliku binarnego (ETL). Aby uzyskać więcej informacji na temat tego raportu, zobacz [raportu funkcji Śledzenie zdarzeń systemu Windows ()](../profiling/event-tracing-for-windows-etw-report.md).  
  
> [!NOTE]
>  Nie można wyświetlić raporty ETW w interfejsie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Informacje dotyczące zbierania danych zdarzeń systemu Windows przy użyciu interfejsu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], zobacz [porady: zbieranie zdarzeń śledzenia dla systemu Windows (ETW) danych](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).  
  
-   Aby dowiedzieć się, jak zbierać dane funkcji ETW z wiersza polecenia, zobacz [VSPerfCmd](../profiling/vsperfcmd.md) i [zdarzenia](../profiling/events-vsperfcmd.md).  
  
 Generowanie raportu ETW za pomocą **VSReport / Podsumowanie: etw** polecenia. Etl, który zawiera dane funkcji ETW muszą być w tym samym katalogu co plik danych profilowania (Vsp lub vsps). Domyślnie raport jest generowany w formacie wartości rozdzielanych przecinkami (CSV). Aby uzyskać więcej informacji, zobacz [VSPerfReport](../profiling/vsperfreport.md).  
  
### <a name="to-generate-an-etw-report"></a>Do wygenerowania raportu ETW  
  
-   W **wiersza polecenia** okna, wpisz następujące polecenie w wierszu:  
  
     *ToolsPath* **VSPerfReport** *Plik_vsp* **/Summary: ETW [XML]**  
  
    |||  
    |-|-|  
    |*ToolsPath*|Ścieżka narzędzia narzędziach profilowania. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*Plik_vsp*|Profilowania (Vsp lub vsps) pliku danych. Ścieżki pełne i częściowe są akceptowane.|  
    |Xml|Generuje raport, który jest sformatowany w kodzie XML.|