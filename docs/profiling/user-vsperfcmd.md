---
title: Użytkownik (VSPerfCmd) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: ee1a478e-374d-4f30-ae28-d260b9d4723a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 128fe1f59cc652d0879e346689c9e84f1c1d9e82
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2018
---
# <a name="user-vsperfcmd"></a>Użytkownik (VSPerfCmd)
**Użytkownika** opcja określa nazwę domeny i nazwę konta, który jest właścicielem PROFILOWANEGO procesu. Ta opcja jest wymagana tylko wtedy, gdy proces jest uruchomiony jako użytkownik innego niż zalogowanego użytkownika. Właściciel procesu w kolumnie Nazwa użytkownika jest wyświetlany na **procesów** kartę Menedżera zadań systemu Windows.  
  
 **Użytkownika** opcji można określić tylko w wierszu polecenia, który zawiera także **Start** opcji.  
  
## <a name="syntax"></a>Składnia  
  
```cmd  
VSPerfCmd.exe /Start:Method /Output:FileName /User:[Domain\]UserName [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 `Domain`  
 Nazwa użytkownika domeny.  
  
 `UserName`  
 Nazwa użytkownika.  
  
## <a name="required-options"></a>Wymagane opcje  
 **Użytkownika** opcja może być używana tylko z **Start** opcji.  
  
 **Uruchom:** `Method`  
 Inicjuje profilera do określonej metody profilowania.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano użycie **użytkownika** opcji.  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /User:SYSTEM  
```  
  
## <a name="see-also"></a>Zobacz także  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)