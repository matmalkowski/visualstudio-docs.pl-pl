---
title: LineOff | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 76082063-20ef-47ae-ad64-81b43b654865
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e0bde53a409428d140afe498c2894e93e1355726
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2018
---
# <a name="lineoff"></a>LineOff
Domyślnie profilera zbiera źródła kodu wiersza numer wiersza numer przesunięcia danych i gdy używana jest metoda profilowania próbkowania. VSPerfCmd **LineOff** opcji wyłącza zbieranie danych numer wiersza podczas VSPerfCmd są używane do uruchamiania aplikacji. Dane profilowania zbieranych funkcji poziomie podczas **LineOff** jest określona.  
  
 Można użyć **LineOff** tylko z **uruchamianie** opcję, i tylko gdy profilera zainicjowano do próbkowania przy użyciu **Start**:**próbki** opcji.  
  
## <a name="syntax"></a>Składnia  
  
```cmd  
VSPerfCmd.exe /Launch:AppName /LineOff [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 Brak  
  
## <a name="required-options"></a>Wymagane opcje  
 **LineOff** opcji można użyć tylko w wierszu polecenia, który zawiera **uruchamianie** opcji.  
  
 **Uruchom:** `AppName`  
 Uruchamia określony aplikację i rozpocznie się profilowania za pomocą metody pobierania próbek.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie uruchamia aplikację i profilera i wyłącza pobierania próbek na poziomie wiersza.  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /LineOff  
```  
  
## <a name="see-also"></a>Zobacz też  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)