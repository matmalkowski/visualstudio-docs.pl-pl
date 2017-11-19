---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 103cefa8573c8f44efff0b53b0c09a5ec26706e6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
Te kroki pokazują podstawową konfiguracją usług IIS. Aby uzyskać więcej szczegółowych informacji lub zainstalować na komputerze pulpitu systemu Windows, zobacz [publikowania w usługach IIS](https://docs.microsoft.com/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration) lub [IIS 8.0 przy użyciu programu ASP.NET 3.5 i ASP.NET 4.5](https://docs.microsoft.com/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

Dla systemów operacyjnych Windows Server, użyj **Dodaj role i funkcje** za pomocą kreatora **Zarządzaj** łącze lub **pulpitu nawigacyjnego** łącze w **Menedżera serwera**. Na **ról serwera** kroku, pole wyboru dla **serwer sieci Web (IIS)**.

![W kroku role serwera wybierz wybrano roli Serwer sieci Web IIS.](../media/remotedbg-server-roles-ws2012.png)

Na **usług ról** kroku, wybierz usługi ról usług IIS, konieczna jest lub zaakceptuj wartość domyślną rolę usług pod warunkiem.

Postępuj zgodnie z instrukcjami kroki potwierdzenie, aby zainstalować rolę serwera sieci web oraz usługi. Po zainstalowaniu roli serwera sieci Web (IIS) nie jest wymagane ponowne uruchomienie serwera i IIS.