---
title: 'Porady: wyszukiwanie wątku w widoku wątków | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- threads, searching
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 071b32a6f8947289d12ad8a402a316b1d174f65f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42697024"
---
# <a name="how-to-search-for-a-thread-in-threads-view"></a>Porady: wyszukiwanie wątku w widoku wątków
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porady: wyszukiwanie wątku w widoku wątków](https://docs.microsoft.com/visualstudio/debugger/how-to-search-for-a-thread-in-threads-view).  
  
Możesz wyszukać określonego wątku w widoku wątków, za pomocą ciągu Identyfikatora lub moduł jego wątku jako kryterium wyszukiwania. Można również określić początkową kierunek wyszukiwania. Pola w oknie dialogowym pokaże atrybuty zaznaczonych wątków w drzewie wątku.  
  
### <a name="to-search-for-a-thread-in-threads-view"></a>Wyszukiwanie wątku w widoku wątków  
  
1.  Rozmieść aplikacji dla systemu windows, więc tego programu Spy ++ i aktywne [Widok wątków](../debugger/threads-view.md) okna są widoczne.  
  
2.  Z **wyszukiwania** menu, wybierz **Znajdź wątek**.  
  
     [Okno dialogowe Wyszukiwanie wątków](../debugger/thread-search-dialog-box.md) zostanie otwarty.  
  
3.  Wpisz identyfikator wątku lub ciąg modułu jako kryterium wyszukiwania.  
  
4.  Wyczyść wszystkie pola, dla których nie chcesz określać wartości.  
  
    > [!TIP]
    >  Aby znaleźć wszystkie wątki, które są własnością modułu, należy wyczyścić **wątku** pole tekstowe i wpisz moduł nazwy **modułu** pole. Następnie użyj **Znajdź następny** kontynuować wyszukiwanie wątków.  
  
5.  Wybierz **się** lub **dół** dla początkowej kierunek wyszukiwania.  
  
6.  Kliknij przycisk **OK**.  
  
 Jeśli zostanie znalezione pasujące wątku, jest wyróżniona w oknie Widok wątków.



