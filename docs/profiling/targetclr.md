---
title: TargetCLR | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a69edb2730ff89a50dd45252258fc57e7205de3d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="targetclr"></a>TargetCLR
**TargetCLR** opcji określa wersję wspólnego języka środowiska wykonawczego (języka wspólnego CLR) do profilu po załadowaniu więcej niż jedną wersję środowiska CLR w aplikacji.  
  
 Domyślnie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] profilowania narzędzia target pierwszej wersji środowiska CLR, który jest ładowany przez aplikację.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]   
```  
  
#### <a name="parameters"></a>Parametry  
 `ClrVersion`  
 Numer wersji środowiska CLR. Użyj formatu wersji **vN.N.NNNNN**.  
  
## <a name="required-options"></a>Wymagane opcje  
 **TargetCLR** opcja może być używana tylko z **uruchamianie** lub **Attach** opcje.  
  
 **Uruchom:**`AppName`  
 Uruchamia określonej aplikacji i uruchamia do profilu.  
  
 **Dołącz:**`PID`  
 Uruchamia profilowanie określony proces.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie opcja TargetCLR służy do upewnij się, że jest profilowane CLR w wersji 4.0.11003.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003  
```