---
title: Debugowanie i proces hostingu | Dokumentacja firmy Microsoft
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
- debugging [Visual Studio], hosting process
- hosting process
ms.assetid: d0f0b9a6-2a6e-463d-b6ea-9518ee727933
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 01d4ebaada2c8ac65c1f44a5c80525f1b9e66a5d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-and-the-hosting-process"></a>Debugowanie i proces hostingu
Procesu hostingu Visual Studio poprawia wydajność debugera i włącza nowe funkcje debugera, takich jak debugowanie częściowo zaufane i Obliczanie wyrażenia czasu projektowania. Jeśli potrzebujesz, można wyłączyć procesu hostingu. Aby uzyskać więcej informacji, zobacz [porady: wyłączanie procesu hostingu](../ide/how-to-disable-the-hosting-process.md). W poniższych sekcjach opisano niektóre różnice między debugowanie z włączonymi i wyłączonymi procesu hostingu.  
  
## <a name="partial-trust-debugging-and-click-once-security"></a>Częściowo zaufane debugowania i kliknij przycisk — raz zabezpieczeń  
 Debugowanie częściowo zaufanym wymaga procesu hostingu. Jeśli wyłączysz procesu hostingu debugowanie częściowo zaufane nie będzie działać nawet jeśli częściowego zaufania zabezpieczeń jest włączona na **zabezpieczeń** strony **właściwości projektu**. Aby uzyskać więcej informacji, zobacz [porady: wyłączanie procesu hostingu](../ide/how-to-disable-the-hosting-process.md) i [porady: debugowanie aplikacji częściowego zaufania](../debugger/how-to-debug-a-partial-trust-application.md).  
  
## <a name="design-time-expression-evaluation"></a>Obliczanie wyrażenia czasu projektowania  
 Zawsze wyrażenia czasu projektowania używa procesu hostingu. Wyłączanie hostingu przetworzyć w **właściwości projektu** wyłącza Obliczanie wyrażenia czasu projektowania dla projektów biblioteki klas. Obliczanie wyrażenia czasu projektowania nie jest wyłączone dla innych typów projektów. Zamiast tego programu Visual Studio rozpoczyna się rzeczywisty plik wykonywalny i używa go do oceny czasu projektowania bez procesu hostingu. Ta różnica można wygenerować różne wyniki.  
  
## <a name="appdomaincurrentdomainfriendlyname-differences"></a>Różnice AppDomain.CurrentDomain.FriendlyName  
 `AppDomain.CurrentDomain.FriendlyName`Zwraca różne wyniki, w zależności od tego, czy Proces hostingu jest włączone. Jeśli należy wywołać `AppDomain.CurrentDomain.FriendlyName` z procesu hostingu włączone, zwraca *nazwa_aplikacji*`.vhost.exe`. Jeśli wywołujesz ona procesu hostingu wyłączone, zwraca *nazwa_aplikacji*`.exe`.  
  
## <a name="assemblygetcallingassemblyfullname-differences"></a>Assembly.GetCallingAssembly(). Różnice imię i nazwisko  
 `Assembly.GetCallingAssembly().FullName`Zwraca różne wyniki, w zależności od tego, czy Proces hostingu jest włączone. Jeśli należy wywołać `Assembly.GetCallingAssembly().FullName` z procesu hostingu włączone, zwraca `mscorlib`. Jeśli należy wywołać `Assembly.GetCallingAssembly().FullName` z procesu hostingu wyłączone, zwraca nazwę aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Proces hostingu (vshost.exe)](../ide/hosting-process-vshost-exe.md)   
 [Porady: debugowanie częściowo zaufanych aplikacji](../debugger/how-to-debug-a-partial-trust-application.md)   
 [Instrukcje: Wyłączanie procesu hostingu](../ide/how-to-disable-the-hosting-process.md)