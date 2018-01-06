---
title: "Karta ogólna, okno dialogowe właściwości wątku | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- threading [Visual Studio], thread properties
- thread properties
ms.assetid: 46b6c668-6786-456e-97dc-337bcac0d812
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d8d53c373c58e31f2a2719df8afa6dd0da9cd3c6
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2018
---
# <a name="general-tab-thread-properties-dialog-box"></a>Karta ogólna, okno dialogowe właściwości wątku
Użyj tego okna dialogowego, aby dowiedzieć się więcej o konkretnym wątkiem. Aby wyświetlić to okno dialogowe, Przenieś fokus do [Widok wątków](../debugger/threads-view.md) okna lub Otwórz [widoku komunikatów](../debugger/messages-view.md) i rozwiń wiadomości. Zaznacz dowolny węzeł wątku w drzewie, a następnie wybierz pozycję **właściwości** z **widoku** menu.  
  
 **Wątku właściwości** okno dialogowe zawiera jedno okienko **ogólne** kartę. Dostępne są następujące ustawienia:  
  
|Wpis|Opis|  
|-----------|-----------------|  
|**Nazwa modułu**|Nazwa modułu.|  
|**Identyfikator wątku**|Unikatowy identyfikator tego wątku. Należy pamiętać, że numery identyfikatorów wątku są ponownie; identyfikują one wątku jedynie przez czas ich istnienia tego wątku.|  
|**Identyfikator procesu**|Unikatowy identyfikator tego procesu. Numery identyfikatorów procesów są używane ponownie, więc identyfikują one procesy jedynie dla okresu istnienia tego procesu. Typ obiektu procesu jest tworzony w momencie uruchomienia programu. Wszystkie wątki w procesie Udostępnij tę samą przestrzeń adresową i mają dostęp do tych samych danych. Wybierz tę wartość, aby wyświetlić właściwości identyfikatora procesu.|  
|**Stan wątku**|Bieżący stan wątku. Uruchomionych wątków jest przy użyciu procesora; Wątek wstrzymania to chwilę. Gotowy wątek oczekuje używać procesora, ponieważ nie jest jedną wolne. Wątek w trakcie przechodzenia oczekuje zasobów do wykonania, takich jak oczekiwanie na swój stos wykonywania stanie z dysku. Wątek oczekiwania musi procesora, ponieważ oczekuje na zakończenie operacji peryferyjne lub zasób, aby zwolnić.|  
|**Przyczyna oczekiwania**|Ma to zastosowanie tylko wtedy, gdy wątek jest w stanie oczekiwania. Pary zdarzenia są używane do komunikacji z podsystemami chronionymi.|  
|**Czas procesora CPU**|Łączny czas procesora CPU podczas tego procesu i wątków. Taki sam jak czas użytkownika + czasu uprzywilejowanego.|  
|**Czas użytkownika**|Całkowity czas spędzony tego wątku wykonywanie kodu w trybie użytkownika. Aplikacje wykonać w trybie użytkownika, jak podsystemów, takich jak Menedżera okien i aparat grafiki.|  
|**Czas uprzywilejowany**|Całkowity czas spędzony tego wątku wykonywanie kodu w trybie uprzywilejowanym. Wywołanego usługa systemu Windows usługi często będzie uruchamiany w trybie uprzywilejowanym w celu uzyskania dostępu do prywatnych danych systemu. Dane te są chronione przed dostępem przez wątków działających w trybie użytkownika. Wywołania systemu może być jawne lub może być pośrednie, takie jak po wystąpieniu błędu strony lub przerwania.|  
|**Czas, który upłynął**|Całkowity czas (w sekundach) ten wątek jest uruchomiony.|  
|**Bieżący priorytet**|Bieżący priorytet dynamiczny tego wątku. Wątków w procesie można wywołać i zmniejszyć ich priorytet podstawowy względem priorytet podstawowy procesu.|  
|**Priorytet podstawowy**|Bieżący priorytet podstawowy tego wątku.|  
|**Adres początkowy**|Początkowy adres wirtualny tego wątku.|  
|**Użytkownik komputera**|Licznik programu użytkownika dla wątku.|  
|**Przełączenia kontekstu**|Liczba przejście z jednego wątku. Przełączenia wątków mogą występować w ramach jednego procesu lub między procesami. Przełączenie wątku może być spowodowane przez jeden wątek innego podanie informacji lub są zastępowane, gdy wątek wyższy priorytet będzie gotowy do uruchomienia wątku.|