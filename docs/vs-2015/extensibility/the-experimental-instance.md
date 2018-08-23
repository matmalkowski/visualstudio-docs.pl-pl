---
title: Wystąpienie eksperymentalne | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
caps.latest.revision: 37
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3d819be41806e075de23dbfb5b5b3cded5bbeb40
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42679051"
---
# <a name="the-experimental-instance"></a>Wystąpienie eksperymentalne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [wystąpienie doświadczalne](https://docs.microsoft.com/visualstudio/extensibility/the-experimental-instance).  
  
Zabezpieczenie środowiska deweloperskiego Visual Studio z nieprzetestowanych aplikacji, które może go zmienić, VSSDK miejsce eksperymentalne używanego do eksperymentowania. Twórz nowe aplikacje za pomocą programu Visual Studio w zwykły sposób, ale można je uruchamiać przy użyciu tego wystąpienie eksperymentalne.  
  
 Każda aplikacja, która zawiera pakiet VSIX uruchamia wystąpienie eksperymentalne programu Visual Studio w trybie debugowania.  
  
 Jeśli chcesz uruchomić doświadczalne wystąpienie programu Visual Studio poza konkretnego rozwiązania, uruchom następujące polecenie w oknie wiersza polecenia:  
  
 "*\<Ścieżka instalacji programu visual studio >* \Common7\IDE\devenv.exe" RootSuffix Exp  
  
> [!NOTE]
>  Wystąpienie eksperymentalne są zapisywane w kluczu rejestru `<version number>Exp` i `<version number>Exp_Config` węzłów. Na przykład jest obszar rejestru eksperymentalne programu Visual Studio 2015  
>   
>  `HKCU\Software\Microsoft\VisualStudio\14.0Exp` i `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`  
  
 Firma Microsoft zaleca uruchomienie Twojego rozszerzenia w doświadczalnym wystąpieniu podczas jej opracowywania. Podczas wdrażania rozszerzenia, jest uruchamiane w wystąpieniu rozwoju. Aby uzyskać więcej informacji na temat rejestrowania aplikacji, zobacz [rejestrowanie pakietów VSPackage](../extensibility/internals/registering-vspackages.md).

