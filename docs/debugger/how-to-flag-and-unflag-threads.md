---
title: 'Porady: Oflagowanie i usuwanie oflagowania wątków | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- treads, switching [debugging]
ms.assetid: 952d579d-6911-413e-b3e5-54e7e797e70c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 052c9d65e833152c0d3d3f67eda41742119eccaf
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31477605"
---
# <a name="how-to-flag-and-unflag-threads"></a>Porada: Oflagowanie i usuwanie oflagowania wątków
Mogą oznaczać wątku, który chcesz nadać szczególną uwagę przez oznaczenie go za pomocą ikony w **wątków**, **stosów równoległych** (Widok wątku), **czujki równoległej**i  **Wątków GPU** systemu windows. Ta ikona może pomóc i inne odróżnić od innych wątków oflagowane wątki.  
  
Oflagowane wątki również odbierać szczególnego traktowania w **wątku** listy na **debugowania lokalizacji** narzędzi i w innych wielowątkowe oknach debugowania. Można wyświetlić wszystkie wątki lub tylko oflagowane wątki w **wątku** listy lub w innych oknach.
  
### <a name="to-flag-or-unflag-a-thread"></a>Flaga lub usuwanie oflagowania wątków 
  
-   W **wątków** lub **czujki równoległej** okna, Znajdź wątek planuje się i kliknij ikonę flagi, aby zaznaczyć lub wyczyścić flagę. 
-   W **stosów równoległych** okna, kliknij prawym przyciskiem myszy na wątku lub grupa wątków i wybierz **flagi / <thread>**  lub **Unflag / <thread>** .
  
### <a name="to-unflag-all-threads"></a>Aby Usuń flagę ze wszystkich wątków  
  
-   W **wątków** okna, kliknij prawym przyciskiem myszy dowolnego wątku, a następnie kliknij przycisk **Usuń flagę ze wszystkich wątków**.
-   W **czujki równoległej** wybierz wszystkie oflagowane wątki, a następnie kliknij prawym przyciskiem myszy i wybierz **Unflag**.  
  
### <a name="to-display-only-flagged-threads"></a>Aby wyświetlić tylko oflagowane wątki  
  
-   Wybierz **Pokaż wątki tylko oflagowane** przycisk w jednym wielowątkowe debugowania systemu Windows.  
  
### <a name="to-flag-just-my-code"></a>Flagi tylko mój kod  
  
1.  Na pasku narzędzi u góry **wątków** okna, kliknij ikonę flagi.  
  
2.  Na liście rozwijanej kliknij **flagę tylko mój kod**.  
  
### <a name="to-flag-threads-that-are-associated-with-selected-modules"></a>Aby Flaga wątków, które są skojarzone z wybranych modułów  
  
1.  Na pasku narzędzi **wątków** okna, kliknij ikonę flagi.  
  
2.  Na liście rozwijanej kliknij **Oflaguj niestandardowy wybór modułów**.  
  
3.  W **wybierz moduły** oknie dialogowym Wybierz moduły, które mają.  
  
4.  (Opcjonalnie) W **wyszukiwania** wpisz ciąg wyszukiwania dla określonych modułów.  
  
5.  Kliknij przycisk **OK**.  
  
## <a name="see-also"></a>Zobacz też  
 [Debuguj aplikacje wielowątkowe](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Rozpocząć debugowanie aplikacji wielowątkowych](../debugger/get-started-debugging-multithreaded-apps.md)  
 [Wskazówki: Debugowanie aplikacji wielowątkowych korzystanie z okna wątków](../debugger/how-to-use-the-threads-window.md)