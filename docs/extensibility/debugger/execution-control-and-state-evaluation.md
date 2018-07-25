---
title: Kontrola wykonywania i ocena stanu | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 8961d2e06c7013b5667191c190053047f82de77d
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232406"
---
# <a name="execution-control-and-state-evaluation"></a>Wykonanie kontroli i stan oceny
Debugowanie aplikacji wymaga implementacji takich funkcji kontroli wykonywania jako przechodzenie krok po kroku do funkcji, zatrzymanie w punktach przerwania i kontynuowanie wykonywania. Podstawy debugowania programu Visual Studio do jego kontrolki wykonywania zdarzeń wysyłane między składnikami debugera.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Kontrola programu](../../extensibility/debugger/program-control.md)  
 Wyświetla listę następujących procedur, które występują na poziomie programu: ustawienie następnej instrukcji, wykonywanie, wykonywanie krokowe, kontynuowanie, zawieszanie i wznawianie.  
  
 [Metody dotyczące punktu przerwania](../../extensibility/debugger/breakpoint-related-methods.md)  
 Definiuje granicę i oczekujące na typy punktów przerwania, które obsługuje program Visual Studio.  
  
 [Ocena stosu wywołań](../../extensibility/debugger/call-stack-evaluation.md)  
 W tym artykule omówiono implementacji metod, które umożliwiają wyświetlanie ramek stosu stosu wywołań w trybie break.  
  
 [Szacowanie wyrażeń](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
 Przedstawia sposób aparat debugowania (DE) Menedżer wyrażenie oceny (EE) i sesja debugowania są zaangażowane w analizę i obliczania wyrażenia wprowadzane do jednego z okien środowiska IDE.  
  
 [Zdarzenia obiektu Controls](../../extensibility/debugger/control-events.md)  
 W tym artykule omówiono interfejsu używane do wysyłania zdarzeń podczas kontrolowanego wykonywanie programu.