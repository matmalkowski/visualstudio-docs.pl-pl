---
title: Wysyłanie zdarzeń | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 87087a2087591b01170b82c0335e4bbffc579cc2
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2018
ms.locfileid: "39252456"
---
# <a name="send-events"></a>Wysyłanie zdarzeń
Mechanizm komunikacji między debugera i aparat debugowania (DE) to model zdarzeń oparty na modelu DCOM. Zdarzenia są wysyłane jako obiekty COM, a każde zdarzenie ma parametry, które określają:  
  
-   DE, która wywołała zdarzenie.  
  
-   Opis co się stało.  
  
-   Proces, program i informacji o wątku, który identyfikuje kontekst, w którym wystąpiło zdarzenie. Ten proces nie są wysyłane do zdarzeń wysyłanych z URZ.  
  
-   Typ zdarzenia, która wskazuje, czy zdarzenie jest synchroniczna lub asynchroniczna.  
  
 Wszystkie zdarzenia debugowania są wysyłane przy użyciu metody [IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Źródła zdarzeń](../../extensibility/debugger/event-sources-visual-studio-sdk.md)  
 Opisano dwa źródła zdarzeń: aparat debugowania (DE) i sesja debugowania manager (SDM).  
  
 [Obsługiwane typy zdarzeń](../../extensibility/debugger/supported-event-types.md)  
 W tym artykule omówiono aktualnie obsługiwane typy zdarzeń: synchronicznego i asynchronicznego.  
  
 [Opisy zdarzeń](../../extensibility/debugger/event-descriptions.md)  
 Definiuje zdarzenia i przyczyny ich użycie.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 W tym artykule opisano, jak DE współpracuje z interpreter lub systemu operacyjnego w celu dostarczania usług debugowania.