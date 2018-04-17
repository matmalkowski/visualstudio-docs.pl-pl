---
title: -Log (devenv.exe) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8fa0fa90e904d4fb7f3e6820ce997a6a93e738f9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)
Loguje wszelką aktywność do pliku dziennika w celu rozwiązywania problemów. Ten plik jest wyświetlany po została wywołana `devenv /log` co najmniej raz. Domyślnie plik dziennika jest:  
  
 *% APPDATA %*\Microsoft\VisualStudio\\*wersji*\ActivityLog.xml  
  
 gdzie *wersji* jest wersją programu Visual Studio. Może jednak określić inną ścieżkę i nazwę.  
  
## <a name="syntax"></a>Składnia  
  
```  
Devenv /log Path\NameOfLogFile  
```  
  
## <a name="remarks"></a>Uwagi  
 Ten przełącznik musi być umieszczony na końcu wiersza polecenia po innych przełącznikach.  
  
 Dziennik jest zapisywany dla wszystkich wystąpień programu Visual Studio, która została wywołana z przełącznikiem/log. Go nie logowania wystąpienia programu Visual Studio, który został wywołany bez utworzenia przełącznika.  
  
## <a name="see-also"></a>Zobacz też  
 [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)