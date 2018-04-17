---
title: 'DA0002: Brakuje VSPerfCorProf.dll | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0002
- vs.performance.2
- vs.performance.rules.DAVsPerfCorProfMissing
- vs.performance.rules.DA0002
ms.assetid: 76e614b3-ad7e-4b92-b7be-88dc1329be1d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9f0e1b87a4fb5232a949c2ec4f4c9d32594b3fb8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="da0002-vsperfcorprofdll-is-missing"></a>DA0002: brakuje VSPerfCorProf.dll
|||  
|-|-|  
|Identyfikator reguły|DA0002|  
|Kategoria|Użycie narzędzia profilowania|  
|Metod profilowania|Profilowanie przy użyciu narzędzia wiersza polecenia VSPerfCmd i VSPerfASPNETCmd|  
|Komunikat|Wygląda na to, że plik został zebrany bez odpowiedniego ustawienia zmiennych środowiskowych poleceniem VSPerfCLREnv.cmd. Symbole dla zarządzanych danych binarnych mogą nie być rozpoznawane.|  
|Typ reguły|Informacje|  
  
## <a name="cause"></a>Przyczyna  
 Profiler nie można odnaleźć VSPerfCorProf.dll podczas przebiegu profilowania. To ostrzeżenie występuje, gdy są używane narzędzia wiersza polecenia do zbierania danych profilera, bez użycia narzędzia VSPerfCLREnv.cmd zainicjować zmienne środowiskowe niezbędne. To ostrzeżenie można również wyzwalana, gdy inny profiler jest uruchomiona po uruchomieniu narzędzia profilowania.  
  
## <a name="rule-description"></a>Opis reguły  
 Przed uruchomienie profilowania profiler do rozpoznawania symboli w plikach binarnych .NET Framework należy ustawić zmienne w danym środowisku. To ostrzeżenie sugeruje narzędzia VSPerfCLREnv.cmd nie zostało uruchomione przed zebrano dane profilowania. Symbole dla zarządzanych danych binarnych nie może rozpoznać. Aby uzyskać więcej informacji dotyczących korzystania z narzędzi profilowania z wiersza polecenia, zobacz [profilowania z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Gdy są profilowanie aplikacji zarządzanych za pomocą narzędzia wiersza polecenia w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzi profilowania, uruchom [VSPerfCLREnv](../profiling/vsperfclrenv.md) narzędzia wiersza polecenia przed rozpoczęciem zbierania danych.