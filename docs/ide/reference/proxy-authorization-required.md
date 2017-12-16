---
title: "Korygowanie proxy autoryzacji wymagane błędy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 09/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2d24ae1-9902-460e-b72a-0299eed9ee82
caps.latest.revision: "4"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7c8c4562f6c3a3b61274024b541f78321c9a8408
ms.sourcegitcommit: 64c7682ec3a2cbea684e716803398d4278b591d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2017
---
# <a name="proxy-authorization-required"></a>Serwer proxy zezwoleń wymaganych

Ten błąd występuje zazwyczaj, gdy użytkownicy są połączeni z Internetem za pośrednictwem serwera proxy, a serwer proxy blokuje wywołań Visual Studio wysyła do niektórych zasobów sieciowych.

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Uruchom ponownie program Visual Studio. Powinny być wyświetlane okno dialogowe uwierzytelniania serwera proxy. Wprowadź swoje poświadczenia w oknie dialogowym.

- Jeśli w kroku powyżej nie rozwiąże problemu, może to być spowodowane serwera proxy nie monit o podanie poświadczeń dla http://go.microsoft.com adresów, ale jest to spowodowane *. visualStudio.com adresów. Na tych serwerach należy dozwolonych poniższą listę adresów URL, aby odblokować wszystkie logowania scenariusze w programie Visual Studio:

    - *.windows.net

    - *.microsoftonline.com

    - *.visualstudio.com

    - *.microsoft.com

    - *.live.com

- W przeciwnym razie można usunąć adres http://go.microsoft.com z listy dozwolonych, aby w oknie dialogowym uwierzytelniania serwera proxy zostaną wyświetlone zarówno adres http://go.microsoft.com i punkty końcowe serwera po ponownym uruchomieniu programu Visual Studio.

    LUB

- Do korzystania z poświadczeń domyślnej z serwera proxy, należy wykonać następujące:

    1. Znajdź **devenv.exe.config** (plik konfiguracji devenv.exe) w: **%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** lub **% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE**.

    1. W pliku konfiguracji, należy znaleźć `<system.net>` zablokować, a następnie dodaj ten kod:

        ```xml
        <defaultProxy enabled="true" useDefaultCredentials="true">
            <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>
        </defaultProxy>
        ```

        Adres serwera proxy poprawne należy wstawić sieci w `proxyaddress="<http://<yourproxy:port#>`.

    LUB

- Można również postępuj zgodnie z instrukcjami [ten wpis](http://blogs.msdn.com/b/rido/archive/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy.aspx) do Dodaj kod, który umożliwi używanie serwera proxy.
