---
title: LineOff | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76082063-20ef-47ae-ad64-81b43b654865
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cf55f34b1ced4d76dcd45ea08514dfbb04ca582b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42677118"
---
# <a name="lineoff"></a>LineOff
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [LineOff](https://docs.microsoft.com/visualstudio/profiling/lineoff).  
  
Domyślnie profiler zbiera kodu wiersza numer i wierszu numer przesunięcia dane źródłowe, gdy używana jest metoda profilowania próbkowanie. Narzędzia VSPerfCmd **LineOff** opcji wyłącza kolekcję danych numeru linii, gdy narzędzie VSPerfCmd są używane do uruchamiania aplikacji. Danych profilowania zbieranych funkcji poziomie podczas **LineOff** jest określony.  
  
 Możesz użyć **LineOff** tylko w przypadku **Uruchom** opcji i tylko gdy program profilujący został zainicjowany do próbkowania przy użyciu **Start**:**przykładowe** opcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /Launch:AppName /LineOff [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 Brak  
  
## <a name="required-options"></a>Wymagane opcje  
 **LineOff** opcja może być używana tylko w wierszu polecenia, który zawiera **Uruchom** opcji.  
  
 **Uruchom:** `AppName`  
 Uruchamia określoną aplikację i rozpoczyna się profilowanie przy użyciu metody pobierania próbek.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie uruchamia aplikację i profiler i wyłączenie próbkowania na poziomie wiersza.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /LineOff  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web platformy ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)



