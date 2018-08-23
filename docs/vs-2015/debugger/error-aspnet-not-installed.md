---
title: 'Błąd: ASP.NET nie jest zainstalowany | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.http_not_supported
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Web applications, errors
- debugger, Web application errors
- error messages, ASP.NET
- ASP.NET, installation error messages
ms.assetid: 6286dd3d-3e2b-4edd-959d-81e0ed45500b
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0617f5200a69809afc86fe9405dc3ea9bd8fcda0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42679246"
---
# <a name="error-aspnet-not-installed"></a>Błąd: ASP.NET nie jest zainstalowany
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [błąd: ASP.NET nie jest zainstalowany](https://docs.microsoft.com/visualstudio/debugger/error-aspnet-not-installed).  
  
Ten błąd występuje, gdy [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] nie jest poprawnie zainstalowany na komputerze, który chcesz debugować. Może to oznaczać, że [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] nigdy nie został zainstalowany lub [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] została zainstalowana jako pierwsza i IIS został zainstalowany później.  
  
### <a name="to-reinstall-aspnet"></a>Ponowna instalacja programu ASP.NET  
  
1.  Z poziomu okna wiersza polecenia Uruchom następujące polecenie:  
  
    ```  
    \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i  
    ```  
  
     gdzie *wersji* reprezentuje numer wersji .NET Framework zainstalowanej na komputerze, na przykład v1.0.370. Można określić framework w wersji, przeszukując `\WINDOWS\Microsoft.NET\Framework` katalogu.  
  
    > [!NOTE]
    >  Windows Server 2003, można zainstalować [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] przy użyciu **apletu Dodaj lub usuń programy** w Panelu sterowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji sieci Web: Błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)



