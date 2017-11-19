---
title: "Adresy URL listę dozwolonych podobnej w sieci prywatnej | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 09/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 94348821e44b5ed07e3df5e4859796342919a833
ms.sourcegitcommit: cc288456329aefca1fdaa7ce74751ce195985c14
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/17/2017
---
# <a name="whitelisting-urls-in-a-private-network"></a>Adresy URL listę dozwolonych podobnej w sieci prywatnej

Jeśli używasz programu Visual Studio w sieci prywatnej używane urządzenia zabezpieczeń, takie jak zapory, Visual Studio nie można nawiązać połączenia z niektórych zasobów sieciowych. Te zasoby obejmują Visual Studio Team Services (VSTS) dla logowania i licencjonowania NuGet i usług Azure. Jeśli program Visual Studio nie może połączyć się z jednego z tych zasobów, zostanie wyświetlony następujący komunikat o błędzie:

  **Połączenie podstawowe zostało zamknięte: Wystąpił nieoczekiwany błąd podczas wysyłania**

Visual Studio korzysta z protokołu Transport Layer Security (TLS) 1.2 nawiązywania połączenia z zasobami sieciowymi. Urządzenia zabezpieczeń w niektórych sieciach prywatnych blokować niektóre połączenia z serwerem, gdy program Visual Studio korzysta z protokołu TLS 1.2. Aby naprawić błąd, należy włączyć połączenia dla następujących adresów URL:

- https://management.core.windows.net

- https://app.vssps.visualstudio.com

- https://login.microsoftonline.com

- https://login.live.com

- https://go.microsoft.com

- https://graph.windows.net

- https://app.vsspsext.visualstudio.com

- *. azurewebsites.net (dla połączeń Azure)

- *. nuget.org (dla połączenia narzędzia NuGet)

- *.visualstudio.com

- CDN.vsassets.IO (hosty sieci dostarczania zawartości lub CDN, zawartości)

- *. gallerycdn.vsassets.io (rozszerzenia programu VSTS hostów)

- static2.sharepointonline.com (obsługuje zasoby używane przez program Visual Studio w sieci szkieletowej pakietu office zestawu interfejsu użytkownika, takie jak czcionki)

> [!NOTE]
> Powyższa prywatnych adresów URL serwera NuGet mogą nie zostać zawarte w powyższej listy. Używane serwery NuGet można sprawdzić, otwierając plik %APPData%\Nuget\NuGet.Config.

## <a name="see-also"></a>Zobacz także

[Błąd autoryzacji wymagane serwera proxy](../ide/reference/proxy-authorization-required.md)  
[Internet zasoby używane przez program Visual Studio](../ide/connected-environment.md)  
[Zainstaluj program Visual Studio za serwerem zapory lub serwera proxy](../install/install-visual-studio-behind-a-firewall-or-proxy-server.md)
