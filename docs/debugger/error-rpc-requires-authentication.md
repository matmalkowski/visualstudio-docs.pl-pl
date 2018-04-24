---
title: 'Błąd: RPC wymaga uwierzytelnienia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.rpc_requires_authentication
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 214dafa5acc925434cf3569570f20ab7f3331bfb
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="error-rpc-requires-authentication"></a>Błąd: RPC wymaga uwierzytelnienia
Debuger programu Visual Studio nie może połączyć się z komputerem zdalnym. Zasady RPC jest włączona na komputerze lokalnym, który uniemożliwia zdalne debugowanie.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Uruchom `\` *windir*`\system32\regedt32.exe`  
  
2.  Zlokalizuj i Usuń `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`.  
  
3.  Dlatego rejestru zmiana zacznie obowiązywać, należy ponownie uruchomić komputer.  
  
4.  Jeśli problem będzie się powtarzać, skontaktuj się z administratorem domeny o **Konfiguracja komputera > Szablony administracyjne > System > zdalne wywołanie procedury > ograniczenia dla nieuwierzytelnionych klientów RPC** zasady grupy ustawienie.