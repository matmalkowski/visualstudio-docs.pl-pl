---
title: "Włączanie programu debugowanego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a581c5a9ae56f52727c011db1de2ad35a5ba3592
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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