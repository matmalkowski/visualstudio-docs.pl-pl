---
title: "Debugowanie zadań | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: d1a6ffff4d3ac0410ca3de7e2cd595119763e88b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-tasks"></a>Debugowanie zadań
Aby zdebugować program, musi zostać uruchomiona i aparat debugowania (DE) musi być dołączony do niego, w przeciwnym razie DE musi być dołączony do wcześniej uruchomionego programu. Po dołączeniu DE należy wygenerować pewnych zdarzeń uruchomienia. W odpowiedzi pakiet debugowania próbuje powiązać punktów przerwania ustawionych w IDE. Gdy program trafi powiązania punktu przerwania, zostaje zatrzymana i oczekuje na dane wejściowe użytkownika.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Problemy dotyczące zabezpieczeń](../../extensibility/debugger/security-issues.md)  
 W tym artykule omówiono czynności zabezpieczeń, które są wymagane do debugowania programu.  
  
 [Uruchamianie programu](../../extensibility/debugger/launching-a-program.md)  
 Instrukcje krok po kroku dotyczące sposobu określania DE, który wymaga systemu operacyjnego, aby uruchomić program.  
  
 [Dołączanie bezpośrednio do programu](../../extensibility/debugger/attaching-directly-to-a-program.md)  
 W tym artykule opisano proces wykorzystywany do debugowania programu w ramach procesu, który jest już uruchomiony.  
  
 [Wysyłanie zdarzeń uruchamiania po uruchomieniu](../../extensibility/debugger/sending-startup-events-after-a-launch.md)  
 Wyświetla listę zdarzeń, które mają miejsce, gdy DE jest dołączony do programu, dopóki program znajduje się na jego główny punkt wejścia i jest gotowy do debugowania.  
  
 [Kontrola wykonywania](../../extensibility/debugger/control-of-execution.md)  
 W tym artykule wyjaśniono, jak DE zwykle wysyła zdarzenie punktu wejścia, zdarzenie ukończenia ładowania lub zdarzeniem zatrzymującym, w zależności od okoliczności.  
  
 [Tworzenie powiązań punktów przerwania](../../extensibility/debugger/binding-breakpoints.md)  
 W tym artykule opisano, jak to zrobić, jeśli punkt przerwania ustawiony przez użytkownika, środowiska IDE formulates żądanie i wyświetla monit o sesji debugowania, aby utworzyć punkt przerwania.  
  
 [Ocenianie wyrażeń](../../extensibility/debugger/evaluating-expressions.md)  
 Wyjaśnia sposób tworzenia wyrażenia i co się dzieje, gdy wyrażenie jest obliczane.  
  
 [Wizualizacja i wyświetlanie danych](../../extensibility/debugger/visualizing-and-viewing-data.md)  
 W tym artykule wyjaśniono, jak wizualizatorach typu i podglądy niestandardowe są obsługiwane przez ewaluatora wyrażenia (EE).  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)  
 Zawiera opis głównych pojęć architektury debugowania.  
  
 [Składniki debugera](../../extensibility/debugger/debugger-components.md)  
 Zawiera omówienie składników debugowania programu Visual Studio, które obejmują DE, EE i obsługi symboli (SH).  
  
 [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)  
 W tym artykule wyjaśniono, jak DE działa jednocześnie w ramach kodu, dokumentacji i konteksty Obliczanie wyrażenia. Opisuje, dla każdego z trzech kontekstów lokalizacji, pozycja lub oceny odpowiednie do niego.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)