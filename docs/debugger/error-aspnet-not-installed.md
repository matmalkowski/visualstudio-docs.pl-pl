---
title: "Błąd: ASP.NET nie jest zainstalowany | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- aspnet
ms.openlocfilehash: 36930db142821b11ed83edf846ccd3f65fd81d1d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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