---
title: Pobieranie zdalnego debugera
description: Łącza pobierania dla zdalnego debugera
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: a9867acf2a0877322b85d25c3af781ccfdd3f58c
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44343183"
---
1.  Na urządzeniu lub serwera maszyny, które chcesz debugować (a nie komputer z programem Visual Studio) Pobierz poprawną wersję narzędzi remote tools.

    |Wersja|Łącze|Uwagi|
    |-|-|-|
    |Visual Studio 2017 (Najnowsza wersja)|[Zdalne narzędzia](https://visualstudio.microsoft.com/downloads/?q=remote+tools#remote-tools-for-visual-studio-2017)|Najnowszą wersję narzędzi remote tools jest zgodny z wszystkimi wersjami programu Visual Studio 2017. Zawsze pobierana wersja dopasowania system operacyjny urządzenia (x 86, x64 lub ARM64). W systemie Windows Server, zobacz [odblokować pobierania pliku](../../debugger/remote-debugging-unblock-file-download.md) Aby uzyskać pomoc pobrać narzędzia remote tools.|
    |Visual Studio 2015|[Zdalne narzędzia](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Zdalne narzędzia dla programu Visual Studio 2015 są dostępne z My.VisualStudio.com. Jeśli zostanie wyświetlony monit, weź udział w bezpłatnych [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) program lub zaloguj się przy użyciu identyfikatora subskrypcji programu Visual Studio. W systemie Windows Server, zobacz [odblokować pobierania pliku](../../debugger/remote-debugging-unblock-file-download.md) Aby uzyskać pomoc pobrać narzędzia remote tools.|
    |Visual Studio 2013|[Zdalne narzędzia](/previous-versions/visualstudio/visual-studio-2013/bt727f1t(v=vs.120)#Installing_the_Remote_Tools)|Pobierz strony w dokumentacji programu Visual Studio 2013|
    |Visual Studio 2012|[Zdalne narzędzia](/previous-versions/visualstudio/visual-studio-2012/bt727f1t(v=vs.110)#BKMK_Installing_the_Remote_Tools)|Pobierz strony w dokumentacji programu Visual Studio 2012|

2.  Na stronie pobierania wybierz wersję narzędzi, który pasuje do systemu operacyjnego (x86, x64, ARM i ARM64), a następnie Pobierz narzędzia remote tools.

    > [!IMPORTANT]
    >  Firma Microsoft zaleca, zainstalować najnowszą wersję narzędzi remote tools dla używanej wersji programu Visual Studio. Najnowsza wersja (na przykład 15.8) jest zgodna z wcześniejszymi wersjami produktów (na przykład 15.0); Jednak wcześniejsze wersje nie są zgodne z nowszych wersji. Ponadto należy zainstalować narzędzi zdalnych, które mają taką samą architekturę co system operacyjny, na którym chcesz go zainstalować. Innymi słowy Jeśli chcesz debugować 32-bitowej aplikacji na komputerze zdalnym z systemem 64-bitowym systemie operacyjnym, należy zainstalować 64-bitowej wersji narzędzi zdalnych na komputerze zdalnym.
    >
    >  Debugowanie w systemie Windows 10 na urządzeniach ARM, wybierz opcję Pobierz ARM64 dostępnych z najnowszą wersją narzędzi zdalnych.  Dla urządzeń z systemem Windows RT należy wybrać wersji ARM, która jest dostępna tylko w przypadku pobierania programu Visual Studio 2015 w wersji RTW.

3.  Po zakończeniu pobierania pliku wykonywalnego, przejdź do następnej sekcji, a następnie postępuj zgodnie z instrukcjami instalacji.

Próby skopiuj zdalny debuger (msvsmon.exe) z komputerem zdalnym i uruchom go, należy pamiętać, że **Kreatora konfiguracji zdalnego debugera** (**rdbgwiz.exe**) jest zainstalowana tylko wtedy, gdy możesz pobrać narzędzia. Konieczne może być za pomocą Kreatora konfiguracji później, zwłaszcza, jeśli chcesz, aby zdalnego debugera, aby uruchomić jako usługę. Aby uzyskać więcej informacji, zobacz [(opcjonalnie) Konfigurowanie debugera zdalnego jako usługę](../../debugger/remote-debugging.md#bkmk_configureService).
