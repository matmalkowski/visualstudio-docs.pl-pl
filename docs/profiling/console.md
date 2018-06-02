---
title: Konsola | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 04cf166880ac8bcf83d4657b9c1c2eec1b46a14a
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34690819"
---
# <a name="console"></a>Konsola
VSPerfCmd.exe **konsoli** opcja uruchamia określonej aplikacji w nowym oknie wiersza polecenia. **Konsola** można używać tylko z VSPerfCmd **uruchamianie** opcji. Jeśli aplikacja nie jest aplikacją wiersza polecenia **konsoli** nie ma wpływu.  
  
## <a name="syntax"></a>Składnia  
  
```cmd  
VSPerfCmd.exe /Launch:AppName /Console  
```  
  
#### <a name="parameters"></a>Parametry  
 Brak  
  
## <a name="required-options"></a>Wymagane opcje  
 **Konsola** można określić tylko w wierszu polecenia, który zawiera także **uruchamianie** opcji.  
  
 **Uruchom:** `AppName`  
 Uruchamia profilera i aplikacji określonej przez `AppName`.  
  
## <a name="see-also"></a>Zobacz także  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)