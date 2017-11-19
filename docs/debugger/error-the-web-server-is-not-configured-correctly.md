---
title: "Błąd: Serwer sieci web nie jest skonfigurowany poprawnie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 09/20/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.remote.projnotconfigured
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: debugger, Web application errors
ms.assetid: 875ba87f-c372-4126-8fe3-e33931cf26c0
caps.latest.revision: "22"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e0538693a815cf9749b3cd9df007486de1af3637
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>Błąd: Serwer sieci Web nie jest prawidłowo skonfigurowany

Po wykonaniu kroków szczegółowe tutaj, aby rozwiązać ten problem, a przed podjęciem ponownej próby debugowania również może być konieczne zresetowanie usług IIS. Możesz to zrobić Otwieranie wiersza polecenia z uprawnieniami administratora i wpisując `iisreset`.

Wykonaj następujące kroki, aby rozwiązać ten problem:

1. Jeśli aplikacja sieci web znajdujących się na serwerze jest skonfigurowany jako kompilację wersji ponownie opublikować jako kompilację debugowania i sprawdź, czy plik web.config zawiera `debug=true` w elemencie kompilacji. Resetowanie usług IIS i spróbuj ponownie.

    Na przykład jeśli używasz profilu publikowania do kompilacji wydania, zmień ją na debugowanie i ponownie opublikować. W przeciwnym razie ustawiono atrybut debugowania `false` po opublikowaniu.

2. (IIS) Sprawdź poprawność ścieżki fizycznej. W usługach IIS, możesz znaleźć tego ustawienia w **podstawowe ustawienia > Ścieżka fizyczna** (lub **Zaawansowane ustawienia** w starszych wersjach usług IIS).

    Jeśli aplikacja sieci web został skopiowany do innej maszyny, ręcznie przeniesiony lub ścieżka fizyczna może być niepoprawny. Resetowanie usług IIS i spróbuj ponownie.

3. W programie Visual Studio Sprawdź, czy właściwym serwerem jest wybrane we właściwościach. (Otwórz **właściwości > sieci Web > serwery** lub **właściwości > debugowanie** zależnie od typu projektu. W projekcie formularzy sieci Web otwórz **strony właściwości > opcje Start > serwer**).

    Jeśli używasz zewnętrznego serwera (niestandardowy), takich jak IIS, adres URL musi być prawidłowy. W przeciwnym razie wybierz usług IIS Express i spróbuj ponownie.

4. (IIS) Upewnij się, że na serwerze zainstalowano poprawną wersję platformy ASP.NET.

    Niezgodne wersje platformy ASP.NET w usługach IIS i projektu programu Visual Studio może być przyczyną tego problemu. Konieczne może być ustawiona wersja programu w pliku web.config. Aby zainstalować program ASP.NET w usługach IIS, należy użyć [Instalatora platformy sieci Web (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). Zobacz też [IIS 8.0 przy użyciu programu ASP.NET 3.5 i ASP.NET 4.5](https://docs.microsoft.com/en-us/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) lub dla platformy ASP.NET Core [hosta w systemie Windows z programem IIS](https://docs.asp.net/en/latest/publishing/iis.html).
  
4. Jeśli `maxConnection` limit w usługach IIS jest zbyt niski i ma zbyt wiele połączeń, konieczne może być [Zwiększ limit połączeń](https://docs.microsoft.com/en-us/iis/configuration/system.applicationhost/sites/sitedefaults/limits).
  
## <a name="see-also"></a>Zobacz też  
 [Zdalne debugowanie ASP.NET na komputerze zdalnym usług IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)   
 [Debugowanie aplikacji sieci Web: Błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)