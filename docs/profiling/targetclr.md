---
title: TargetCLR | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5f8ea5bd3f1ec16f6deeae8365cc90541bc8b958
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2018
---
# <a name="targetclr"></a>TargetCLR
**TargetCLR** opcji określa wersję wspólnego języka środowiska wykonawczego (języka wspólnego CLR) do profilu po załadowaniu więcej niż jedną wersję środowiska CLR w aplikacji.  
  
 Domyślnie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] profilowania narzędzia target pierwszej wersji środowiska CLR, który jest ładowany przez aplikację.  
  
## <a name="syntax"></a>Składnia  
  
```cmd  
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]   
```  
  
#### <a name="parameters"></a>Parametry  
 `ClrVersion`  
 Numer wersji środowiska CLR. Użyj formatu wersji **vN.N.NNNNN**.  
  
## <a name="required-options"></a>Wymagane opcje  
 **TargetCLR** opcja może być używana tylko z **uruchamianie** lub **Attach** opcje.  
  
 **Uruchom:** `AppName`  
 Uruchamia określonej aplikacji i uruchamia do profilu.  
  
 **Dołącz:** `PID`  
 Uruchamia profilowanie określony proces.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie opcja TargetCLR służy do upewnij się, że jest profilowane CLR w wersji 4.0.11003.  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003  
```