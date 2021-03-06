---
title: 'Porady: wyszukiwanie procesu w widoku procesów | Dokumentacja firmy Microsoft'
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
- Processes view
- processes, searching for
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ebb0c6a13db0fdc1a586a78038f759c59f8b110
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42682264"
---
# <a name="how-to-search-for-a-process-in-processes-view"></a>Porady: wyszukiwanie procesu w widoku procesów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porady: wyszukiwanie procesu w widoku procesów](https://docs.microsoft.com/visualstudio/debugger/how-to-search-for-a-process-in-processes-view).  
  
Możesz wyszukać określonego procesu w widoku procesów za pomocą ciągu Identyfikatora lub moduł jego procesu jako kryterium wyszukiwania. Można również określić początkową kierunek wyszukiwania. Pola w oknie dialogowym zostaną wyświetlone atrybuty wybranego procesu w drzewo procesów.  
  
### <a name="to-search-for-a-process-in-processes-view"></a>Wyszukiwanie procesu w widoku procesów  
  
1.  Rozmieść aplikacji dla systemu windows, więc tego programu Spy ++ i aktywne [widok procesy](../debugger/processes-view.md) okna są widoczne.  
  
2.  Z **wyszukiwania** menu, wybierz **Znajdź proces**  
  
     [Okno dialogowe Wyszukiwanie procesów](../debugger/process-search-dialog-box.md) zostanie otwarty.  
  
3.  Wpisz identyfikator procesu lub ciąg modułu jako kryterium wyszukiwania.  
  
4.  Wyczyść wszystkie pola, dla których nie chcesz określać wartości.  
  
    > [!TIP]
    >  Aby znaleźć wszystkie procesy, które są własnością modułu, należy wyczyścić **procesu** pole, a następnie wpisz nazwę modułu w **modułu** pole. Następnie użyj **Znajdź następny** kontynuować wyszukiwanie procesów.  
  
5.  Wybierz **się** lub **dół** dla początkowej kierunek wyszukiwania.  
  
6.  Kliknij przycisk **OK**.  
  
 Jeśli proces dopasowywania zostanie znaleziony, jest wyróżniona na **widok procesu** okna.



