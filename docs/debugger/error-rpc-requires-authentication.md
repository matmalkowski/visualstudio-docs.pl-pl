---
title: "Błąd: RPC wymaga uwierzytelnienia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vs.debug.error.rpc_requires_authentication
dev_langs:
- CSharp
- VB
- FSharp
- C++
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 73cd474d415a49b6dd9075559d8618289b1b0d21
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="error-rpc-requires-authentication"></a>Błąd: RPC wymaga uwierzytelnienia
Debuger programu Visual Studio nie może połączyć się z komputerem zdalnym. Zasady RPC jest włączona na komputerze lokalnym, który uniemożliwia zdalne debugowanie.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Uruchom `\` *windir*`\system32\regedt32.exe`  
  
2.  Zlokalizuj i Usuń `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`.  
  
3.  Dlatego rejestru zmiana zacznie obowiązywać, należy ponownie uruchomić komputer.  
  
4.  Jeśli problem będzie się powtarzać, skontaktuj się z administratorem domeny o **Konfiguracja komputera > Szablony administracyjne > System > zdalne wywołanie procedury > ograniczenia dla nieuwierzytelnionych klientów RPC** zasady grupy ustawienie.