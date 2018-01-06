---
title: "Porady: debugowanie klientów i serwerów za pomocą debugowania RPC COM | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.com
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- RPC (Remote Procedure Call), debugging COM clients and servers
- COM, debugging
- RPC (Remote Procedure Call)
- RPC (Remote Procedure Call), debugging
- COM clients, debugging
- COM servers, debugging
- out-of-process remote procedure call debugging
- remote debugging, RPC (Remote Procedure Call)
- in-process remote procedure call debugging
ms.assetid: 3e8526c8-43b5-4b87-8e0d-b22c24f0a3ea
caps.latest.revision: "23"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 624a08f436999c30290d7ca338669f7b0a33d1c7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-debug-com-clients-and-servers-using-rpc-debugging"></a>Porady: debugowanie klientów i serwerów COM za pomocą debugowania RPC
Debugowanie zdalnego wywołania (procedur RPC) procedury służy do debugowania aplikacji klient/serwer COM. Należy włączyć RPC, debugowanie, aby go użyć. Z włączonym debugowaniem RPC, po kroku do wywołania serwera od klientów, debuger dołączony do serwera i umożliwia debugowanie kodu. Gdy debuger jest dołączony, można użyć wszystkich funkcji debugera z procesami klienta i serwera.  
  
### <a name="to-enable-rpc-debugging"></a>Aby włączyć debugowanie RPC  
  
1.  Na **narzędzia** menu, kliknij przycisk **opcje**.  
  
2.  W **opcje** okno dialogowe, kliknij przycisk **debugowanie** folderu.  
  
3.  Kliknij przycisk **natywnego** strony.  
  
4.  Wybierz **debugowania RPC** pole wyboru.  
  
    > [!NOTE]
    >  Aby debugować wywołania RPC, musi mieć uprawnienia administratora lub użytkownika.  
  
    > [!NOTE]
    >  Wykonywanie krok po kroku na zdalnym serwerze z systemem Microsoft Windows Vista RPC będzie działać tylko wtedy, gdy debuger natywny jest dołączony do serwera zdalnego. W przeciwnym razie wywołania RPC zakończy się niepowodzeniem bez komunikatu o błędzie. W przeciwnym razie ukończy wywołanie RPC, ale krok do wywołania RPC nie będą działać.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kontenera i serwera COM](../debugger/com-server-and-container-debugging.md)  
 [Debugowanie w programie Visual Studio](../debugger/index.md) [debugera samouczek funkcji](../debugger/debugger-feature-tour.md)