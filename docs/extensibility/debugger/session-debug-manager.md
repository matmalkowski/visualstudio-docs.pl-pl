---
title: Sesja debugowania Manager | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 001c0b954cd47b9825a6982f2474d6fd6d415e23
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="session-debug-manager"></a>Menedżer sesji debugowania
Menedżer debugowania sesji (SDM) zarządza dowolną liczbę aparatami debugowania (DE) debugowania dowolną liczbę programów w wielu procesach w dowolnej liczby maszyn. Oprócz multiplekser aparat debugowania, SDM zapewnia spójny obraz sesji debugowania do IDE.  
  
## <a name="session-debug-manager-operation"></a>Operacja Menedżera sesji debugowania  
 Menedżer debugowania sesji (SDM) zarządza DE. Może być uruchomione na komputerze, w tym samym czasie więcej niż jeden aparat debugowania. Aby Multipleksowanie DEs, SDM opakowuje liczba interfejsów z DEs i udostępnia je do środowiska IDE jako jeden interfejs.  
  
 Aby zwiększyć wydajność, niektóre interfejsy nie są multipleksowane. Zamiast tego są one używane bezpośrednio z DE i wywołania te interfejsy nie przechodzi przez SDM. Na przykład interfejsy używane z pamięci, kod i kontekstami dokumentu są nie multiplexed, ponieważ odnoszą się do instrukcji określonych, pamięć lub dokument w debugowane określonych DE określonego programu. Nie inne DE należy zaangażować w tym samym poziomie komunikacji.  
  
 Nie dotyczy wszystkich kontekstach. Wywołania interfejsu kontekstu oceny wyrażenia przejść przez SDM. Podczas obliczania wyrażenia opakowuje SDM [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfejs, który zapewnia do środowiska IDE, ponieważ podczas szacowania tego wyrażenia może obejmować wiele DEs, który debugowania programów w ten sam proces, która może być uruchomiona na tym samym wątku.  
  
 SDM zwykle działa jako mechanizm delegowania, ale mogą działać jako mechanizm emisji. Na przykład podczas obliczania wyrażenia SDM działa jako mechanizm emisji do powiadamiania DEs wszystkie one na uruchamianie kodu w określonym wątku. Podobnie SDM odebrania zdarzeniem zatrzymującym emituje wszystkie programy zaprzestania uruchomiona. Po wywołaniu krok SDM emituje wszystkie programy że są one nadal działa. Punkty przerwania są również emisji do każdego DE.  
  
 SDM nie śledzi bieżący program, wątku lub ramki stosu. Proces, program i wątku informacje są wysyłane do SDM w połączeniu z określonych zdarzeń debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Aparat debugowania](../../extensibility/debugger/debug-engine.md)   
 [Składniki debugera](../../extensibility/debugger/debugger-components.md)   
 [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)