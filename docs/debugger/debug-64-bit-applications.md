---
title: Debugowanie aplikacji 64-bitowych | Dokumentacja firmy Microsoft
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
helpviewer_keywords:
- debugging [Visual Studio], 64-bit
- 64-bit debugging
ms.assetid: db648e5f-6375-4e2d-aa98-eb7261958927
caps.latest.revision: "32"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5c3840cc7d43c3e30dda0317674ffb8cd664a262
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="debug-64-bit-applications"></a>Debugowanie aplikacji 64-bitowych
Można debugować aplikacji 64-bitowego, która działa na komputerze lokalnym lub zdalnym.  
  
 Debugowanie aplikacji 64-bitowego, która działa na komputerze zdalnym, zobacz [zdalnego debugowania](../debugger/remote-debugging.md).  
  
 Debugowanie aplikacji 64-bitowych lokalnie, Visual Studio będzie korzystać proces roboczy 64-bitowych (msvsmon.exe) wykonywanie operacji niskiego poziomu, których nie można wykonać wewnątrz procesu 32-bitowego programu Visual Studio.  
  
 Debugowanie w trybie mieszanym nie jest obsługiwane dla procesów 64-bitowych, które używają .NET Framework w wersji 3.5 lub starszej.  
  
## <a name="debug-a-64-bit-application"></a>Debugowanie aplikacji 64-bitowych  
 Aby wypróbować debugowanie aplikacji 64-bitowe:  
  
1.  Tworzenie rozwiązań programu Visual Studio, na przykład aplikacji konsolowej C#.  
  
2.  Ustaw konfigurację 64-bitowym przy użyciu programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [porady: Konfigurowanie projektów do platform docelowych](../ide/how-to-configure-projects-to-target-platforms.md).  
  
3.  W tym momencie zostanie uruchomiony 64-bitowej wersji zdalnego debugera (msvsmon.exe). Działa on tak długo, jak rozwiązanie z konfiguracją 64-bitowych jest otwarty.  
  
4.  Rozpocznij debugowanie. Powinny mieć to samo środowisko korzystania, zgodnie z konfiguracją 32-bitowych. Jeśli występują błędy, zobacz sekcję Rozwiązywanie problemów poniżej.  
  
## <a name="troubleshooting-64-bit-debugging"></a>Rozwiązywanie problemów z debugowaniem 64-bitowych  
 Może zostać wyświetlony błąd: "Operacja debugowania 64-bitowego trwa dłużej niż oczekiwano." W takim przypadku Visual Studio wysłał żądanie do 64-bitowej wersji msvsmon.exe i trwało długo daje w wyniku tego żądania, aby wrócić do.  
  
 Istnieją dwa główne przyczyny tego błędu:  
  
-   Zainstalowane na komputerze, który spowodował stos sieciowy się niepewne sieci oprogramowanie zabezpieczeń i została porzucona pakiety przesyłane za pośrednictwem hosta lokalnego. Spróbuj wyłączyć wszelkie oprogramowanie zabezpieczeń sieci i zobacz, jeśli to rozwiązuje go. Jeśli tak, zgłoś ruchu localhost uniemożliwiać oprogramowanie dostawcy oprogramowania zabezpieczeń sieci.  
  
-   Używasz zawieszenie lub wydajności problem z programem Visual Studio. Jeśli ten problem występuje regularnie, można zbierać zrzuty programu Visual Studio (devenv.exe) i proces roboczy (msvsmon.exe) i wysyłać je do firmy Microsoft. Informacji o raportach problemu, zobacz [jak zgłosić Problem z programem Visual Studio](../ide/How-to-Report-a-Problem-with-Visual-Studio-2017.md).
  
## <a name="see-also"></a>Zobacz też  
 [64-bit — aplikacje](http://msdn.microsoft.com/Library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)   
 [Konfigurowanie programów dla wersji 64-bitowych](/cpp/build/configuring-programs-for-64-bit-visual-cpp)   
 [Obsługa 64-bitowego środowiska IDE programu Visual Studio](../ide/visual-studio-ide-64-bit-support.md)   
 [Przy użyciu plików zrzutu](../debugger/using-dump-files.md)   
 [Debugowanie zdalne](../debugger/remote-debugging.md)