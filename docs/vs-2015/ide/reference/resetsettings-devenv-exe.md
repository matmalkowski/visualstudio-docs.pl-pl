---
title: -ResetSettings (devenv.exe) | Dokumentacja firmy Microsoft
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
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 25697a792b0c48746a1d7840b8091ea718f5cdc7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42684844"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [- ResetSettings (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/resetsettings-devenv-exe).  
  
  
Przywraca [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ustawienia domyślne i automatycznie uruchamia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE. Opcjonalnie resetuje ustawienia do określonego pliku .vssettings.  
  
 Ustawienia domyślne są określane przez profil który został wybrany, gdy [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] najpierw została uruchomiona.  
  
## <a name="syntax"></a>Składnia  
  
```  
Devenv /ResetSettings SettingsFile  
```  
  
## <a name="arguments"></a>Argumenty  
 `SettingsFile`  
 Pełna ścieżka i nazwa pliku .vssettings do zastosowania do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Aby przywrócić profil ogólne ustawienia projektowe, użyj `General`.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli nie `SettingsFile` jest określona, zostanie wyświetlony monit wybór domyślnej kolekcji ustawień przy następnym uruchomieniu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="example"></a>Przykład  
 Następujący wiersz polecenia powoduje zastosowanie ustawień przechowywanych w pliku `MySettings.vssettings`.  
  
```  
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dostosowywanie ustawień środowiska deweloperskiego w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)



