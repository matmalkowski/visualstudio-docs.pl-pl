---
title: LineOff | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76082063-20ef-47ae-ad64-81b43b654865
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6914a94300cd7fdb06db8743159698047451fd74
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="lineoff"></a>LineOff
Domyślnie profilera zbiera źródła kodu wiersza numer wiersza numer przesunięcia danych i gdy używana jest metoda profilowania próbkowania. VSPerfCmd **LineOff** opcji wyłącza zbieranie danych numer wiersza podczas VSPerfCmd są używane do uruchamiania aplikacji. Dane profilowania zbieranych funkcji poziomie podczas **LineOff** jest określona.  
  
 Można użyć **LineOff** tylko z **uruchamianie** opcję, i tylko gdy profilera zainicjowano do próbkowania przy użyciu **Start**:**próbki** opcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /Launch:AppName /LineOff [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 Brak  
  
## <a name="required-options"></a>Wymagane opcje  
 **LineOff** opcji można użyć tylko w wierszu polecenia, który zawiera **uruchamianie** opcji.  
  
 **Uruchom:**`AppName`  
 Uruchamia określony aplikację i rozpocznie się profilowania za pomocą metody pobierania próbek.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie uruchamia aplikację i profilera i wyłącza pobierania próbek na poziomie wiersza.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /LineOff  
```  
  
## <a name="see-also"></a>Zobacz też  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)