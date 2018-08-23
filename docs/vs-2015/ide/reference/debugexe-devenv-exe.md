---
title: -DebugExe (devenv.exe) | Dokumentacja firmy Microsoft
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
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f58db37f353cddd7444e7ea185dc07c0ec6cd603
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42633487"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [- DebugExe (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/debugexe-devenv-exe).  
  
  
Otwiera określony plik wykonywalny do zdebugowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
Devenv /debugexe ExecutableFile  
```  
  
## <a name="arguments"></a>Argumenty  
 `ExecutableFile`  
 Wymagane. Ścieżka i nazwa pliku .exe.  
  
 Jeśli plik .exe nie zostanie znaleziony lub nie istnieje, jest wyświetlana nie ostrzeżenia lub błędu i [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] uruchamia się normalnie.  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie ciągi zgodnie z `ExecutableFile` parametru są przekazywane do tego pliku jako argumenty.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie otwierany plik `MyApplication.exe` do debugowania.  
  
```  
Devenv.exe /debugexe MyApplication.exe  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)



