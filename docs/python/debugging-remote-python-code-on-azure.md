---
title: Zdalne debugowanie przy użyciu języka Python platformy Azure
description: Jak skonfigurować usługi Azure App Service, aby użyć programu Visual Studio zdalne debugowanie aplikacji w języku Python.
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
ms.openlocfilehash: 1e3e70675901128ed6b8d118e54dc10ddee152a5
ms.sourcegitcommit: 96a6d1f16d06ca28d309d05b6e9fbd52f628cdbc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40008622"
---
# <a name="remotely-debug-python-code-on-azure"></a>Zdalne debugowanie kodu w języku Python na platformie Azure

[Obsługa języka Python w programie Visual Studio](installing-python-support-in-visual-studio.md) umożliwia zdalne debugowanie kodu w języku Python, który działa w usłudze Azure App Service. W odróżnieniu od prostego zdalnego debugowania komputera docelowego, w tym scenariuszu nie jest bezpośrednio dostępny za pośrednictwem protokołu TCP, więc program Visual Studio udostępnia serwer proxy, który udostępnia protokół debuger za pośrednictwem protokołu HTTP. Projekty utworzone za pomocą szablonu sieci Web automatycznie skonfigurować ten serwer proxy w wygenerowanym *web.debug.config* pliku. Zdalne debugowanie jest włączona po opublikowaniu **debugowania** konfigurację projektu zgodnie z opisem na [Publikuj w usłudze Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md).

Ponieważ zdalne debugowanie platformy Azure używa gniazda sieci web, gniazda musi być włączona dla usługi App Service za pośrednictwem [witryny Azure portal](https://portal.azure.com) , przechodząc do **ustawienia** > **ustawień aplikacji**  włączając **ustawienia ogólne** > **Web sockets** do **na**, a następnie wybierając pozycję **Zapisz**do zastosowania zmiany. (Należy pamiętać, że **debugowanie** ustawienia nie są stosowane do debugowania języka Python.)

![Włączanie gniazda sieci web w witrynie Azure portal](media/azure-remote-debugging-enable-web-sockets.png)

## <a name="attach-with-server-explorer"></a>Dołącz za pomocą Eksploratora serwera

Gdy projekt jest prawidłowo wdrożony i gniazda sieci web jest włączona, możesz dołączyć do usługi App Service z **Eksploratora serwera** w programie Visual Studio (**widoku** > **Eksploratora serwera**). Znajdź witryny w ramach **Azure** > **usługi App Service** i pasujące zasoby grupy, kliknij prawym przyciskiem myszy i wybierz **dołączanie debugera (Python)**. ( **Dołączyć debuger** polecenie dla aplikacji .NET działających w ramach usług IIS i przydaje się tylko wtedy, gdy .NET współprowadzącym kodu wraz z aplikacji w języku Python.)

Visual Studio może przejść bezpośrednio do zestawu instrukcje dotyczące dołączania bezpośrednio, zgodnie z poniższym opisem w [Dołącz bez Eksploratora serwera](#attach-without-server-explorer). Jeśli nie widzisz **dołączanie debugera (Python)** polecenia lub programu Visual Studio kończy się niepowodzeniem do dołączenia do swojej witryny, zobacz [zdalnego debugowania do rozwiązywania problemów z języka Python i platformą Azure](debugging-remote-python-code-on-azure-troubleshooting.md).

Jeśli dołączanie zakończy się pomyślnie, Visual Studio przełącza widok debugera. Pasek narzędzi wskazuje, takich jak debugowanego procesu `wss://` identyfikatora URI:

![Debugowanie witryny sieci Web w usłudze Azure App Service](media/azure-remote-debugging-attached.png)

Po dołączeniu środowisko debugowania jest przeważnie taka sama, jak w przypadku regularnego debugowania zdalnego podlegających kilku ograniczeniom. W szczególności serwer sieci web usług IIS, obsługujący żądania przychodzące i deleguje je do kodu w języku Python za pomocą interfejsu FastCGI ma limit czasu dla obsługi żądań, którego wartość domyślna to 90 sekund. Jeśli obsługa żądanie dłużej niż ten limit czasu (na przykład z powodu proces wstrzymane w punkcie przerwania), usługi IIS kończy proces zakończenia sesji debugowania. 

## <a name="attach-without-server-explorer"></a>Dołącz bez Eksploratora serwera

Aby dołączyć debuger bezpośrednio w usłudze App Service, postępuj zgodnie z instrukcjami na stronie informacje o serwera proxy protokołu WebSocket, który program Visual Studio wdroży do witryny w  *\<site_url > / ptvsd* takich jak  *ptvsdemo.azurewebsites.NET/ptvsd*. Również odwiedzić tę stronę sprawdza, czy serwer proxy jest skonfigurowany poprawnie:

![Usługa Azure strona informacji o serwera proxy debugowania zdalnego](media/azure-remote-debugging-proxy-info-page.png)

Zgodnie z instrukcjami, skonstruować adres URL przy użyciu klucza tajnego z *web.debug.config*, zostanie ponownie wygenerowany za każdym razem, gdy projekt zostanie opublikowany. Ten plik jest domyślne ukryty, w **Eksploratora rozwiązań** i dlatego nie jest uwzględniony w projekcie, Pokaż wszystkie pliki lub otworzyć go w edytorze oddzielne. Po otwarciu pliku Przyjrzyj się wartość appSetting o nazwie `WSGI_PTVSD_SECRET`:

![Określanie punktu końcowego usługi Azure App Service w debugerze](media/azure-remote-debugging-secret.png)

Adres URL, teraz należy znajduje się w formularzu `wss://<secret>@<site_name>.azurewebsites.net/ptvsd` gdzie Zastąp &lt;klucz tajny&gt; i &lt;nazwa_witryny&gt; w ciągu przy użyciu określonych wartości.

Aby dołączyć debuger, wybierz pozycję **debugowania** > **dołączyć do procesu**, wybierz opcję **zdalnego debugowania w języku Python** w **transportu**listy rozwijanej, wprowadź adres URL do **textbox kwalifikator**i naciśnij klawisz **Enter**. Jeśli program Visual Studio można pomyślnie nawiązać usługi App Service, zawiera jeden proces języka Python na liście. Zaznacz go i następnie **Dołącz** można rozpocząć debugowania:

![Za pomocą Dołącz do procesu okna dialogowego do dołączania do witryny sieci web systemu Azure](media/azure-remote-debugging-manual-attach.png)
