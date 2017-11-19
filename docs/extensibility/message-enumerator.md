---
title: "Moduł wyliczający komunikatu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 000b853c1f25d8b68ccdda87e6c0496aeeaaca0e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="message-enumerator"></a>Moduł wyliczający wiadomości
Następujące flagi są używane do `TEXTOUTPROC` funkcji, która jest funkcja wywołania zwrotnego, która zapewnia IDE, gdy wywołuje [SccOpenProject](../extensibility/sccopenproject-function.md) (zobacz [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) szczegółowe informacje dotyczące wywołania zwrotnego Funkcja).  
  
 Jeśli IDE jest pytanie, aby anulować proces, jego może otrzymywać wiadomości Anuluj. W takim przypadku źródło kontrolować wtyczki używa `SCC_MSG_STARTCANCEL` poprosić IDE, aby wyświetlić **anulować** przycisku. Po to mogą być wysyłane dowolny zbiór zwykłych wiadomości. Jeśli dowolny z tych zwraca `SCC_MSG_RTN_CANCEL`, a następnie wtyczki kończy działanie i zwraca. Wtyczka również sonduje `SCC_MSG_DOCANCEL` okresowo, aby określić, czy użytkownik anulował operację. Gdy wszystkie operacje są wykonywane, lub jeśli została anulowana przez użytkownika, wysyła wtyczki `SCC_MSG_STOPCANCEL`. `SCC_MSG_INFO`, SCC_MSG_WARNING, oraz typy SCC_MSG_ERROR są używane do wiadomości, które są wyświetlane na liście przewijania wiadomości. `SCC_MSG_STATUS`to specjalny typ, który wskazuje, że tekst powinny być widoczne w pasku stanu lub obszar tymczasowy wyświetlania. Nie ona trwale na liście.  
  
## <a name="syntax"></a>Składnia  
  
```  
enum {   
   SCC_MSG_RTN_CANCEL = -1,   
   SCC_MSG_RTN_OK = 0,   
   SCC_MSG_INFO = 1   
   SCC_MSG_WARNING,   
   SCC_MSG_ERROR,   
   SCC_MSG_STATUS,   
   SCC_MSG_DOCANCEL,   
   SCC_MSG_STARTCANCEL,   
   SCC_MSG_STOPCANCEL   
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 SCC_MSG_RTN_CANCEL  
 Powrót z wywołania zwrotnego, aby wskazać, Anuluj.  
  
 SCC_MSG_RTN_OK  
 Powrót z wywołania zwrotnego, aby kontynuować.  
  
 SCC_MSG_INFO  
 Komunikat ma charakter informacyjny.  
  
 SCC_MSG_WARNING  
 Komunikat jest ostrzeżenie.  
  
 SCC_MSG_ERROR  
 Komunikat jest błąd.  
  
 SCC_MSG_STATUS  
 Komunikat jest przeznaczona dla paska stanu.  
  
 SCC_MSG_DOCANCEL  
 Brak tekstu; Zwraca IDE `SCC_MSG_RTN_OK` lub `SCC_MSG_RTN_CANCEL`.  
  
 SCC_MSG_STARTCANCEL  
 Uruchamia pętli Anuluj.  
  
 SCC_MSG_STOPCANCEL  
 Zatrzymuje pętli Anuluj.  
  
## <a name="see-also"></a>Zobacz też  
 [Plug-in kontroli źródła](../extensibility/source-control-plug-ins.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)