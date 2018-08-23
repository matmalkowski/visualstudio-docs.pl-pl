---
title: 'Błąd: Serwer sieci web nie skonfigurowano poprawnie | Dokumentacja firmy Microsoft'
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
- vs.debug.remote.projnotconfigured
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: 875ba87f-c372-4126-8fe3-e33931cf26c0
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 82d827e0f821712306cf1ec6049129fbf4437d67
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42682715"
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>Błąd: Serwer sieci Web nie jest prawidłowo skonfigurowany
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [błąd: serwer sieci web nie jest poprawnie skonfigurowany](https://docs.microsoft.com/visualstudio/debugger/error-the-web-server-is-not-configured-correctly).  
  
Możliwe przyczyny tego błędu:  
  
-   Podczas próby debugowania aplikacji sieci Web platformy .NET, który został skopiowany do innej maszyny, ręcznie zmieniono jego nazwę lub przenieść.  
  
-   Nie ma wystarczającej liczby połączeń usług IIS. Aby uzyskać więcej informacji na temat wdrażania witryny sieci web usług IIS, zobacz [Utwórz witrynę sieci Web](http://www.iis.net/learn/get-started/getting-started-with-iis/create-a-web-site).  
  
-   Jeśli próbujesz debugowania aplikacji ASP.NET, zobacz [publikowania w usługach IIS](https://docs.asp.net/en/latest/publishing/iis.html) instrukcje dotyczące wdrażania na komputerze zdalnym, uruchomione usługi IIS 8 lub nowszy, lub [zdalnego programu na komputerze zdalnym w wersji 7.5 usług IISdebugowanieASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) instrukcje dotyczące wdrażania do komputera zdalnego z programem IIS 7.5.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji sieci Web: Błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)



