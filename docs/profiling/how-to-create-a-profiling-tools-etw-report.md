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
ms.openlocfilehash: 4b086e726f45010d2d71395d0c6119625180add3
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815301"
---
# <a name="how-to-create-a-profiling-tools-etw-report"></a>Porady: Tworzenie raportu ETW narzędzi profilowania
Raport zdarzenia śledzenia dla systemu Windows (ETW) zawiera listę zdarzeń funkcji ETW, które są rejestrowane w sesji wydajności [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędziach profilowania. Dane funkcji ETW są gromadzone w pliku binarnym (. *etl*) pliku. Aby uzyskać więcej informacji na temat tego raportu, zobacz [raportu funkcji Śledzenie zdarzeń systemu Windows ()](../profiling/event-tracing-for-windows-etw-report.md).  
  
> [!NOTE]
>  Nie można wyświetlić raporty ETW w interfejsie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Informacje dotyczące zbierania danych zdarzeń systemu Windows przy użyciu interfejsu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], zobacz [porady: zbieranie zdarzeń śledzenia dla systemu Windows (ETW) danych](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).  
  
-   Aby dowiedzieć się, jak zbierać dane funkcji ETW z wiersza polecenia, zobacz [VSPerfCmd](../profiling/vsperfcmd.md) i [zdarzenia](../profiling/events-vsperfcmd.md).  
  
 Generowanie raportu ETW za pomocą **VSReport / Podsumowanie: etw** polecenia. . *etl* zawierający funkcji ETW dane muszą być w tym samym katalogu co dane profilowania (. *Vsp* lub. *vsps*) pliku. Domyślnie raport jest generowany jako wartość rozdzielaną przecinkami (. *CSV*) pliku. Aby uzyskać więcej informacji, zobacz [VSPerfReport](../profiling/vsperfreport.md).  
  
### <a name="to-generate-an-etw-report"></a>Do wygenerowania raportu ETW  
  
-   W **wiersza polecenia** okna, wpisz następujące polecenie w wierszu:  
  
     *ToolsPath* **VSPerfReport** *Plik_vsp*  **/Summary: ETW [XML]**  
  
    |||  
    |-|-|  
    |*ToolsPath*|Ścieżka narzędzia narzędziach profilowania. Aby uzyskać więcej informacji, zobacz [Określ ścieżkę do narzędzia wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*Plik_vsp*|Dane profilowania (. *Vsp* lub. *vsps*) pliku. Ścieżki pełne i częściowe są akceptowane.|  
    |Xml|Generuje raport, który jest sformatowany w kodzie XML.|
