---
title: Debugowanie zdalne z Python platformy Azure
description: Jak skonfigurować usługę aplikacji Azure używać programu Visual Studio zdalne debugowanie aplikacji Python.
ms.date: 06/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 92fd9cf7c81b0b383a185a76eaaf5a3bfc8b93a5
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37057983"
---
# <a name="remotely-debugging-python-code-on-azure"></a>Zdalne debugowanie kodu Python na platformie Azure

[Python obsługi w programie Visual Studio](installing-python-support-in-visual-studio.md) umożliwia zdalne debugowanie kodu języka Python, który działa na usłudze Azure App Service. W odróżnieniu od prostego zdalnego debugowania, w tym scenariuszu komputer docelowy nie jest bezpośrednio dostępny za pośrednictwem protokołu TCP, więc program Visual Studio udostępnia serwer proxy, który opisuje protokół debugera za pośrednictwem protokołu HTTP. Projektów utworzonych za pomocą szablonu sieci Web automatycznie skonfigurować ten serwer proxy w wygenerowanym `web.debug.config` pliku. Zdalne debugowanie jest włączona podczas publikowania konfiguracji debugowania projektu, zgodnie z opisem w [publikowania w usłudze Azure App Service] (publishing-python-web-applications-do-azure-from-visual-studio.md.

Ponieważ Azure debugowania zdalnego używa gniazda sieci web, sockets musi być włączony dla aplikacji usługi za pośrednictwem [portalu Azure](https://portal.azure.com) , przechodząc do **Ustawienia > Ustawienia aplikacji** i włączając  **Ustawienia ogólne > sieci Web sockets** do **na**, wybierając **zapisać** do zastosowania zmiany. (Należy pamiętać, że **debugowanie** ustawienia nie są stosowane do debugowania języka Python.)

![Włączanie gniazda sieci web w portalu Azure](media/azure-remote-debugging-enable-web-sockets.png)

Po projektu jest prawidłowo wdrożony i gniazda sieci web jest włączona, możesz dołączyć do usługi App Service z **Eksploratora serwera** w programie Visual Studio (**Widok > Eksploratora serwera**). Zlokalizuj witryny w obszarze **Azure > App Service** i grupy do odpowiednich zasobów, kliknij prawym przyciskiem myszy i wybierz **dołączanie debugera (Python)**. ( **Dołączyć debuger** command jest aplikacji .NET do uruchamiania usług IIS i przydaje się tylko wtedy, gdy .NET hostowane kod z aplikacji języka Python.)

Visual Studio może przejść bezpośrednio do zestawu instrukcje dotyczące dołączania bezpośrednio, zgodnie z poniższym opisem w [Dołączanie bez Eksploratora serwera](#attaching-without-server-explorer). Jeśli nie widzisz **dołączanie debugera (Python)** polecenia lub programu Visual Studio nie może dołączyć do swojej witryny, zobacz [Rozwiązywanie problemów z Azure zdalne debugowanie](debugging-remote-python-code-on-azure-troubleshooting.md).

W przypadku pomyślnego nawiązania Podłączanie programu Visual Studio zmienia się na widok debugera. Pasek narzędzi wskazuje, takich jak debugowanym procesie `wss://` identyfikatora URI:

![Profilowanie witryny sieci Web usługi aplikacji Azure](media/azure-remote-debugging-attached.png)

Po dołączeniu działanie debugowania jest przeważnie taka sama jak w przypadku regularnego zdalnego debugowania mogą ulec kilka ograniczeń. W szczególności serwer sieci web usług IIS obsługuje żądania przychodzącego, który deleguje je do kodu Python przez FastCGI ma limit czasu dla obsługi żądań, która domyślnie określa 90 sekund. Jeśli obsługa żądania trwa dłużej niż ten limit czasu (na przykład ze względu na proces wstrzymana w punkcie przerwania), usługi IIS kończy proces kończy sesję debugowania. 

## <a name="attaching-without-server-explorer"></a>Dołączanie bez Eksploratora serwera

Aby dołączyć debuger bezpośrednio w usłudze App Service, postępuj zgodnie z instrukcjami na stronie informacje o serwera proxy protokołu WebSocket wdrażającej do swojej witryny w Visual Studio `<site_url>/ptvsd` takich jak `ptvsdemo.azurewebsites.net/ptvsd`. Również odwiedzić tę stronę sprawdza, czy został poprawnie skonfigurowany:

![Azure strony informacji serwera proxy debugowania zdalnego](media/azure-remote-debugging-proxy-info-page.png)

Zgodnie z instrukcją, należy utworzyć adres URL przy użyciu klucza tajnego z `web.debug.config`, jest generowany ponownie projekt zostanie opublikowana. Ten plik jest ukryty domyślnie w Eksploratorze rozwiązań i nie jest uwzględniony w projekcie, dlatego Pokaż wszystkie pliki lub otworzyć go w edytorze oddzielne. Po otwarciu pliku przyjrzeć się wartość appSetting o nazwie `WSGI_PTVSD_SECRET`:

![Określanie punktu końcowego debugera w usłudze Azure App Service](media/azure-remote-debugging-secret.png)

Adres URL, należy teraz ma postać `wss://<secret>@<site_name>.azurewebsites.net/ptvsd` gdzie Zastąp &lt;klucz tajny&gt;i &lt;nazwa_witryny&gt; w ciągu o określonej wartości.

Aby dołączyć debuger, wybierz **debugowania > dołączyć do procesu**, wybierz pozycję **zdalnego debugowania języka Python** w **transportu** listy rozwijanej, wprowadź adres URL do  **Pole tekstowe kwalifikator**, i naciśnij klawisz Enter. Jeśli program Visual Studio może nawiązywać połączeń z usługi aplikacji, zawiera jeden proces Python na liście. Wybierz go, a następnie **Attach** można rozpocząć debugowania:

![Przy użyciu Dołącz do procesu okna dialogowego do dołączenia do usługi Azure witryny sieci web](media/azure-remote-debugging-manual-attach.png)
