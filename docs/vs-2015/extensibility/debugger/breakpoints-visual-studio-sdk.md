---
title: Punkty przerwania (zestaw SDK programu Visual Studio) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 194551141ed6d56344a4ed49962df41fd3b8d2ae
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42628701"
---
# <a name="breakpoints-visual-studio-sdk"></a>Punkty przerwania (zestaw SDK programu Visual Studio)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [punkty przerwania (Visual Studio SDK)](https://docs.microsoft.com/visualstudio/extensibility/debugger/breakpoints-visual-studio-sdk).  
  
Istnieją trzy typy punktów przerwania: Oczekujące, powiązaną i błędów.  
  
 **A oczekujących punktów przerwania:**  
  
-   Jest klasą abstrakcyjną, która zawiera wszystkie informacje potrzebne, aby powiązać punkt przerwania z co najmniej jeden kontekst kodu w jednym lub wielu programów. Za każdym razem program debugowany kod przyczyny, aby załadować, aparat debugowania sprawdza wszystkich oczekujących punktów przerwania, aby zobaczyć, jeśli może być powiązana.  
  
     Oczekujący punkt przerwania, sama nigdy nie wiąże się kod, ale raczej zbiera i jest nazywany ma zawierać wszystkie powiązane punkty przerwania, które generuje.  
  
-   Jest reprezentowany przez [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) interfejsu.  
  
 **Powiązany punkt przerwania:**  
  
-   Jest skojarzony z klasą abstrakcyjną dla punktu przerwania lub powiązany z kontekstu pojedynczego kodu. Każdy powiązany punkt przerwania jest generowany w odpowiedzi na oczekujący punkt przerwania. Oczekujący punkt przerwania, można wygenerować więcej niż jeden powiązany punkt przerwania.  
  
     Gdy kod jest zwolniony, powiązany punkt przerwania można niepowiązanych i odrzucone.  
  
-   Jest reprezentowany przez [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) interfejsu.  
  
 **Punkt przerwania błąd:**  
  
-   Jest klasą abstrakcyjną dla opisujący błąd podczas próby powiązać oczekujący punkt przerwania kontekst kodu. Błąd punktu przerwania w tym artykule opisano albo błąd w lokalizacji lub wyrażenia punktu przerwania. Aby uzyskać więcej informacji, zobacz [powiązań punktów przerwania](../../extensibility/debugger/binding-breakpoints.md).  
  
     Błąd punktu przerwania, może być błąd lub ostrzeżenie.  
  
-   Jest reprezentowany przez [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 [Programy](../../extensibility/debugger/programs.md)   
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)   
 [Kontekst kodu](../../extensibility/debugger/code-context.md)   
 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)

