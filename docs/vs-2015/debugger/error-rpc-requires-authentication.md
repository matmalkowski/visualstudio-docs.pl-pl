---
title: 'Błąd: RPC wymaga uwierzytelnienia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.rpc_requires_authentication
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 88362b3b-8fbe-431f-96a4-80e2d822bbc7
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e606c0e730b279723248a3fdbdd5b3e2bca1c4a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42696651"
---
# <a name="error-rpc-requires-authentication"></a>Błąd: RPC wymaga uwierzytelnienia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [błąd: RPC wymaga uwierzytelnienia](https://docs.microsoft.com/visualstudio/debugger/error-rpc-requires-authentication).  
  
Debuger programu Visual Studio nie może połączyć się z komputerem zdalnym. Na komputerze lokalnym, która uniemożliwia zdalne debugowanie jest włączona zasada rcp.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Uruchom `\` *windir*`\system32\regedt32.exe`  
  
2.  Zlokalizuj i Usuń `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`.  
  
3.  Aby zmiany w rejestrze zostaną wprowadzone, uruchom ponownie komputer.  
  
4.  Jeśli problem będzie się powtarzać, skontaktuj się z administratorem domeny o **Konfiguracja komputera -> Szablony administracyjne - > System -> zdalnego wywołania procedury -> ograniczenia dotyczące nieuwierzytelnionych klientów RPC** grupy ustawienia zasad.



