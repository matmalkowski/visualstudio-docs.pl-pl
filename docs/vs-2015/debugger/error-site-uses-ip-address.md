---
title: 'Błąd: Witryna korzysta z adresu IP | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.webdbg_siteusesipaddress
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: b2b8ddc8-746d-46e3-87a6-b956b1ee048d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93d64f06db4b1f070da4f0963ed879ef64e4cb33
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42678080"
---
# <a name="error-site-uses-ip-address"></a>Błąd: witryna korzysta z adresu IP
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [błąd: witryna korzysta z adresu](https://docs.microsoft.com/visualstudio/debugger/error-site-uses-ip-address).  
  
Ten błąd występuje, gdy debuger próbuje automatyczne dołączanie do aplikacji sieci Web, który jest przy użyciu adresu IP. Dzieje się tak w przypadku zmiany **Identyfikacja witryny sieci Web** do **użyć określonego adresu IP** w usługach IIS.  
  
 Aby uzyskać automatyczne dołączanie do pracy, należy utworzyć projekt z określonego adresu IP, a nie tylko nazwę maszyny. W przeciwnym razie debuger zmieni nazwę komputera, na hoście lokalnym, co spowoduje niepowodzenie wysyłania czasownik debug w usługach IIS.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Użyj ręcznie dołączyć zamiast (wybierz z menu Debugowanie **dołączyć do procesu**).  
  
     —lub—  
  
2.  Zmiana **Identyfikacja witryny sieci Web usług IIS** ustawienie.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji sieci Web: Błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)



