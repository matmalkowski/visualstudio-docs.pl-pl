---
title: Widok procesów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.externaltools.spyplus.processesview
helpviewer_keywords:
- Processes view
ms.assetid: e144e70e-eef2-45a7-a562-a177f177d9a1
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c83b57ade3a78a4dcc926e34547ee566326e129
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42690082"
---
# <a name="processes-view"></a>Widok procesów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [widok procesy](https://docs.microsoft.com/visualstudio/debugger/processes-view).  
  
Widok procesów przedstawia drzewo wszystkich aktywnych procesów w Twoim systemie. Nazwa procesu modułu i identyfikator są wyświetlane. Użyj widoku procesów, jeśli chcesz sprawdzić procesu określonym systemie zazwyczaj odnosi się do wykonywania programu. Procesy są identyfikowane przez nazwy modułów lub zostały one oznaczone "procesy systemowe".  
  
 Program Microsoft Windows obsługuje wiele procesów. Każdy proces może mieć jeden lub więcej wątków i każdy wątek może zawierać jeden lub kilka skojarzonych okien najwyższego poziomu. Każde okno najwyższego poziomu może posiadać kilka okien. A + symbol informuje, że poziom jest zwinięta. W widoku zwiniętym składa się z jeden wiersz dla każdego procesu. Kliknij pozycję + symbolu, aby rozwinąć poziomu.  
  
 Użyj widoku procesów, jeśli chcesz sprawdzić procesu określonym systemie zazwyczaj odnosi się do wykonywania programu. Procesy są identyfikowane przez nazwy modułów lub zostały one oznaczone "procesy systemowe". Aby znaleźć proces, Zwiń drzewo i listę można przeszukiwać.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-open-the-processes-view"></a>Aby otworzyć widok procesów  
  
1.  Z **Spy** menu, wybierz **procesy**.  
  
 ![Szpieguj&#43; &#43; widok procesów](../debugger/media/spy-processes.png "Spy ++ _Processes")  
Widok procesów programu Spy ++  
  
 Powyższy rysunek przedstawia widok procesów z węzłami procesu i wątku, rozwinięty.  
  
### <a name="in-this-section"></a>W tej sekcji  
 [Trwa wyszukiwanie procesu w widoku procesów](../debugger/how-to-search-for-a-process-in-processes-view.md)  
 Wyjaśnia, jak można znaleźć określonego procesu w widoku procesów.  
  
 [Wyświetlanie właściwości procesu](../debugger/how-to-display-process-properties.md)  
 Wyjaśnia, jak wyświetlić więcej informacji na temat wiadomości.  
  
### <a name="related-sections"></a>Sekcje pokrewne  
 [Widoki w programie Spy++](../debugger/spy-increment-views.md)  
 W tym artykule wyjaśniono widoków programu Spy ++ drzewa systemu windows, wiadomości, procesów i wątków.  
  
 [Korzystanie z programu Spy++](../debugger/using-spy-increment.md)  
 Wprowadza narzędzie Spy ++ i wyjaśnia, jak mogą być używane.  
  
 [Okno dialogowe Wyszukiwanie procesów](../debugger/process-search-dialog-box.md)  
 Umożliwia znalezienie węzła dla określonego procesu w widoku procesów.  
  
 [Okno dialogowe właściwości procesu](../debugger/process-properties-dialog-box.md)  
 Wyświetla właściwości wybranego w widoku procesów procesu.  
  
 [Spy++ — dokumentacja](../debugger/spy-increment-reference.md)  
 Zawiera sekcje, zawierająca opis każdego Spy ++ menu i okno dialogowe.



