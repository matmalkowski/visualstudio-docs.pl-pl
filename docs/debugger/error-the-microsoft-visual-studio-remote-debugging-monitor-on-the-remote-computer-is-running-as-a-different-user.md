---
title: "Błąd: Program Microsoft Visual Studio Monitor debugera zdalnego na komputerze zdalnym pracuje jako inny użytkownik | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
ms.assetid: e5b18734-2daf-4c58-b5de-24ae1295703e
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5f3f2c9e0b3f88734d21ae06f1af48409c58766a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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