---
title: 'Błąd: ASP.NET nie jest zainstalowany | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.http_not_supported
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Web applications, errors
- debugger, Web application errors
- error messages, ASP.NET
- ASP.NET, installation error messages
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: b462c3ed02ebd622a39cd08039037b3ba63e7f57
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="error-aspnet-not-installed"></a>Błąd: ASP.NET nie jest zainstalowany
Ten błąd występuje, gdy [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] nie jest poprawnie zainstalowana na komputerze, na którym chcesz debugować. Może to oznaczać, że [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] nigdy nie został zainstalowany lub [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] najpierw zainstalować i program IIS został zainstalowany później.  
  
### <a name="to-reinstall-aspnet"></a>Aby ponownie zainstalować program ASP.NET  
  
1.  W oknie wiersza polecenia Uruchom następujące polecenie:  
  
    ```  
    \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i  
    ```  
  
     gdzie *wersji* reprezentuje numer wersji platformy .NET zainstalowany na komputerze, na przykład v1.0.370. Można określić wersji platformy, przeszukując `\WINDOWS\Microsoft.NET\Framework` katalogu.  
  
    > [!NOTE]
    >  Windows Server 2003, można zainstalować [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] za pomocą **Dodaj lub usuń programy** w Panelu sterowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji sieci Web: Błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)