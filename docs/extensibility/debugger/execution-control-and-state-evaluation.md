---
title: Kontrola wykonywania i oceny stanu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4f2f76f97111f24a7b6b4ea1a7a22004d6867fcd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="execution-control-and-state-evaluation"></a>Kontrola wykonywania i oceny stanu
Debugowanie aplikacji wymaga wykonania takie funkcje kontroli wykonywania jako Wkraczanie do funkcji, zatrzymywania na punktów przerwania i kontynuowanie wykonania. Visual Studio debugowanie baz jego kontrola wykonywania na zdarzenia wysyłane między składnikami debugera.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Formant programu](../../extensibility/debugger/program-control.md)  
 Wyświetla następujące procedury, które występują w poziomie programu: ustawienie następnej instrukcji, wykonywania, wykonywanie krok po kroku, kontynuowanie, wstrzymywania i wznawiania.  
  
 [Metody dotyczące punktu przerwania](../../extensibility/debugger/breakpoint-related-methods.md)  
 Definiuje to granica i oczekujące na typy punktów kontrolnych, które obsługuje program Visual Studio.  
  
 [Ocena stosu wywołań](../../extensibility/debugger/call-stack-evaluation.md)  
 W tym artykule omówiono implementacji metody, które umożliwiają wyświetlanie ramek stosu stosu wywołań w trybie przerwania.  
  
 [Szacowanie wyrażeń](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
 Wyjaśniono sposób aparat debugowania (DE), wyrażenie oceny (EE), a sesja debugowania Menedżera objętego analizowania i obliczenia wyrażenia wprowadzane do jednego z okien IDE.  
  
 [Zdarzenia formantów](../../extensibility/debugger/control-events.md)  
 W tym artykule omówiono interfejs używany do wysyłania zdarzeń podczas wykonywania kontrolowany przez program.