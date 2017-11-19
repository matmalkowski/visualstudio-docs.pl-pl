---
title: "Na podstawie uruchamiania załącznika | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2aa9787ad432e402375680c4e27e433236b13249
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="launch-based-attachment"></a>Na podstawie uruchamiania załącznika
Na podstawie uruchamiania załącznika z programem odbywa się automatycznie. Gdy proces obsługujący program jest uruchamiana przez SDM, na podstawie uruchamiania załącznika następuje ścieżkę do tej metody ręcznego załącznika. Aby uzyskać informacje, zobacz [dołączenie do programu](../../extensibility/debugger/attaching-to-the-program.md).  
  
## <a name="the-attaching-process"></a>Dołączenia procesu  
 Główna różnica polega na sekwencję zdarzeń po **Attach** wywołań w następujący sposób:  
  
1.  Wyślij **IDebugEngineCreateEvent2** obiekt zdarzenia do SDM. Aby uzyskać więcej informacji, zobacz [wysyłania zdarzeń](../../extensibility/debugger/sending-events.md).  
  
2.  Wywołania `IDebugProgram2::GetProgramId` metody w **IDebugProgram2** interfejsu przekazany do **Attach** metody.  
  
3.  Wyślij **IDebugProgramCreateEvent2** obiekt zdarzenia powiadomiono SDM który lokalnej **IDebugProgram2** do reprezentowania program DE utworzenia obiektu.  
  
4.  Wyślij [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) zdarzeń obiektu do powiadamiania SDM utworzony dla procesu, który uruchomić nowego wątku.  
  
## <a name="see-also"></a>Zobacz też  
 [Wysyłanie zdarzeń wymagane](../../extensibility/debugger/sending-the-required-events.md)   
 [Włączanie programu do debugowania](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)