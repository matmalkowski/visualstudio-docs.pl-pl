---
title: 'Błąd: Przekroczono limit czasu podczas debugowania usług sieci Web | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
- XML Web services, timeout while debugging
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 41c6793e1fdf4e3ed2d7e42fbd32bd20ad9f494a
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37056271"
---
# <a name="error-timeout-while-debugging-web-services"></a>Błąd: przekroczono limit czasu podczas debugowania usług sieci Web
Gdy są Wkraczanie do usługi XML sieci Web, z kodu wywołującego, wywołanie może czasami limit czasu, w wyniku że nie będzie można kontynuować debugowania. Może zostać wyświetlony komunikat błędu, takich jak ta.  
  
```cmd
An unhandled exception of type 'System.Net.WebException' occurred in   
system.Web.services.dll  
Additional information: The operation has timed-out.  
```  
  
## <a name="solution"></a>Rozwiązanie  
 Aby uniknąć tego problemu, należy ustawić wartość limitu czasu dla wywołania usługi XML sieci Web na wartość infinite, jak pokazano w poniższym przykładzie:  
  
```csharp
Service1 obj = new Service1();  
obj.TimeOut = -1; // infinite time out.  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji sieci Web: Błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
