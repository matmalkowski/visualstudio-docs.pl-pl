---
title: Włączanie programu debugowanego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3f8dc37e5d59738e6ef326be71e773c1e4e57351
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="enabling-a-program-to-be-debugged"></a>Włączanie programu do debugowania
Przed aparat debugowania (DE) można zdebugować program, należy uruchomić DE lub dołączenie go do istniejącego programu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Pobieranie portu](../../extensibility/debugger/getting-a-port.md)  
 W tym artykule omówiono sposób uzyskiwania portu jako pierwszy krok w celu włączenia programu do debugowania.  
  
 [Rejestrowanie programu](../../extensibility/debugger/registering-the-program.md)  
 Wyjaśniono, następnym krokiem podczas włączania programu do debugowania: rejestrując ją z portem. Po zarejestrowaniu, program może być debugowany przez proces dołączania lub debugowania just-in-time (JIT).  
  
 [Dołączanie do programu](../../extensibility/debugger/attaching-to-the-program.md)  
 Wyjaśniono, następnym krokiem: dołączanie debugera do programu.  
  
 [Na podstawie uruchamiania dołączania](../../extensibility/debugger/launch-based-attachment.md)  
 W tym artykule opisano na podstawie uruchamiania załącznika program, który jest automatycznie po uruchomieniu przez SDM.  
  
 [Wysyłanie wymaganych zdarzeń](../../extensibility/debugger/sending-the-required-events.md)  
 Kroki wymagane zdarzenia podczas tworzenia aparat debugowania (DE) i dołączenie go do programu.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Definiuje aparat debugowania (DE) oraz opis implementowane za pośrednictwem interfejsów DE i sposób może spowodować debugera do przejścia w tryb działania różnych usług.