---
title: -Log (devenv.exe) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bfd6d9ac2493e4caca95538140fb9af78db8e074
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42685197"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [-Log (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/log-devenv-exe).  
  
  
Loguje wszelką aktywność do pliku dziennika w celu rozwiązywania problemów. Ten plik pojawia się, gdy została wywołana `devenv /log` co najmniej raz. Domyślnie plik dziennika to:  
  
 *% APPDATA %* \Microsoft\VisualStudio\\*wersji*\ActivityLog.XML  
  
 gdzie *wersji* jest wersja programu Visual Studio. Można jednak określić inną ścieżkę i nazwę pliku.  
  
## <a name="syntax"></a>Składnia  
  
```  
Devenv /log Path\NameOfLogFile  
```  
  
## <a name="remarks"></a>Uwagi  
 Ten przełącznik musi być umieszczony na końcu wiersza polecenia po innych przełącznikach.  
  
 Dziennik jest zapisywany dla wszystkich wystąpień programu Visual Studio, która została wywołana z przełącznikiem/log. Go nie logowania wystąpienia programu Visual Studio, który został wywołany bez przełącznika.  
  
## <a name="see-also"></a>Zobacz też  
 [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)



