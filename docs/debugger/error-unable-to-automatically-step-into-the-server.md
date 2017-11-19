---
title: "Błąd: Nie można automatycznie Wkrocz do serwera | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.causality_no_server_response
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords: remote debugging, notification error
ms.assetid: 9a370ccc-d358-429c-b285-9b6c0649bc68
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 63e8d73b9df650a1d98b0c9f080c7b32cc0a324e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>Błąd: Nie można automatycznie rozpocząć wykonywania krok po kroku na serwerze
Odczytuje kod błędu:  
  
 Nie można automatycznie Wkrocz do serwera. Debuger nie został powiadomiony, zanim wykonano procedury zdalnej  
  
 Ten błąd może wystąpić, gdy użytkownik próbuje wkroczyć do usługi sieci web (zobacz [wykonywanie krok po kroku w XML sieci Web usługi](http://msdn.microsoft.com/en-us/8e67de38-bf5f-41cc-a457-1b88ce63d764)). Może wystąpić po każdej zmianie [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] nie jest skonfigurowany prawidłowo.  
  
 Możliwe przyczyny to:  
  
-   Plik web.config dla Twojego [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji nie ustawia debugowania na wartość "true" (zobacz [tryb debugowania w aplikacjach ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)).  
  
-   Wersja [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] został zainstalowany po zainstalowaniu programu Visual Studio. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]powinien być zainstalowany przed Visual Studio. Aby rozwiązać ten problem, należy użyć systemu Windows **Panel sterowania > programy i funkcje** Aby naprawić instalację programu Visual Studio.  
  
## <a name="see-also"></a>Zobacz też  
 [Zdalne debugowanie błędów i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Debugowanie zdalne](../debugger/remote-debugging.md)