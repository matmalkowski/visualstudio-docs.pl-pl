---
title: "Śledzenie zdarzeń systemu Windows (ETW) raportu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Event tracing for Windows profiling report
- ETW profiling report
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6ae3b43f300ce410f58dd3fc4d849b2fe1bb3c38
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="event-tracing-for-windows-etw-report"></a>Zdarzenia śledzenia dla systemu Windows (ETW) — Raport
Raport zdarzenia śledzenia dla systemu Windows (ETW) zawiera listę zdarzeń funkcji ETW, które zostały zarejestrowane w sesji wydajności [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędziach profilowania. Dane funkcji ETW są gromadzone w pliku binarnego (ETL).  
  
> [!NOTE]
>  Nie można wyświetlić raporty ETW w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] interfejsu.  
  
-   Informacje dotyczące zbierania zdarzeń systemu Windows przy użyciu narzędzi profilowania z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] interfejsu, zobacz [porady: zbieranie zdarzeń śledzenia dla systemu Windows (ETW) danych](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).  
  
-   Aby uzyskać informacje dotyczące zbierania danych zdarzeń systemu Windows przy użyciu [VSPerfCmd](../profiling/vsperfcmd.md) narzędzia wiersza polecenia, zobacz [zdarzenia](../profiling/events-vsperfcmd.md).  
  
-   Generowanie raportu ETW za pomocą **VSReport / Podsumowanie: ETW** polecenia. Aby uzyskać więcej informacji, zobacz [VSPerfReport](../profiling/vsperfreport.md).  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Znacznik czasu**|Identyfikuje po wystąpieniu zdarzenia.|  
|**Identyfikator procesu**|Identyfikuje proces, który wygenerował zdarzenie.|  
|**Identyfikator wątku**|Identyfikuje wątku, który wygenerował zdarzenie.|  
|**Opis**|Określa dostawcę zdarzeń.|  
|**Typ**|Określa typ zdarzenia.|  
|**Właściwości**|Właściwości zdarzenia. Każde wydarzenie jest parę oddzielone przecinkami, nazwa wartość jest ujęta w nawiasy kwadratowe.|