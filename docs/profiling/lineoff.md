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
ms.openlocfilehash: ba5d8c3e2644c94a4e15115661341a34c9e6f761
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34845431"
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
  
## <a name="see-also"></a>Zobacz także  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)