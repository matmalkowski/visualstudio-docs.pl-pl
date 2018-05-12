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
ms.openlocfilehash: 8c835894d18ca1aea33f26f234a4df914114089c
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2018
---
# <a name="shutdown"></a>Zamykanie
**Zamknięcia** opcja oczekiwania dla żadnego obecnie profilowany proces, aby zakończyć lub odłączyć, a następnie wyłącza profilera i zamyka plik danych profilowania. **Zamknięcia** opcja musi być ostatnie polecenie profilowania Uruchom.  
  
 Jeśli nie określono parametr limitu czasu, **zamknięcia** opcja oczekiwania przez czas nieokreślony. Jeśli określono parametr limitu czasu, opcja zwraca po określonej liczbie sekund bez wyłączania profilera i zamykania pliku danych.  
  
 **Zamknięcia** opcja musi być jedyną opcją określona w wierszu polecenia.  
  
## <a name="syntax"></a>Składnia  
  
```cmd  
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