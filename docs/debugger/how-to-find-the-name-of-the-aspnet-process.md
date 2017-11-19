---
title: 'Porady: znajdowanie nazwy procesu ASP.NET | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ASP.NET debugging, ASP.NET process
- ASP.NET process
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
caps.latest.revision: "29"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 03ae4956f0e16a4fb9267266ebc6b6c335c95eac
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-find-the-name-of-the-aspnet-process"></a>Porada: Znajdowanie nazwy procesu ASP.NET
Aby dołączyć do uruchomionej [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji, musisz znać nazwę [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces:  

-   Jeśli używasz platformy ASP.NET Core dla usług IIS lub programu IISExpress, nazwa procesu jest dotnet.exe.

-   Jeśli później jest uruchomiony program ASP.NET w usługach IIS 6.0, nazwa jest w3wp.exe.  
  
-   Jeśli korzystasz z programu ASP.NET we wcześniejszej wersji programu IIS, nazwa jest aspnet_wp.exe.

-   Jeśli używasz programu IISExpress ASP.NET, nazwa jest iisexpress.exe.
  
Dla aplikacji tworzonych przy użyciu wersji programu Visual Studio przed programu Visual Studio 2012 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] kod może znajdować się w systemie plików i działać na serwerze testowym WebDev.WebServer.exe lub WebDev.WebServer40.exe. W takim przypadku należy dołączyć do WebDev.WebServer.exe lub WebDev.WebServer40.exe zamiast [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu. Ten scenariusz dotyczy tylko do debugowania lokalnego.
  
Starsze aplikacje ASP uruchamiane wewnątrz inetinfo.exe proces usług IIS działające w procesie.  

### <a name="to-determine-the-iis-version-under-which-the-application-is-running"></a>Aby określić wersji usług IIS, na którym uruchomiono aplikację  

1.  Upewnij się, że aplikacja jest uruchomiona, a następnie w programie Visual Studio za pomocą [dołączyć do procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) polecenia.

2.  Wpisz pierwszą literę nazwę procesu, takie jak w3wp.exe można szybko znaleźć procesów w **dostępne procesy** listy.

    Dostępne procesy z listy, w tym temacie poinformuje o wersjach programu IIS są dostępne, a które proces jest uruchomiona aplikacja.

    > [!NOTE]
    > Począwszy od programu Visual Studio 2017 r, można użyć pola wyszukiwania do Wyszukaj nazwę procesu.
  
## <a name="see-also"></a>Zobacz też  
 [Dołączanie do uruchomionego procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)  
 [Wstępne wymagania debugowania zdalnego aplikacji sieci Web](../debugger/prerequistes-for-remote-debugging-web-applications.md)   
 [Wymagania systemowe](../debugger/aspnet-debugging-system-requirements.md)   
 [Debugowanie aplikacji ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)