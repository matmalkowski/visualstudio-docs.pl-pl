---
title: Wprowadzenie programu Spy ++ | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Spy++
ms.assetid: 733b514b-63a9-402d-89aa-4f0416766655
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: cb12ef13e73e33b213d2b8ca79c2439b517fbda9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="introducing-spy"></a>Wprowadzenie programu Spy++
Spy ++ umożliwia wykonywanie następujących zadań:  
  
-   Wyświetla graficzny drzewa relacje między obiektami systemu. Obejmują one [procesów](../debugger/processes-view.md), [wątków](../debugger/threads-view.md), i [windows](../debugger/windows-view.md).  
  
-   Wyszukaj określone [windows](../debugger/how-to-search-for-a-window-in-windows-view.md), [wątków](../debugger/how-to-search-for-a-thread-in-threads-view.md), [procesów](../debugger/how-to-search-for-a-process-in-processes-view.md), lub [wiadomości](../debugger/how-to-search-for-a-message-in-messages-view.md).  
  
-   Wyświetl właściwości wybranego [windows](../debugger/how-to-display-window-properties.md), [wątków](../debugger/how-to-display-thread-properties.md), [procesów](../debugger/how-to-display-process-properties.md), lub [wiadomości](../debugger/how-to-display-message-properties.md).  
  
-   Wybierz okno, wątek, proces lub komunikat bezpośrednio w widoku.  
  
-   Użyj [narzędzia wyszukiwania](../debugger/how-to-use-the-finder-tool.md) wybierz okno, umieszczając kursor myszy.  
  
-   Ustaw [komunikatu opcja](../debugger/how-to-open-messages-view-from-find-window.md) przy użyciu parametrów wyboru dziennika złożonych wiadomości.  
  
 Spy ++ ma paska narzędzi i hiperłącza do pomagających w pracy szybciej. Zapewnia także **Odśwież** polecenie, aby zaktualizować widoku aktywnego **narzędzie Window Finder** aby łatwiej, spying i **czcionki** okno dialogowe, aby dostosować wyświetlanie systemu windows. Ponadto Spy ++ umożliwia zapisywanie i przywracanie preferencji użytkownika.  
  
 W różnych Spy ++ systemu windows należy kliknąć prawym przyciskiem myszy, aby wyświetlić menu skrótów często używanych poleceń. Polecenia są wyświetlane zależy od tego, gdzie jest wskaźnik. Na przykład, kliknij prawym przyciskiem myszy wpis w widoku okna wybrane okno jest widoczne, następnie klikając pozycję **zaznacz** na skrót menu powoduje, że obramowanie okna wybranych do flash, dzięki czemu można go zlokalizować łatwiej.  
  
> [!NOTE]
>  Istnieją dwa narzędzia, które przypominają Spy ++: PView, która przedstawia szczegółowe informacje dotyczące procesów i wątków oraz DDESPY. EXE, który umożliwia monitorowanie dynamicznej wymiany danych (DDE) wiadomości.  
  
## <a name="64-bit-operating-systems"></a>64-bitowe systemy operacyjne  
 Istnieją dwie wersje programu Spy ++. Pierwszą wersję, nazwę programu Spy ++ (spyxx.exe), służy do wyświetlania wiadomości wysyłane do okna, który działa w procesie 32-bitowych. Na przykład Visual Studio działa w procesie 32-bitowych. W związku z tym służy narzędzie Spy ++ do wyświetlenia wiadomości wysyłane do **Eksploratora rozwiązań**. Ponieważ konfigurację domyślną dla większości kompilacje w Visual Studio jest uruchamiane w procesie 32-bitowy, to pierwszej wersji programu Spy ++ jest jedną, która jest [dostępne na **narzędzia** menu](../debugger/how-to-start-spy-increment.md) w programie Visual Studio.  
  
 Druga wersja o nazwie Spy ++ (64-bitowy) (spyxx_amd64.exe), służy do wyświetlania wiadomości wysyłane do okna, który działa w procesie 64-bitowych. Na przykład na 64-bitowym systemie operacyjnym, Notatnik działa w procesie 64-bitowych. W związku z tym służy narzędzie Spy ++ (64-bitowy) do wyświetlenia wiadomości wysyłane do Notatnika. Spy ++ (64-bitowy) znajduje się w  
  
 .. \\ *Folder instalacji programu visual Studio*\Common7\Tools\spyxx_amd64.exe.  
  
 Danej wersji programu Spy ++ można uruchomić bezpośrednio z poziomu wiersza polecenia.  
  
> [!NOTE]
>  Mimo że nazwa pliku (64-bitowy) Spy ++ zawiera "amd", uruchomieniu na dowolnym x64 systemu operacyjnego Windows.  
  
## <a name="see-also"></a>Zobacz też 
 [Porady: Uruchom narzędzie Spy ++](../debugger/how-to-start-spy-increment.md)   
 [Korzystanie z programu Spy ++](../debugger/using-spy-increment.md)   
 [Widoków Spy ++](../debugger/spy-increment-views.md)   
 [Spy++ — dokumentacja](../debugger/spy-increment-reference.md)