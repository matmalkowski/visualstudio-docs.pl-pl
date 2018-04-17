---
title: Widok procesów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.processesview
helpviewer_keywords:
- Processes view
ms.assetid: e144e70e-eef2-45a7-a562-a177f177d9a1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 40a92a65e4a10cd5321f513cb313035d8910022f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="processes-view"></a>Widok procesów
Widok procesy Wyświetla drzewa wszystkich aktywnych procesów w systemie. Nazwa procesu modułu i identyfikator są wyświetlane. Użyj widoku procesów, jeśli chcesz sprawdzić proces określony system, który zazwyczaj odpowiada zakresowi wykonywania programu. Procesy są identyfikowane za pomocą nazwy modułu lub są wyznaczone "procesy systemowe".  
  
 Microsoft Windows obsługuje wiele procesów. Każdy proces może mieć jeden lub więcej wątków i każdy wątek może zawierać jeden lub kilka skojarzonych okien najwyższego poziomu. Każde okno najwyższego poziomu może posiadać kilka okien. A + symbol wskazuje, że poziom jest zwinięty. W widoku zwiniętym zawiera jeden wiersz dla każdego procesu. Kliknij pozycję + symbol do zwiększenia poziomu.  
  
 Użyj widoku procesów, jeśli chcesz sprawdzić proces określony system, który zazwyczaj odpowiada zakresowi wykonywania programu. Procesy są identyfikowane za pomocą nazwy modułu lub są wyznaczone "procesy systemowe". Aby znaleźć proces, należy Zwiń drzewa i listy wyszukiwania.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-open-the-processes-view"></a>Aby otworzyć widok procesów  
  
1.  Z **Spy** menu, wybierz **procesy**.  
  
 ![Spy&#43; &#43; widok procesów](../debugger/media/spy--_processes.png "Spy ++ _Processes")  
Widok procesy Spy ++  
  
 Na rysunku powyżej przedstawiono widoku procesów z węzłami procesów i wątków rozwinięty.  
  
### <a name="in-this-section"></a>W tej sekcji  
 [Wyszukiwanie procesu w widoku procesów](../debugger/how-to-search-for-a-process-in-processes-view.md)  
 Wyjaśniono, jak można znaleźć określonego procesu w widoku procesów.  
  
 [Wyświetlanie właściwości procesu](../debugger/how-to-display-process-properties.md)  
 Wyjaśniono, jak można wyświetlić więcej informacji na temat wiadomości.  
  
### <a name="related-sections"></a>Sekcje pokrewne  
 [Widoki w programie Spy++](../debugger/spy-increment-views.md)  
 W tym artykule wyjaśniono widoków Spy ++ drzewa systemu windows, wiadomości, procesów i wątków.  
  
 [Korzystanie z programu Spy++](../debugger/using-spy-increment.md)  
 Wprowadzono narzędzie Spy ++ i opisano, jak mogą być używane.  
  
 [Wyszukiwanie procesów — okno dialogowe](../debugger/process-search-dialog-box.md)  
 Umożliwia znalezienie węzła dla określonego procesu w widoku procesów.  
  
 [Okno dialogowe właściwości procesu](../debugger/process-properties-dialog-box.md)  
 Wyświetla właściwości procesu, który wybrano w widoku procesów.  
  
 [Spy++ — dokumentacja](../debugger/spy-increment-reference.md)  
 Zawiera sekcje zawierająca opis każdego Spy ++ menu i okno dialogowe.