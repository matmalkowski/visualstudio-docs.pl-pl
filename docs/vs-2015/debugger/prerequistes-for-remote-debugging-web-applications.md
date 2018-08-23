---
title: Wstępne wymagania zdalne debugowanie aplikacji sieci Web | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications, remote servers
- remote debugging, prerequisites
- remote servers, debugging Web applications
ms.assetid: 1cd777b5-6d20-4ca6-a0df-51653b118469
caps.latest.revision: 30
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 197a6e9b433173f1de13e3506db79e7edf53bade
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42682456"
---
# <a name="prerequistes-for-remote-debugging-web-applications"></a>Wstępne wymagania debugowania zdalnego aplikacji internetowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [wymagania wstępne dla zdalnego debugowania aplikacji sieci Web](https://docs.microsoft.com/visualstudio/debugger/prerequistes-for-remote-debugging-web-applications).  
  
Za pomocą [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] debugera można debugować aplikacji sieci Web w sposób niewidoczny dla użytkownika na komputerze lokalnym lub zdalnym serwerem. To oznacza, że funkcje debugera taki sam sposób i umożliwia korzystanie z tej samej funkcji na komputerze. Zdalne debugowanie działało poprawnie, istnieją pewne wymagania wstępne.  
  
-   [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] składniki zdalnego debugowania musi być zainstalowany na serwerze, który chcesz debugować. Aby uzyskać więcej informacji, zobacz [ustawienie zapasowej zdalne debugowanie](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).  
  
-   Domyślnie [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] proces roboczy, który jest uruchamiany jako proces użytkownika ASPNET. W rezultacie, musi mieć uprawnienia administratora na komputerze, gdzie [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] przebiegów, aby go debugować. Nazwa [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] procesu roboczego zależy od scenariusz debugowania i wersję usług IIS. Aby uzyskać więcej informacji, zobacz [porady: znajdowanie nazwy procesu ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji ASP.NET i AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Wymagania systemowe](../debugger/aspnet-debugging-system-requirements.md)



