---
title: 'Błąd: Przekroczono limit czasu podczas debugowania usług sieci Web | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
- XML Web services, timeout while debugging
ms.assetid: 4b7df112-788a-4429-9a0c-4c6dac4fb609
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dee3017114c645c5bc3c2001e0cb2cafda48ef53
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42679885"
---
# <a name="error-timeout-while-debugging-web-services"></a>Błąd: przekroczono limit czasu podczas debugowania usług sieci Web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [błąd: limit czasu podczas debugowania usług sieci Web](https://docs.microsoft.com/visualstudio/debugger/error-timeout-while-debugging-web-services).  
  
Gdy są Wkraczanie do usługi sieci Web XML, z kodu wywołującego, wywołanie może czasami limit czasu, w wyniku możliwe, że nie można kontynuować debugowanie. Zobaczysz komunikat o błędzie, np. to.  
  
```  
An unhandled exception of type 'System.Net.WebException' occurred in   
system.Web.services.dll  
Additional information: The operation has timed-out.  
```  
  
## <a name="solution"></a>Rozwiązanie  
 Aby uniknąć tego problemu, należy ustawić wartość limitu czasu dla wywołania usługi sieci Web XML na wartość infinite, jak pokazano w poniższym przykładzie:  
  
```  
Service1 obj = new Service1();  
obj.TimeOut = -1; // infinite time out.  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji sieci Web: Błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)



