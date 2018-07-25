---
title: Dołączanie na podstawie uruchamiania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 518a3f804298df6c0af98a6e5d2a6d851b645aee
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231707"
---
# <a name="launch-based-attachment"></a>Dołączanie na podstawie uruchamiania
Na podstawie uruchamiania załącznika do programu odbywa się automatycznie. Podczas procesu hostingu program jest uruchamiany przez SDM, na podstawie uruchamiania załącznika poniżej ścieżką podobną do tej metody ręcznego załącznika. Aby uzyskać informacje, zobacz [dołączyć do programu](../../extensibility/debugger/attaching-to-the-program.md).  
  
## <a name="the-attaching-process"></a>Dołączanie procesu  
 Główna różnica polega na sekwencję zdarzeń po **Dołącz** wywołań w następujący sposób:  
  
1.  Wyślij **IDebugEngineCreateEvent2** obiekt zdarzenia do SDM. Aby uzyskać więcej informacji, zobacz [wysyłanie zdarzeń](../../extensibility/debugger/sending-events.md).  
  
2.  Wywołania `IDebugProgram2::GetProgramId` metody **IDebugProgram2** interfejsu przekazany do **Dołącz** metody.  
  
3.  Wyślij **IDebugProgramCreateEvent2** zdarzeń obiektowi powiadomić SDM, lokalnej **IDebugProgram2** do reprezentowania program DE został utworzony obiekt.  
  
4.  Wyślij [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) obiektu zdarzenia, aby powiadomić SDM, utworzenia nowego wątku dla procesu, który uruchomił.  
  
## <a name="see-also"></a>Zobacz także  
 [Wysyłanie wymaganych zdarzeń](../../extensibility/debugger/sending-the-required-events.md)   
 [Włącz program do debugowania](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)