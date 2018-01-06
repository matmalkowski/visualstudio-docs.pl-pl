---
title: -Log (devenv.exe) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: fb84c4bab7ce9480deefbb88ac02289415f33d5d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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