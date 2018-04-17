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
ms.openlocfilehash: 9bbe7946b866cd751be1f0dac2dba5b8dea57e04
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="sending-events"></a>Wysyłanie zdarzeń
Mechanizm komunikacji między debugera i aparat debugowania (DE) to model zdarzenie oparte na modelu DCOM. Zdarzenia są wysyłane jako obiekty COM, a każde zdarzenie ma parametry, które określ następujące ustawienia:  
  
-   Niemcy, który wywołał zdarzenie.  
  
-   Opis co się stało.  
  
-   Proces, program i informacji o wątku, który identyfikuje kontekst, w którym wystąpiło zdarzenie. Proces nie są wysyłane do zdarzeń wysyłanych z URZ.  
  
-   Typ zdarzenia, który wskazuje, czy zdarzenie jest synchroniczna lub asynchroniczna.  
  
 Wszystkie zdarzenia debugowania są wysyłane przy użyciu metody [IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Źródła zdarzeń](../../extensibility/debugger/event-sources-visual-studio-sdk.md)  
 Opisano dwa źródła zdarzeń: aparat debugowania (DE), a sesja debugowania Menedżera (SDM).  
  
 [Obsługiwane typy zdarzeń](../../extensibility/debugger/supported-event-types.md)  
 W tym artykule omówiono typy zdarzeń aktualnie obsługiwany: synchronicznego i asynchronicznego.  
  
 [Opisy zdarzeń](../../extensibility/debugger/event-descriptions.md)  
 Definiuje zdarzenia i powody ich używania.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 W tym artykule opisano, jak URZ współpracuje z interpreter lub systemu operacyjnego do świadczenia usług debugowania.