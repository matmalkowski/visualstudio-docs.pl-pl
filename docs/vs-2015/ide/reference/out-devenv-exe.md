---
title: -Out (devenv.exe) | Dokumentacja firmy Microsoft
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
- errors [Visual Studio], builds
- Devenv, /out switch
- builds [Visual Studio], logs
- error logs [Visual Studio], command-line build errors
- error logs [Visual Studio]
- /out Devenv switch
- out Devenv switch
- builds [Visual Studio], errors
- output files, build errors
ms.assetid: 9002d8c2-36d4-451c-b489-8f01932f31f7
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4edcdf6da73c3f4c4ee9d221d7bbaef8e520c5e3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42679675"
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [-Out (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/out-devenv-exe).  
  
  
Określa plik do przechowywania i wyświetlania błędów podczas uruchamiania, tworzenia, odbudować lub wdrożyć rozwiązanie.  
  
## <a name="syntax"></a>Składnia  
  
```  
devenv /out FileName  
```  
  
## <a name="arguments"></a>Argumenty  
 `FileName`  
 Wymagane. Ścieżka i nazwa pliku, aby otrzymywać komunikaty o błędach podczas kompilowania pliku wykonywalnego.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli określono nazwę pliku, który nie istnieje, plik zostanie utworzony automatycznie. Jeśli plik już istnieje, wyniki są dołączane do istniejącej zawartości pliku.  
  
 Błędy kompilacji wiersza polecenia są wyświetlane w **polecenia** okna i konstruktora rozwiązania widoku **dane wyjściowe** okna. Ta opcja jest przydatna, jeśli działają nienadzorowanej kompilacji i chcesz zobaczyć wyniki.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie jest uruchamiany `MySolution` i zapisuje błędy do pliku `MyErrorLog.txt`.  
  
```  
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [/ Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)   
 [/ Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/ Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/ Wdrażanie (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)



