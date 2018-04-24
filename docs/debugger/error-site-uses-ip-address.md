---
title: 'Błąd: Witryna korzysta z adresu IP | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.webdbg_siteusesipaddress
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b726902c57cc95b694f2ab7e656a444ed42a0ba9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
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