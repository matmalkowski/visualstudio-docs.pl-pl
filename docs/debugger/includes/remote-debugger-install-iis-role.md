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
ms.openlocfilehash: 103000c2ded944236762ffd55603877ece7b7968
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38809465"
---
Te kroki pokazują podstawową konfiguracją usług IIS. Aby uzyskać więcej szczegółowych informacji lub zainstalować maszyną Windows Desktop, zobacz [publikowania w usługach IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration) lub [3.5 przy użyciu platformy ASP.NET w programie IIS 8.0 i program ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

W przypadku systemów operacyjnych Windows Server, użyj **Dodaj role i funkcje** kreatora za pośrednictwem **Zarządzaj** łącze lub **pulpitu nawigacyjnego** łącze w **Menedżera serwera**. Na **ról serwera** kroku, pole wyboru dla **serwer sieci Web (IIS)**.

![W kroku role serwera wybierz zaznaczona została rola Serwer sieci Web IIS.](../media/remotedbg-server-roles-ws2012.png)

Na **usług ról** kroku, Wybieranie usług ról usług IIS, użytkowników lub zaakceptuj domyślną rolę usług pod warunkiem. Jeśli chcesz włączyć wdrożenia przy użyciu publikowania, ustawienia i narzędzia Web Deploy, upewnij się, że **narzędzia i skrypty zarządzania usługami IIS** jest zaznaczone.

Postępuj zgodnie z instrukcjami procedury potwierdzenie instalacji roli serwera sieci web i usług. Po zainstalowaniu roli serwera sieci Web (IIS) nie jest wymagane ponowne uruchomienie serwera/IIS.