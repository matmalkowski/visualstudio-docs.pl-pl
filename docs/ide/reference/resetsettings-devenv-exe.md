---
title: -ResetSettings (devenv.exe) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 52d01cfc3ae6a453330c2dda5da137f449ff5cbd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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