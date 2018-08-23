---
title: 'DA0002: Brakuje VSPerfCorProf.dll | Dokumentacja firmy Microsoft'
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
- vs.performance.DA0002
- vs.performance.2
- vs.performance.rules.DAVsPerfCorProfMissing
- vs.performance.rules.DA0002
ms.assetid: 76e614b3-ad7e-4b92-b7be-88dc1329be1d
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 54c43143fae898b5a8177d4710bd335e2b8919f2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42680422"
---
# <a name="da0002-vsperfcorprofdll-is-missing"></a>DA0002: brakuje VSPerfCorProf.dll
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [DA0002: brakuje VSPerfCorProf.dll](https://docs.microsoft.com/visualstudio/profiling/da0002-vsperfcorprof-dll-is-missing).  
  
Identyfikator reguły | DA0002 |  
| Kategoria | Profilowanie użycia narzędzia |  
| Profilowanie metody | Profilowanie przy użyciu narzędzia wiersza polecenia narzędzia VSPerfCmd i VSPerfASPNETCmd |  
| Komunikat | Wydaje się, że plik został zebrany bez odpowiedniego ustawienia zmiennych środowiskowych poleceniem VSPerfCLREnv.cmd. Symbole dla zarządzanych danych binarnych mogą nie być rozpoznawane. |  
| Typ reguły | Informacji |  
  
## <a name="cause"></a>Przyczyna  
 Program profilujący nie może odnaleźć VSPerfCorProf.dll podczas uruchomienia profilowania. To ostrzeżenie występuje, gdy są używane narzędzia wiersza polecenia do zbierania danych profilera, bez użycia narzędzia VSPerfCLREnv.cmd, aby zainicjować zmienne środowiskowe wymagane. Ostrzeżenie można również uruchamiają się, jeśli inny profiler jest uruchomiona, gdy start Profiling Tools.  
  
## <a name="rule-description"></a>Opis reguły  
 Przed uruchomienie profilowania profiler można rozpoznać symboli w plikach binarnych w .NET Framework, należy ustawić określonych zmiennych środowiskowych. To ostrzeżenie sugeruje narzędzia VSPerfCLREnv.cmd nie zostało uruchomione przed zbierania danych profilowania. Symbole dla zarządzanych danych binarnych nie może rozpoznać. Aby uzyskać więcej informacji o korzystaniu z narzędzi profilowania z wiersza polecenia, zobacz [profilowania z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Jeśli profilowany zarządzanych aplikacji za pomocą narzędzia wiersza polecenia w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Profiling Tools, uruchom [VSPerfCLREnv](../profiling/vsperfclrenv.md) narzędzie wiersza polecenia, przed rozpoczęciem zbierania danych.



