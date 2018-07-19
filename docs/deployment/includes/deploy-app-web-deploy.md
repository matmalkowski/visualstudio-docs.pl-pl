---
title: Wdrażanie za pomocą narzędzia Web Deploy
description: Wdrażanie aplikacji za pomocą narzędzia Web Deploy w programie Visual Studio
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 4ef232e64f308699c73c60cbe5b155f1d4ebb725
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38811931"
---
Po zainstalowaniu narzędzia Web Deploy, za pomocą Instalatora platformy sieci Web, możesz wdrożyć aplikację bezpośrednio z programu Visual Studio.

1. Uruchom program Visual Studio z uprawnieniami administratora, a następnie ponownie otwórz projekt.

    Aby wdrożyć aplikację za pomocą narzędzia Web Deploy, wymagane są uprawnienia administratora.

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Publikuj**.

    Jeśli wcześniej skonfigurowano żadnych profilów publikowania **Publikuj** zostanie wyświetlone okienko. Kliknij przycisk **nowy profil**.

1. Dla **wybierz lokalizację docelową publikowania**, wybierz opcję **usług IIS, FTP, itp.** i kliknij przycisk **Publikuj**.

    ![RemoteDBG_Publish_IISl](../../debugger/media/remotedbg_iis_profile.png "RemoteDBG_Publish_IIS")

1. Wprowadź parametry konfiguracji korekcji konfigurację usług IIS.

    ![RemoteDBG_Publish_WebDeployl](../../debugger/media/remotedbg_iis_webdeploy_config.png "RemoteDBG_Publish_WebDeploy")

    Jeśli nazwa hosta nie rozwiąże to podczas sprawdzania poprawności w kolejnych kroków w **serwera** tekst pola, spróbuj użyć adresu IP. Obejmują `http://` jako prefiksu w **serwera** pola.  Upewnij się, że korzystanie z portu 80 w **serwera** tekstu pole i upewnij się, że port 80 i 8172 są otwarte w zaporze.

1. Wybierz **zweryfikować**. Jeśli ustawienia połączenia jest weryfikowana, możesz spróbować do opublikowania.

1. Kliknij przycisk **Publikuj** Aby opublikować aplikację.

    Karta danych wyjściowych dowiesz się, jeśli publikowania zakończy się pomyślnie, a przeglądarka następnie otwiera aplikację.

    Jeśli wystąpi błąd podczas wymieniania narzędzia Web Deploy, sprawdź ponownie kroki instalacji narzędzia Web Deploy i upewnij się, że odpowiednie porty są otwarte (Web Deploy wymaga także portu 8172 być otwarte na serwerze).

    Jeśli aplikacja wdrożona pomyślnie, ale nie działa poprawnie, może to być problem z konfiguracji usług IIS, instalacja programu ASP.NET lub konfigurację witryny sieci Web. W systemie Windows Server otwórz witrynę sieci Web za pomocą programu IIS, aby uzyskać bardziej szczegółowe komunikaty o błędach, a następnie ponownie sprawdź wcześniejszych krokach.
