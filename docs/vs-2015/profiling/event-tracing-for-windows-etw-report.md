---
title: Śledzenie zdarzeń systemu Windows (ETW) raport | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Event tracing for Windows profiling report
- ETW profiling report
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 49ea37f6830c7e4fdf8c8d94b0f323c6337329c5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42680494"
---
# <a name="event-tracing-for-windows-etw-report"></a>Zdarzenia śledzenia dla systemu Windows (ETW) — Raport
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [raportu śledzenie zdarzeń dla Windows (ETW)](https://docs.microsoft.com/visualstudio/profiling/event-tracing-for-windows-etw-report).  
  
Raport śledzenie zdarzeń dla Windows (ETW) zawiera listę zdarzeń ETW, które zostały zapisane w sesji pomiaru wydajności [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Profiling Tools. Dane ETW są zbierane w pliku danych binarnych (ETL).  
  
> [!NOTE]
>  Nie można wyświetlić raporty ETW w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interfejsu.  
  
-   Aby uzyskać informacje dotyczące zbierania zdarzeń systemu Windows przy użyciu narzędzi profilowania z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interfejsu, zobacz [jak: danych zbierania zdarzeń śledzenia dla Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).  
  
-   Aby uzyskać informacje dotyczące zbierania danych ETW przy użyciu [VSPerfCmd](../profiling/vsperfcmd.md) narzędzi wiersza polecenia, zobacz [zdarzenia](../profiling/events-vsperfcmd.md).  
  
-   Generowanie raportu ETW za pomocą **VSReport / Summary: ETW** polecenia. Aby uzyskać więcej informacji, zobacz [VSPerfReport](../profiling/vsperfreport.md).  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Znacznik czasu:**|Umożliwia określenie, kiedy wystąpiło zdarzenie.|  
|**Identyfikator procesu**|Identyfikuje proces, który wygenerował zdarzenie.|  
|**Identyfikator wątku**|Identyfikuje wątku, który wygenerował zdarzenie.|  
|**Opis**|Określa dostawcę zdarzeń.|  
|**Typ**|Określa typ zdarzenia.|  
|**Właściwości**|Właściwości zdarzenia. Każde wydarzenie jest parą rozdzielonych przecinkami, nazwa wartość, która jest ujęty w nawiasy kwadratowe.|



