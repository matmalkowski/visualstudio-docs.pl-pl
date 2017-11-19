---
title: "Wysyłanie zdarzeń | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bf4c3b0f494a5825820b8f794ccaf5dc727786e3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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
  
 [Typy obsługiwane zdarzeń](../../extensibility/debugger/supported-event-types.md)  
 W tym artykule omówiono typy zdarzeń aktualnie obsługiwany: synchronicznego i asynchronicznego.  
  
 [Opisy zdarzeń](../../extensibility/debugger/event-descriptions.md)  
 Definiuje zdarzenia i powody ich używania.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Tworzenie aparat debugowania niestandardowych](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 W tym artykule opisano, jak URZ współpracuje z interpreter lub systemu operacyjnego do świadczenia usług debugowania.