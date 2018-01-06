---
title: "Błąd: Program Microsoft Visual Studio Monitor debugera zdalnego na komputerze zdalnym pracuje jako inny użytkownik | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- -anyuser option
- anyuser option
- Remote Debugging Monitor
- remote debugging, Remote Debugging Monitor
- msvsmon.exe
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f6575dc0d0a71481efff1da7808c7fbc62f94e56
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user"></a>Błąd: Monitor debugera zdalnego Microsoft Visual (MSVSMON.EXE) na komputerze zdalnym pracuje jako inny użytkownik
Podczas próby czy zdalne debugowanie, może pojawić się następujący komunikat o błędzie:  
  
 Microsoft Visual Studio Monitor debugera zdalnego na komputerze zdalnym jest uruchomiony jako inny użytkownik.  
  
## <a name="cause"></a>Przyczyna  
 Ten komunikat jest wyświetlany podczas debugowania w trybie bez uwierzytelniania i użytkownika, który uruchomił polecenie msvsmon nie jest użytkownik, który jest uruchomiony program Visual Studio.  
  
## <a name="solution"></a>Rozwiązanie  
 Najbezpieczniejszy i najlepszych rozwiązań jest uruchomienie zdalnego Monitor debugera (msvsmon.exe) dla tego samego konta użytkownika, co program Visual Studio. Jeśli nie możesz tego zrobić, można uruchomić monitora zdalnego debugowania w ramach konta z **Zezwalaj dowolnemu użytkownikowi na debugowanie** opcji wybranej w Monitor debugera zdalnego **opcje** okno dialogowe.  
  
> [!CAUTION]
>  Udzielanie uprawnień do łączenia z innych użytkowników umożliwia możliwości przypadkowe łączenie się niewłaściwy sesja debugowania zdalnego. Debugowanie w **bez uwierzytelniania** tryb nigdy nie jest bezpieczne i powinny być stosowane z rozwagą.
  
## <a name="see-also"></a>Zobacz też  
 [Zdalne debugowanie błędów i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Debugowanie zdalne](../debugger/remote-debugging.md)