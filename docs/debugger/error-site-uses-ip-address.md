---
title: "Błąd: Witryna korzysta z adresu IP | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.webdbg_siteusesipaddress
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: debugger, Web application errors
ms.assetid: b2b8ddc8-746d-46e3-87a6-b956b1ee048d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6e1ee3e2ed3d6524749757806931fbb8c4b9a36a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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