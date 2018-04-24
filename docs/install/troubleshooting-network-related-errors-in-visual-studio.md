---
title: Rozwiązywania problemów związanych z siecią, podczas instalowania lub użyć programu Visual Studio
description: Rozwiązania błędów dotyczących sieci lub serwera proxy, które można napotkać podczas instalowania lub użyć programu Visual Studio za zaporą lub serwer proxy.
ms.custom: ''
ms.date: 02/12/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: troubleshooting
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs, Visual Studio
- proxy errors, Visual Studio
ms.assetid: ''
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 41fed015f4ad80c3c3b74bc77ea3b9cc6ed8eb18
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="troubleshooting-network-related-errors-when-you-install-or-use-visual-studio"></a>Rozwiązywania problemów związanych z siecią, podczas instalowania lub użyć programu Visual Studio

Mamy rozwiązania najczęstszych błędów dotyczących sieci lub serwera proxy, które można napotkać podczas instalowania lub użyć programu Visual Studio za zaporą lub serwer proxy.

## <a name="error-proxy-authorization-required"></a>Błąd: "Proxy zezwoleń wymaganych"

Ten błąd występuje zazwyczaj, gdy użytkownicy są połączeni z Internetem za pośrednictwem serwera proxy, a serwer proxy blokuje wywołań Visual Studio wysyła do niektórych zasobów sieciowych.

### <a name="to-fix-this-proxy-error"></a>Aby naprawić ten błąd serwera proxy

- Uruchom ponownie program Visual Studio. Powinny być wyświetlane okno dialogowe uwierzytelniania serwera proxy. Wprowadź swoje poświadczenia, po wyświetleniu monitu w oknie dialogowym.

- Jeśli ponowne uruchomienie programu Visual Studio nie rozwiązuje problemu, może to oznaczać czy serwer proxy nie jest wyświetlany monit o poświadczenia dla protokołu http:&#47;&#47;go.microsoft.com adresów, ale jest to spowodowane &#42;. visualStudio.com adresów. Na tych serwerach należy wziąć pod uwagę listę dozwolonych podobnej o następujących adresach URL, aby odblokować wszystkie logowania scenariusze w programie Visual Studio:

    - &#42;.windows.net

    - &#42;.microsoftonline.com

    - &#42;.visualstudio.com

    - &#42;.microsoft.com

    - &#42;.live.com

- W przeciwnym razie można usunąć http:&#47;&#47;go.microsoft.com adres z listy dozwolonych, dzięki czemu dialog uwierzytelniania serwera proxy zostaną wyświetlone dla obu http:&#47;&#47;go.microsoft.com adres i punkty końcowe serwera, gdy program Visual Studio ponowne uruchomienie.

    LUB

- Jeśli chcesz użyć poświadczeń domyślnej z serwera proxy, można wykonywać następujące czynności:

    1. Znajdź **devenv.exe.config** (plik konfiguracji devenv.exe) w: **%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** lub **% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE**.

    1. W pliku konfiguracji, należy znaleźć `<system.net>` zablokować, a następnie dodaj ten kod:

        ```xml
        <defaultProxy enabled="true" useDefaultCredentials="true">
            <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>
        </defaultProxy>
        ```

        Adres serwera proxy poprawne należy wstawić sieci w `proxyaddress="<http://<yourproxy:port#>`.

    LUB

- Można również postępuj zgodnie z instrukcjami [sposób nawiązywania połączenia za pośrednictwem uwierzytelnionego serwera Proxy sieci Web](http://blogs.msdn.com/b/rido/archive/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy.aspx) blogu pokazuje, jak dodać kod, który umożliwi używanie serwera proxy.

## <a name="error-the-underlying-connection-was-closed"></a>Błąd: "Połączenie podstawowe zostało zamknięte"

Jeśli używasz programu Visual Studio w sieci prywatnej z zaporą, Visual Studio nie można nawiązać połączenia z niektórych zasobów sieciowych. Zasoby te mogą obejmować Visual Studio Team Services (VSTS) dla logowania i licencjonowania NuGet i usług Azure. Jeśli program Visual Studio nie może połączyć się z jednego z tych zasobów, mogą pojawić następujący komunikat o błędzie:

  **Połączenie podstawowe zostało zamknięte: Wystąpił nieoczekiwany błąd podczas wysyłania**

Visual Studio korzysta z protokołu Transport Layer Security (TLS) 1.2 nawiązywania połączenia z zasobami sieciowymi. Urządzenia zabezpieczeń w niektórych sieciach prywatnych blokować niektóre połączenia z serwerem, gdy program Visual Studio korzysta z protokołu TLS 1.2.

### <a name="to-fix-this-connection-error"></a>Aby naprawić ten błąd połączenia

Włącz połączenia dla następujących adresów URL:

- https:&#47;&#47;management.core.windows.net

- https:&#47;&#47;app.vssps.visualstudio.com

- https:&#47;&#47;login.microsoftonline.com

- https:&#47;&#47;login.live.com

- https:&#47;&#47;go.microsoft.com

- https:&#47;&#47;graph.windows.net

- https:&#47;&#47;app.vsspsext.visualstudio.com

- &#42;. azurewebsites.net (dla połączeń Azure)

- &#42;.visualstudio.com

- CDN.vsassets.IO (hosty sieci dostarczania zawartości lub CDN, zawartości)

- &#42;. gallerycdn.vsassets.io (rozszerzenia programu VSTS hostów)

- static2.sharepointonline.com (obsługuje zasoby używane przez program Visual Studio w zestawie sieci szkieletowej interfejsu użytkownika pakietu Office, takich jak czcionki)

- &#42;. nuget.org (dla połączenia narzędzia NuGet)

 > [!NOTE]
 > Powyższa prywatnych adresów URL serwera NuGet mogą nie zostać zawarte w tej listy. Możesz sprawdzić serwery NuGet, które są używane w % APPData%\Nuget\NuGet.Config.

## <a name="get-support"></a>Uzyskaj pomoc techniczną

W przypadku niepowodzenia instalacji programu Visual Studio, zobacz [problemy dotyczące instalacji i uaktualniania Rozwiązywanie problemów z programu Visual Studio 2017](troubleshooting-installation-issues.md) strony. Jeśli żaden z instalacji, kroki rozwiązywania problemów, można skontaktować się nam przez rozmów na żywo, aby uzyskać pomoc przy instalacji (tylko w języku angielskim). Aby uzyskać więcej informacji, zobacz [strony pomocy technicznej programu Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Poniżej przedstawiono kilka więcej opcji pomocy technicznej:

* Problemy z produktu może raportować do nas za pomocą [zgłosić Problem](../ide/how-to-report-a-problem-with-visual-studio-2017.md) narzędzia, która pojawia się zarówno w Instalatorze programu Visual Studio, jak i w środowisku IDE programu Visual Studio.
* Można udostępniać sugestię produktu z nami na [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Można śledzić problemy z produktu i odpowiedzi w [Visual Studio Developer Community](https://developercommunity.visualstudio.com/).
* Można również kontaktowaniu się z nami i innymi deweloperami Visual Studio za pomocą [konwersacji programu Visual Studio w społeczności Gitter](https://gitter.im/Microsoft/VisualStudio). (Ta opcja wymaga [GitHub](https://github.com/) konta.)

## <a name="see-also"></a>Zobacz także

* [Instalowanie i używanie programu Visual Studio za zaporą lub serwerem proxy](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Podręcznik administratora programu Visual Studio](visual-studio-administrator-guide.md)
* [Zainstaluj program Visual Studio 2017 r.](install-visual-studio.md)
