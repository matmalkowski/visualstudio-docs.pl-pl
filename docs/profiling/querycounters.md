---
title: QueryCounters | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 64bcd93e6d9045558c231c3b47ff967ffe14c078
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
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