---
title: Tryby operacyjne | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 205837bc5bfdf9476839ea1e54a53dc57dbf9a72
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="operational-modes"></a>Tryby operacyjne
Istnieją trzy tryby, w których IDE może działać, w następujący sposób:  
  
-   [Tryb projektowania](#vsconoperationalmodesanchor1)  
  
-   [Tryb uruchamiania](#vsconoperationalmodesanchor2)  
  
-   [Tryb przerwania](#vsconoperationalmodesanchor3)  
  
 Jak aparat debugowania niestandardowe (DE) przejścia między trybów jest decyzji o implementacji, musisz znać mechanizmów przejścia. Niemcy może lub nie może bezpośrednio implementować trybów. Te tryby są naprawdę pakietu tryb debugowania które przełączają się na podstawie akcji użytkownika lub zdarzenia z DE. Na przykład przejście z trybu wykonywania do tryb przerwania jest zainicjowanego przez zdarzeniem zatrzymującym z DE. Przejście z break, aby uruchomić trybu lub kroku jest zainicjowanego przez użytkownika wykonywania operacji, takich jak krok lub Execute. Aby uzyskać więcej informacji o zmianach, DE, zobacz [kontroli wykonania](../../extensibility/debugger/control-of-execution.md).  
  
##  <a name="vsconoperationalmodesanchor1"></a>Tryb projektowania  
 Tryb projektowania jest nonrunning stan debugowania programu Visual Studio, w tym czasie można ustawić debugowanie funkcji w aplikacji.  
  
 Tylko kilka debugowanie funkcji są używane w trybie projektowania. Programista może zdecydować ustawić punkty przerwania lub utworzyć Czujka wyrażeń. Niemcy nigdy nie jest załadowany lub wywołana w czasie, w jakim jest IDE w trybie projektowania. Interakcja z DE odbywa się podczas tylko tryby uruchomienia i przerwania.  
  
##  <a name="vsconoperationalmodesanchor2"></a>Tryb uruchamiania  
 Tryb uruchamiania występuje, gdy program jest uruchamiany w sesji debugowania w środowisku IDE. Aplikacja zostanie uruchomiona do momentu zakończenia, do momentu punkt przerwania zostaje trafiony, lub jest zgłaszany wyjątek. Gdy aplikacja zostanie uruchomiona zakończenia, DE przejścia do trybu projektowania. Gdy punkt przerwania zostaje trafiony lub jest zgłaszany wyjątek, DE przechodzi w tryb przerwania.  
  
##  <a name="vsconoperationalmodesanchor3"></a>Tryb przerwania  
 Tryb przerwania występuje, gdy wykonywanie programu debugowania jest wstrzymana. Tryb przerwania oferuje dewelopera migawki aplikacji w czasie podziału i umożliwia deweloperowi analizowanie stanu aplikacji i zmiany sposobu uruchamiania aplikacji. Deweloper można wyświetlać i edytować kod, zbadać lub modyfikować danych, ponownie uruchom aplikację, zakończenie wykonywania lub kontynuować działanie z tego samego punktu.  
  
 Tryb przerwania jest wprowadzana w trakcie DE wysyła zdarzenia synchroniczne zatrzymania. Zdarzenia synchroniczne zatrzymywania, skrót zdarzenia zatrzymywania powiadomić menedżera debugowania sesji (SDM) i środowiska IDE programu debugowanej aplikacji została zatrzymana wykonywanie kodu. [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) i [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) interfejsy są przykłady zatrzymywania zdarzeń.  
  
 Trwa zatrzymywanie zdarzenia są nadal przez wywołanie do jednej z następujących metod, których przejście debugera z trybu przerwania Uruchom lub krok trybu:  
  
-   [Wykonanie](../../extensibility/debugger/reference/idebugprocess3-execute.md)  
  
-   [Krok](../../extensibility/debugger/reference/idebugprocess3-step.md)  
  
-   [Kontynuuj](../../extensibility/debugger/reference/idebugprocess3-continue.md)  
  
###  <a name="vsconoperationalmodesanchor4"></a>Tryb kroku  
 Tryb krok występuje, gdy program kroki do następnego wiersza kodu, lub do, za pośrednictwem lub funkcji. Krok jest wykonywany przez wywołanie metody [krok](../../extensibility/debugger/reference/idebugprocess3-step.md). Ta metoda wymaga `DWORD`s, która określa [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) i [STEPKIND](../../extensibility/debugger/reference/stepkind.md) wyliczenia jako parametry wejściowe.  
  
 Gdy program pomyślnie kroków do następnego wiersza kodu lub do funkcji lub uruchomieniu kursor lub ustaw punkt przerwania, DE automatycznie zostanie przekazana do tryb przerwania.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrola wykonywania](../../extensibility/debugger/control-of-execution.md)