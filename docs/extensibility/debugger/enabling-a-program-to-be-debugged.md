---
title: Włączanie debugowania programu | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: ad6e8e9cb8dd34e3cd084bde1eb94ff5774dd4ba
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2018
ms.locfileid: "39204391"
---
# <a name="enable-a-program-to-be-debugged"></a>Włącz program do debugowania
Zanim program debugować silnik debugowania (DE), możesz uruchomić DE lub dołączyć do istniejącego programu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Pobieranie portu](../../extensibility/debugger/getting-a-port.md)  
 W tym artykule omówiono sposób uzyskiwania portu jako pierwszy krok, aby włączyć program do debugowania.  
  
 [Rejestrowanie programu](../../extensibility/debugger/registering-the-program.md)  
 Wyjaśnia, następnym krokiem podczas włączania programu do debugowania: rejestrując ją za pomocą portu. Po zarejestrowaniu programu mogą być debugowane przez proces dołączania lub debugowania just-in-time (JIT).  
  
 [Dołącz do programu](../../extensibility/debugger/attaching-to-the-program.md)  
 Wyjaśnia, następnym krokiem: dołączanie debugera do programu.  
  
 [Dołączanie na podstawie uruchamiania](../../extensibility/debugger/launch-based-attachment.md)  
 W tym artykule opisano na podstawie uruchamiania załącznika program, który odbywa się automatycznie po uruchomieniu przez kierownika ds.  
  
 [Wysyłanie wymaganych zdarzeń](../../extensibility/debugger/sending-the-required-events.md)  
 Kroki wykonywane w wymaganych zdarzeń podczas tworzenia aparatu debugowania (DE) i dołączania ich do programu.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Definiuje aparat debugowania (DE), a w tym artykule opisano usług implementowane za pomocą interfejsów DE i jak może spowodować, że debuger w celu przejścia między różne tryby operacyjne.