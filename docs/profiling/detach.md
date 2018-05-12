---
title: Odłącz | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: d9d1b52c-7f28-467d-b1e0-512afc4e46c9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 33255899cbd3ac1fb539d29de5d8b6875a7ea8d6
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2018
---
# <a name="detach"></a>Odłącz
VSPerfCmd.exe **Detach** opcji rozłącza profilera z określonych procesów lub wszystkich procesów, jeśli żaden nie jest określony. Profilowanie muszą zostać zainicjowane przy użyciu metody pobierania próbek.  
  
 Profilowania, która została uruchomiona w trybie **uruchamianie** lub **Attach** opcje może zostać rozłączona z **Detach**. Profiler może być reattched za pomocą kolejnych **Attach** poleceń.  
  
 **Odłącz** nie zamknąć plik danych profilowania. Użyj **zamknięcia** opcję, aby zakończyć profilowania i zamknij plik danych.  
  
> [!NOTE]
>  Jeśli **Start** określono opcję z **Crosssession** opcję wszelkie wywołania **VSPerfCmd /Attach** lub **VSPerfCmd /Detach** musi Określ również **Crosssession**.  
  
## <a name="syntax"></a>Składnia  
  
```cmd  
VSPerfCmd.exe /Detach[:PIDs|ProcessNames]  
```  
  
#### <a name="parameters"></a>Parametry  
 `PIDs|ProcessNames`  
 `PID` Identyfikatorem systemu liczbowego jednego lub więcej procesów.  
  
 `ProcessNames` -nazwę procesu. Korzystający z wielu wystąpień nazwanych procesu, wyniki są nieprzewidywalne.  
  
 Wiele procesów należy oddzielić przecinkami.  
  
 Jeśli żaden proces nie zostanie określony, profiler jest odłączona od wszystkich PROFILOWANEGO procesu.  
  
## <a name="valid-options"></a>Prawidłowe opcje  
 Następujące **VSPerfCmd** opcje można łączyć z **Attach** opcji w jednym wierszu polecenia.  
  
 **Crosssession**  
 Włącza profilowanie aplikacji w sesji innej niż sesji logowania. Jeśli wymagane **Start** określono opcję z **Crosssession** opcji.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie **Detach** polecenie zawiesza profilowania i **zamknięcia** polecenie zamyka plik danych profilera.  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
;REM Excercise the application  
VSPerfCmd.exe /Detach  
VSPerfCmd.exe /Shutdown  
```  
  
## <a name="see-also"></a>Zobacz też  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)