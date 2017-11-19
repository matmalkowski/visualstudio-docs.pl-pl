---
title: QueryCounters | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2b8dbbf2539980f775fb6385303a3fcfe7ae7e07
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="querycounters"></a>QueryCounters
**QueryCounters** opcja Wyświetla liczniki wydajności procesora CPU (sprzęt), które są dostępne na komputerze.  
  
 **QueryCounters** musi być jedyną opcją w wierszu polecenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /QueryCounters  
```  
  
#### <a name="parameters"></a>Parametry  
 Brak  
  
## <a name="remarks"></a>Uwagi  
 Jeśli używasz metody Instrumentacji profilera mogą zbierać wartości co najmniej jeden liczniki wydajności procesora CPU na każdego zdarzenia zbierania danych. Gdy używana jest metoda profilowania próbkowania, można określić jeden licznik zdarzeń i liczbę wystąpień zdarzeń ma być używany jako interwał próbkowania.  
  
 Różnych procesorów ujawnić różne liczniki wydajności procesora CPU. Profiler definiuje zestaw ogólnego liczniki, które mogą być używane w prawie wszystkie procesory. **QueryCounters** opcja wyświetla zarówno nazw liczników ogólnego i nazwy liczników, które są specyficzne dla procesora.  
  
## <a name="see-also"></a>Zobacz też  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)