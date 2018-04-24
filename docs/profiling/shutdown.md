---
title: Zamknięcie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1a9c79b132dcd3358c697f9b08466af306aeed21
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="shutdown"></a>Zamykanie
**Zamknięcia** opcja oczekiwania dla żadnego obecnie profilowany proces, aby zakończyć lub odłączyć, a następnie wyłącza profilera i zamyka plik danych profilowania. **Zamknięcia** opcja musi być ostatnie polecenie profilowania Uruchom.  
  
 Jeśli nie określono parametr limitu czasu, **zamknięcia** opcja będzie czekać w nieskończoność. Jeśli określono parametr limitu czasu, opcja zwraca po określonej liczbie sekund bez wyłączania profilera i zamykania pliku danych.  
  
 **Zamknięcia** opcja musi być jedyną opcją określona w wierszu polecenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /Shutdown[:Timeout]  
```  
  
#### <a name="parameters"></a>Parametry  
 `Timeout`  
 -   (Opcjonalnie) Jeśli zostanie określona, opcja zwraca po określonej liczbie sekund bez wyłączania profilera i zamykania pliku danych profilowania.  
  
## <a name="see-also"></a>Zobacz też  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)