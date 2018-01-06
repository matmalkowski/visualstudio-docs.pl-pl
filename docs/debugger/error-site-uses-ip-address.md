---
title: "Błąd: Witryna korzysta z adresu IP | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.error.webdbg_siteusesipaddress
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: debugger, Web application errors
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e6073fd88221e307b46a90173526876f2e2186d4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="error-site-uses-ip-address"></a>Błąd: witryna korzysta z adresu IP
Ten błąd występuje, gdy debuger próbuje automatyczne dołączanie do aplikacji sieci Web, który jest używany adres IP. Dzieje się tak w przypadku zmiany **Identyfikacja witryny sieci Web** do **użyć określonego adresu IP** w usługach IIS.  
  
 Dla automatyczne dołączanie do pracy, należy utworzyć projekt z określonego adresu IP, a nie tylko nazwę komputera. W przeciwnym razie debuger będzie Zmień nazwę maszyny localhost, co spowoduje niepowodzenie wysyłania zlecenie debug w usługach IIS.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Ręczne Użyj zamiast tego dołączyć (z menu debugowanie wybierz **dołączyć do procesu**).  
  
     —lub—  
  
2.  Zmień **Identyfikacja witryny sieci Web usług IIS** ustawienie.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji sieci Web: Błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)