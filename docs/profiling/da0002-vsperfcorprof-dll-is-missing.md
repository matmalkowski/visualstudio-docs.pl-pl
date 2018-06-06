---
title: 'DA0002: Brakuje VSPerfCorProf.dll | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: cc0207a529fe74e23e6b1b032c1eb6919cf38592
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34749310"
---
# <a name="da0002-vsperfcorprofdll-is-missing"></a>DA0002: brakuje VSPerfCorProf.dll
|||  
|-|-|  
|Identyfikator reguły|DA0002|  
|Kategoria|Użycie narzędzia profilowania|  
|Metod profilowania|Profilowanie przy użyciu narzędzia wiersza polecenia VSPerfCmd i VSPerfASPNETCmd|  
|Komunikat|Wygląda na to, że plik został zebrany bez odpowiedniego ustawienia zmiennych środowiskowych poleceniem *VSPerfCLREnv.cmd*. Symbole dla zarządzanych danych binarnych mogą nie być rozpoznawane.|  
|Typ reguły|Informacje|  
  
## <a name="cause"></a>Przyczyna  
 Nie można odnaleźć profilera *VSPerfCorProf.dll* podczas przebiegu profilowania. To ostrzeżenie występuje, gdy są używane narzędzia wiersza polecenia do zbierania danych profilera, bez korzystania z *VSPerfCLREnv.cmd* narzędzia, aby zainicjować zmienne środowiskowe to konieczne. To ostrzeżenie można również wyzwalana, gdy inny profiler jest uruchomiona po uruchomieniu narzędzia profilowania.  
  
## <a name="rule-description"></a>Opis reguły  
 Przed uruchomienie profilowania profiler do rozpoznawania symboli w plikach binarnych .NET Framework należy ustawić zmienne w danym środowisku. Sugeruje to ostrzeżenie, że *VSPerfCLREnv.cmd* przed zebrano dane profilowania nie zostało uruchomione narzędzie. Symbole dla zarządzanych danych binarnych nie może rozpoznać. Aby uzyskać więcej informacji dotyczących korzystania z narzędzi profilowania z wiersza polecenia, zobacz [profilowania z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)  
  
## <a name="how-to-fix-violations"></a>Jak rozwiązać naruszeń  
 Gdy są profilowanie aplikacji zarządzanych za pomocą narzędzia wiersza polecenia w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzi profilowania, uruchom [VSPerfCLREnv](../profiling/vsperfclrenv.md) narzędzia wiersza polecenia przed rozpoczęciem zbierania danych.