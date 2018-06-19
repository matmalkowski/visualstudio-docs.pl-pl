---
title: 'Porady: debugowanie metody OnStart | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- OnStart method
- debugging [Visual Studio], Windows services
- debugging managed code, OnStart method
- debugging Windows Services applications, OnStart method
- Windows Service applications, debugging
ms.assetid: b06b5d65-424b-490f-bf58-97583cd7006a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d438a8d6dcd80ec8d9dcce2fb4943e8b5614442c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31481856"
---
# <a name="how-to-debug-the-onstart-method"></a>Porady: debugowanie metody OnStart
Usługa systemu Windows można debugować przez uruchamianie usługi i dołącza debuger do procesu usługi. Aby uzyskać więcej informacji, zobacz [porady: debugowanie aplikacji usług systemu Windows](/dotnet/framework/windows-services/how-to-debug-windows-service-applications). Jednak aby debugować <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> metody usługi systemu Windows, można uruchomić debugera z wewnątrz metody.  
  
1.  Dodaj wywołanie do <xref:System.Diagnostics.Debugger.Launch%2A> na początku `OnStart()`metody.  
  
    ```csharp  
    protected override void OnStart(string[] args)  
    {  
        System.Diagnostics.Debugger.Launch();  
     }  
    ```  
  
2.  Uruchom usługę (można użyć `net start`, lub uruchomić go w **usług** okno).  
  
     Powinny pojawić okno dialogowe podobne do poniższych:  
  
     ![OnStartDebug](../debugger/media/onstartdebug.png "OnStartDebug")  
  
3.  Wybierz **tak, debugowania \<nazwa usługi >.**  
  
4.  W oknie Debuger just in Time wybierz wersję programu Visual Studio ma być używany na potrzeby debugowania.  
  
     ![JustInTimeDebugger](../debugger/media/justintimedebugger.png "JustInTimeDebugger")  
  
5.  Nowe wystąpienie klasy uruchomieniu programu Visual Studio i wykonywanie został zatrzymany w `Debugger.Launch()` metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)