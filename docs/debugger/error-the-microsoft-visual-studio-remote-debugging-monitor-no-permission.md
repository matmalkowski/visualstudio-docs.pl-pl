---
title: 'Błąd: Program Microsoft Visual Studio Monitor debugera zdalnego na komputerze zdalnym nie ma uprawnień do połączenia z tym komputerem | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.error.access_denied_oncallback
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, Windows version error
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 266a301bca4953066621d759518c1754052dfeb2
ms.sourcegitcommit: eefffa7ebe339d1297cdc12f51a813e7849d7e95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
ms.locfileid: "34177972"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-does-not-have-permission-to-connect-to-this-computer"></a>Błąd: Monitor debugera zdalnego Microsoft Visual Studio na komputerze zdalnym nie ma uprawnień do połączenia z tym komputerem
Ten błąd występuje, gdy użytkownik, który próbuje uruchomić program Visual Studio Monitor debugera zdalnego (polecenie msvsmon) nie ma konta na komputerze lokalnym.  
  
### <a name="to-fix-this-problem"></a>Aby rozwiązać ten problem  
  
-   Dodaj konto użytkownika do komputera hosta debugera programu Visual Studio, z taką samą nazwę i hasło jako konto użytkownika uruchamiającego polecenie msvsmon na komputerze zdalnym  
  
     \- lub -  
  
-   Uruchom polecenie msvsmon jako użytkownik, który ma uprawnienia do wywoływania na komputerze lokalnym. Oznacza to, że użytkownik musi być użytkownikiem domeny oraz administratorem komputera polecenia msvsmon. Możesz określić konto użytkownika, aby uruchomić polecenie msvsmon w jeden z dwóch sposobów:  
  
    -   Kliknij prawym przyciskiem myszy ikonę polecenia msvsmon i wybierz polecenie **Uruchom jako** menu skrótów  
  
     \- lub -  
  
    -   W wierszu polecenia Uruchom `runas.exe`.  
  
## <a name="see-also"></a>Zobacz też  
 [Zdalne debugowanie błędów i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Debugowanie zdalne](../debugger/remote-debugging.md)