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
ms.openlocfilehash: 62bdcd8109263cc86e13484d146e46f8e95c7198
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2018
---
Te kroki pokazują podstawową konfiguracją usług IIS. Aby uzyskać więcej szczegółowych informacji lub zainstalować na komputerze pulpitu systemu Windows, zobacz [publikowania w usługach IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration) lub [IIS 8.0 przy użyciu programu ASP.NET 3.5 i ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

Dla systemów operacyjnych Windows Server, użyj **Dodaj role i funkcje** za pomocą kreatora **Zarządzaj** łącze lub **pulpitu nawigacyjnego** łącze w **Menedżera serwera**. Na **ról serwera** kroku, pole wyboru dla **serwer sieci Web (IIS)**.

![W kroku role serwera wybierz wybrano roli Serwer sieci Web IIS.](../media/remotedbg-server-roles-ws2012.png)

Na **usług ról** kroku, wybierz usługi ról usług IIS, konieczna jest lub zaakceptuj wartość domyślną rolę usług pod warunkiem. Jeśli planujesz wdrożyć przy użyciu narzędzia Web Deploy, upewnij się, że **narzędzia i skrypty zarządzania usługami IIS** jest zaznaczone.

Postępuj zgodnie z instrukcjami kroki potwierdzenie, aby zainstalować rolę serwera sieci web oraz usługi. Po zainstalowaniu roli serwera sieci Web (IIS) nie jest wymagane ponowne uruchomienie serwera i IIS.