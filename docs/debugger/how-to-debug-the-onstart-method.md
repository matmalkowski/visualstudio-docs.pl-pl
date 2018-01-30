---
title: 'Porady: debugowanie metody OnStart | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: bcfe3062ff0f36628016e1a9c0fc70278a5b0de7
ms.sourcegitcommit: 9a2f937e42305db6e3eaa7aadc235b0ba9aafc83
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2018
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