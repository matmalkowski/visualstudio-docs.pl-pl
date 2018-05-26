---
title: Wdrażanie na folder lokalny
description: Wdrażanie aplikacji na folder lokalny
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: bd477fec033eb75f626401586abfd10c798601ef
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2018
---
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **publikowania** (formularzy sieci Web **publikowania aplikacji sieci Web**).

    Jeśli wcześniej skonfigurowano żadnych profilów publikowania, **publikowania** pojawi się okienko. Kliknij przycisk **nowy profil**.

1. W **publikowania** okno dialogowe, wybierz opcję **folderu**, kliknij przycisk **Przeglądaj**i Utwórz nowy folder **C:\Publish**.

    ![RemoteDBG_Publish_Local](../media/remotedbg_publish_local.png "RemoteDBG_Publish_Local")

    W przypadku aplikacji formularzy sieci Web wybierz **niestandardowy** w oknie dialogowym Publikowanie, wprowadź nazwę profilu, a następnie wybierz pozycję **OK**.

1. Kliknij przycisk **Utwórz profil** na liście rozwijanej (**publikowania** jest wartością domyślną).

1. W **publikowania** okno dialogowe, kliknij przycisk **ustawienia** łącza, a następnie wybierz **ustawienia** kartę.

1. Ustaw dla konfiguracji **debugowania**, wybierz pozycję **Usuń wszystkie istniejące pliki przez opublikowaniem**, a następnie kliknij przycisk **zapisać**.

    > [!NOTE]
    > Jeśli używasz kompilacji wydania wyłączeniu debugowania w pliku web.config podczas publikowania.

1. Kliknij przycisk **publikowania**.

    ![RemoteDBG_Publish_Debug_Config](../media/remotedbg_publish_debug_config.png "RemoteDBG_Publish_Debug_Config")
    
    Publikowanie aplikacji **debugowania** konfiguracji projektu do folderu lokalnego. Przedstawia postęp w oknie danych wyjściowych.

1. Skopiuj katalog projektu ASP.NET z komputera programu Visual Studio do katalogu lokalnego skonfigurowane dla aplikacji ASP.NET (w tym przykładzie **C:\Publish**) na komputerze z systemem Windows Server. W tym samouczku przyjęto założenie, kopiowane są ręcznie, ale można użyć innych narzędzi, takich jak programu PowerShell, Xcopy lub Robocopy.

    > [!CAUTION]
    >  Jeśli chcesz dokonać zmian kodu lub skompiluj ponownie, należy ponownie opublikować i powtórz ten krok. Plik wykonywalny skopiowane na komputer zdalny musi dokładnie odpowiadać lokalnego źródłowe i symboli.    Jeśli tego nie zrobi to otrzymasz `cannot find or open the PDB file` ostrzeżenie w programie Visual Studio, gdy próbują debugowanie tego procesu.

1. W systemie Windows Server Sprawdź, że aplikację można uruchomić poprawnie, otwierając aplikację w przeglądarce.

    Jeśli aplikacja nie działa prawidłowo, może być niezgodność między wersji platformy ASP.NET zainstalowanej na serwerze i komputerze Visual Studio lub może wystąpić problem z konfiguracją usług IIS lub witryny sieci Web. Ponownie sprawdź wcześniejszych krokach.
