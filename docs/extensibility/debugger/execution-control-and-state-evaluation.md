---
title: Kontrola wykonywania i oceny stanu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d306ffe484605a081afa81afdcdcaa1a70339c84
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31098176"
---
# <a name="execution-control-and-state-evaluation"></a>Kontrola wykonywania i oceny stanu
Debugowanie aplikacji wymaga wykonania takie funkcje kontroli wykonywania jako Wkraczanie do funkcji, zatrzymywania na punktów przerwania i kontynuowanie wykonania. Visual Studio debugowanie baz jego kontrola wykonywania na zdarzenia wysyłane między składnikami debugera.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Kontrola programu](../../extensibility/debugger/program-control.md)  
 Wyświetla następujące procedury, które występują w poziomie programu: ustawienie następnej instrukcji, wykonywania, wykonywanie krok po kroku, kontynuowanie, wstrzymywania i wznawiania.  
  
 [Metody dotyczące punktu przerwania](../../extensibility/debugger/breakpoint-related-methods.md)  
 Definiuje to granica i oczekujące na typy punktów kontrolnych, które obsługuje program Visual Studio.  
  
 [Ocena stosu wywołań](../../extensibility/debugger/call-stack-evaluation.md)  
 W tym artykule omówiono implementacji metody, które umożliwiają wyświetlanie ramek stosu stosu wywołań w trybie przerwania.  
  
 [Szacowanie wyrażeń](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
 Wyjaśniono sposób aparat debugowania (DE), wyrażenie oceny (EE), a sesja debugowania Menedżera objętego analizowania i obliczenia wyrażenia wprowadzane do jednego z okien IDE.  
  
 [Zdarzenia kontrolki](../../extensibility/debugger/control-events.md)  
 W tym artykule omówiono interfejs używany do wysyłania zdarzeń podczas wykonywania kontrolowany przez program.