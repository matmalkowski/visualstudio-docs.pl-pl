---
title: "Opisy zdarzeń | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], events
ms.assetid: 09f61652-7e16-4bb0-8055-f61a84bf384e
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6ec084c0d985ce5cc3cb0a886bd1fdcaf6cc3e54
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="event-descriptions"></a>Opisy zdarzeń
Każdy typ zdarzenia ma określone przeznaczenie.  
  
## <a name="events-and-the-reasons-for-their-use"></a>Zdarzenia i powody ich wykorzystania  
  
|Zdarzenie|Opis|  
|-----------|-----------------|  
|Aktywuj zdarzenia dokumentu|Wystąpić, gdy aparat debugowania (DE) wymaga środowiska IDE na otwarcie lub przeniesienia na pierwszy plan dokumentu.|  
|Powiązany punkt przerwania lub punktu przerwania zdarzenia błędów|Wysyłany, gdy punkt przerwania jest powiązany lub gdy nie można powiązać punktu przerwania i zostanie zwrócony błąd.|  
|Anulowano powiązanie punktu przerwania zdarzenia|Wystąpić, gdy punkt przerwania powiązanej usuwa powiązanie z kodu.|  
|Można zatrzymać zdarzenia|Wysyłane do środowiska IDE, aby ustalić, czy użytkownik chce zatrzyma się w określonym w kodzie.|  
|Zdarzenia punktu przerwania|Występują, jeśli kod lub dane punkt przerwania zostaje trafiony.|  
|Zdarzenia tekst dokumentu|Występuje, gdy tekst dokumentu zostanie zmieniona. Te zdarzenia nie są wysyłane za pośrednictwem `IDebugEventCallBack2::Event` metody.|  
|Aparat utworzyć zdarzenia|Wysyłany, gdy aparat pierwszego tworzenia.|  
|Zdarzenia punktu wejścia|Wysyłany, gdy debugowany program ma uruchomić jej kod inicjujący i osiągnięto jego pierwszego punktu wejścia użytkownika.|  
|Zdarzenia wyjątków|Wysyłany, gdy uruchomiony program trafienia Wystąpił wyjątek.|  
|Zdarzenia pełną ocenę wyrażenia|Wysyłane po zakończeniu asynchronicznego wyrażenia.|  
|Znajdź Symbol zdarzenia|Wysyłany, gdy DE musi poprosić użytkownika o znalezienie symboli dla modułu.|  
|Zakończenie zdarzenia obciążenia|Wysyłane tylko po ukończeniu ładowania początkowego programu i pierwszy kod zostanie uruchomiony w programie.|  
|Komunikat zdarzenia|Wysyłany, gdy komunikaty są wysyłane do użytkowników.|  
|Zdarzenia modułu obciążenia|Wysyłany, gdy nowy moduł ładowania lub zwalnianie modułu.|  
|Zdarzenia ciąg w danych wyjściowych|Wysyłany, gdy program zapisuje dane wyjściowe debugowania.|  
|Tworzenie i zniszcz zdarzenia|Wysyłane do anonsowania utworzenia lub zniszczenia procesów, programy, właściwości, sesje i wątków, więc środowiska IDE programu Visual Studio można zachować informacje o stan debugowane programy.|  
|Krok zakończenie zdarzenia|Wysyłany, gdy krok został ukończony.|  
|Zdarzenia zmiany nazwy wątków|Wysyłany, gdy użytkownik zmieni nazwę wątku.|  
|Zdarzenia Zmień nazwę programu|Wysyłany, gdy użytkownik zmieni nazwę programu.|  
  
## <a name="see-also"></a>Zobacz też  
 [Wysyłanie zdarzeń](../../extensibility/debugger/sending-events.md)