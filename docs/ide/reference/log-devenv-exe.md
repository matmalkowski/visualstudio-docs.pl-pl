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
ms.openlocfilehash: cf5ab0e1949716005d12d51d06b0d915344833aa
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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