---
title: Tworzenie niestandardowego aparatu debugowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 66ec73a13a3494ae6642e6d0f7397c9f3c1f0b0b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31101381"
---
# <a name="creating-a-custom-debug-engine"></a>Tworzenie aparat debugowania niestandardowych
Aparat debugowania (DE) to składnik, który pozwala na debugowanie architektury określonego czasu wykonywania. Zazwyczaj jest tylko jedna implementacja DE na środowisko wykonawcze.  
  
> [!NOTE]
>  Gdy istnieją oddzielne implementacje DE języka Transact-SQL i JScript i VBScript i JScript udostępniać pojedynczy DE.  
  
 Niemcy działa w systemie operacji lub interpreter zapewnienie debugowania usług wykonywania oceny kontroli, punkty przerwania i wyrażenia. Te usługi są implementowane za pośrednictwem interfejsów DE i może powodować debugera do przejścia w tryb innego działania. Aby uzyskać więcej informacji, zobacz [tryby operacyjne](../../extensibility/debugger/operational-modes.md).  
  
 Tworzenie URZ składa się z następujących czynności:  
  
1.  Rejestrowanie URZ z programem Visual Studio  
  
2.  Włączanie programu do debugowania  
  
3.  Wykonanie oceny kontroli i stanu  
  
4.  Wysyłanie zdarzeń  
  
5.  Kończenie działania i odłączanie  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Rejestrowanie niestandardowego aparatu debugowania](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 Opisano kroki wymagane do zarejestrowania aparat debugowania z programem Visual Studio, aby można go używać.  
  
 [Włączanie debugowania programu](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 Wyjaśnia, czy przed Twojej DE można debugować programu, musi najpierw uruchomić DE lub dołączenie go do istniejącego programu.  
  
 [Kontrola wykonywania i ocena stanu](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 W tym artykule omówiono, dlaczego debugowania aplikacji wymaga implementowania funkcji kontroli wykonania.  
  
 [Wysyłanie zdarzeń](../../extensibility/debugger/sending-events.md)  
 W tym artykule opisano komunikację między debugera i DE jako model zdarzeń oparty na modelu DCOM.  
  
 [Kończenie i odłączanie](../../extensibility/debugger/termination-and-detaching.md)  
 Wyjaśniono, jak uzyskać normalne wygaśnięcie, co oznacza, że nie ma żadnych punktów przerwania, wyjątki, błędy środowiska wykonawczego ani nieskończone pętle w aplikacji do debugowania.  
  
 [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)  
 Dokumenty wywoływania kolejność zdarzeń występujących w sesji debugowania.  
  
 [Instrukcje: debugowanie niestandardowego aparatu debugowania](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 Wyjaśniono, jak debugować DE niestandardowych.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzalność debugera programu Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)