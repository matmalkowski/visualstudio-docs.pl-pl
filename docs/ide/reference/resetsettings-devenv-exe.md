---
title: -ResetSettings (devenv.exe) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 22dd925755e996a927664e0a9a5846fc10247882
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)
Przywraca [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ustawienia domyślne i automatycznie uruchamia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Opcjonalnie resetuje ustawienia do pliku określonego .vssettings.  
  
 Ustawienia domyślne są określane przez profil, który zostało zaznaczone, gdy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] najpierw została uruchomiona.  
  
## <a name="syntax"></a>Składnia  
  
```  
Devenv /ResetSettings SettingsFile  
```  
  
## <a name="arguments"></a>Argumenty  
 `SettingsFile`  
 Pełna ścieżka i nazwa pliku .vssettings do zastosowania do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Aby przywrócić profilu ogólne ustawienia środowiska deweloperskiego, należy użyć `General`.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli nie `SettingsFile` jest określony, pojawi się monit wybierz domyślną kolekcję ustawień przy następnym uruchomieniu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="example"></a>Przykład  
 Następujące polecenie w wierszu stosuje ustawienia przechowywane w pliku `MySettings.vssettings`.  
  
```  
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)   
 [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)