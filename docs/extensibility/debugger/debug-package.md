---
title: Debugowanie pakietu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6ca438b7ed8c9b6a4b84693f975144040f998f01
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="debug-package"></a>Debugowanie pakietu
Pakiet debugowania jest uruchamiany w powłoce programu Visual Studio i obsługuje wszystkie interfejsu użytkownika. Korzysta z programu Visual Studio debugowanie interfejsów, a komunikuje się z menedżerem sesji debugowania (SDM).  
  
 Podział zdarzeń wysyłanych za pośrednictwem SDM przełącznika debugera z trybu wykonywania tryb przerwania i zmienić fokus do programu, gdy wystąpił przerwy. Pakiet debugowania śledzi ramki stosu i wątku z informacje wysyłane do niej przez zdarzenia.  
  
 Pakiet debugowania nie ma języka ani zależności środowiska wykonawczego środowiska. Nie jest wymagane do wdrożenia lub zmodyfikować pakiet debugowania.  
  
 Pakiet debugowania jest implementowany przez vsdebug.dll.  
  
## <a name="see-also"></a>Zobacz też  
 [Menedżer sesji debugowania](../../extensibility/debugger/session-debug-manager.md)   
 [Ramki stosu](../../extensibility/debugger/stack-frames.md)   
 [Wątki](../../extensibility/debugger/threads.md)   
 [Składniki debugera](../../extensibility/debugger/debugger-components.md)